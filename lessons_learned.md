# Lessons Learned

## 1. site.yml attributes block Showroom user data injection

**Problem:** Showroom injects per-user values (`user`, `password`, `openshift_api_url`, etc.) into `content/antora.yml` at deploy time. However, Antora's attribute precedence is:

```
site.yml (playbook) > antora.yml (component descriptor) > document
```

If `site.yml` defines those same attributes (even as placeholders), they win — the injected user data is silently ignored and users see the placeholder defaults.

**Fix:** Remove the runtime-injected attributes from `site.yml`. Only keep truly static attributes (versions, image URLs, doc links) there. Let Showroom own `user`, `password`, `openshift_api_url`, `openshift_console_url`, `openshift_cluster_ingress_domain`, and any other per-user values entirely via `antora.yml` injection.

**Bonus gotcha:** If the Antora init container has already built the site (producing `/showroom/www`), the content container will skip rebuilding even after you fix `site.yml`. Delete and redeploy the showroom pod to force a clean build.

---

## 2. AsciiDoc attribute substitution is disabled inside code blocks

**Problem:** `{variable}` substitution works in normal paragraph text but is **off by default** inside listing/code blocks (`----` and `[source,...]`). Variables render as literal text (e.g. `{user}` instead of `user-abc123`).

**Fix:** Add `subs="attributes+"` to any block that references `{...}` variables:

```adoc
[source,bash,subs="attributes+"]
----
oc login {openshift_api_url} --username {user} --password {password}
----
```

For bare `----` blocks (e.g. expected output), add it on the preceding line:

```adoc
[subs="attributes+"]
----
No resources found in {user}-lab namespace.
----
```

Regular paragraph text does **not** need this.
