# OpenShift Getting Started Workshop - Learning Outcomes

This document outlines the learning objectives for each module in the OpenShift Getting Started Workshop.

## Module 1: Introduction to OpenShift

At the end of this module, the student will be able to:
- Define what OpenShift is and its role as a container application platform
- Explain what containers are and how they differ from virtual machines
- Describe the benefits of using containers for application deployment

## Module 2: OpenShift Architecture

At the end of this module, the student will be able to:
- Identify the main components of an OpenShift cluster (control plane nodes, worker nodes)
- Recognize supporting infrastructure components (dynamic provisioned storage, private container registry, routing layer)
- Understand that OpenShift can run on various infrastructures (on-premises, public cloud, hybrid)

## Module 3: Explore OpenShift

At the end of this module, the student will be able to:
- Access the OpenShift web console using provided credentials
- Navigate the OpenShift web console dashboard
- Install and verify the OpenShift CLI (`oc`) tool
- Authenticate to an OpenShift cluster using the command line (via username/password or token)
- Use the `oc whoami` command to verify authentication
- List available projects using `oc projects`
- Switch between web console and command line interfaces

## Module 4: Projects

At the end of this module, the student will be able to:
- Define what an OpenShift project is and its purpose for organizing resources
- Explain how projects provide isolation, policies, and resource constraints
- Describe the relationship between OpenShift projects and Kubernetes namespaces
- Navigate to a project in the web console
- Use the Topology view to visualize applications
- Switch to a specific project using the `oc project` command
- Understand the project scope for subsequent operations

## Module 5: ParksMap Architecture

At the end of this module, the student will be able to:
- Describe a polyglot microservices architecture
- Identify the components of a multi-tier application (frontend web app, backend services)
- Understand how server-side and client-side components work together
- Explain the concept of service discovery in OpenShift

## Module 6: Parksmap App - Deploying Container Images

At the end of this module, the student will be able to:
- Deploy a pre-existing container image using the OpenShift web console
- Specify container image details (image name, application name, component name)
- Select resource types (Deployment vs DeploymentConfig)
- Add labels to deployments for identification and filtering
- Define what a Pod is and its relationship to containers
- Explain the purpose of Services in OpenShift
- View Pod details using both web console and CLI (`oc get pods`, `oc describe pods`)
- Examine Pod specifications in YAML format
- Understand how Services use selectors and labels to route traffic to Pods
- Query Service information using `oc get services` and `oc describe service`
- Verify Service endpoints

## Module 7: Scaling Apps

At the end of this module, the student will be able to:
- Define what Deployments and ReplicaSets are and their purposes
- Explain how ReplicaSets ensure the desired number of Pods are running
- View Deployment and ReplicaSet information using `oc get deployment` and `oc get rs`
- Scale an application using the `oc scale` command
- Scale an application using the web console
- Verify scaling operations by checking Pod counts and Service endpoints
- Demonstrate OpenShift's self-healing capabilities by deleting a Pod
- Understand the relationship between Deployments, ReplicaSets, and Pods
- Scale an application back down

## Module 8: Routes

At the end of this module, the student will be able to:
- Define what a Route is and its purpose for external access
- Explain the role of the HAProxy router in OpenShift
- Create a Route using the OpenShift web console
- Create a Route using the `oc create route edge` command
- Configure TLS termination for secure Routes
- Verify Route creation using `oc get route`
- Access an application through its Route URL
- Understand the relationship between Routes and Services

## Module 9: Logging

At the end of this module, the student will be able to:
- Explain how OpenShift captures container logs (STDOUT/STDERR)
- View Pod logs using the web console
- View Pod logs using the `oc logs` command
- Use label selectors to view logs from multiple Pods (`oc logs -l app=parksmap`)
- Understand that applications should log to STDOUT for proper OpenShift integration

## Module 10: Permissions

At the end of this module, the student will be able to:
- Explain the concepts of authentication (AuthN) and authorization (AuthZ) in OpenShift
- Define what a Service Account is and its purpose
- Identify the default Service Account used by Pods
- Navigate to the project's Role Bindings in the web console
- Grant permissions to a Service Account using the web console
- Grant permissions to a Service Account using the `oc policy add-role-to-user` command
- Use the `-z` flag shortcut for service accounts
- Trigger a new deployment using `oc rollout restart`
- Verify that permission changes resolved application errors

## Module 11: Connecting to a Container

At the end of this module, the student will be able to:
- Establish a remote shell session to a container using `oc rsh`
- Execute commands within a container using `oc exec`
- Access a container's terminal through the web console
- Navigate the container's filesystem
- View Service Account tokens injected into containers
- Understand the `--` delimiter in `oc exec` commands
- Explain why OpenShift randomizes container user IDs for security

## Module 12: Nationalparks Backend App - Source-to-Image

At the end of this module, the student will be able to:
- Define what Source-to-Image (S2I) is and its purpose
- Explain the difference between S2I, Dockerfile builds, and custom builds
- Deploy an application from a Git repository using the web console
- Select appropriate builder images for different programming languages
- Configure import strategies (Devfile, Dockerfile, Builder Image)
- Add labels during application creation
- Configure routing options during deployment
- Monitor build progress through logs (web console and `oc logs -f builds/<build-name>`)
- Understand the build and deployment process flow
- Verify deployment by checking Routes and accessing application endpoints
- Test REST API endpoints in a browser

## Module 13: Connecting to a Database

At the end of this module, the student will be able to:
- Create Kubernetes Secrets to store sensitive information
- Deploy a MongoDB database from a container image
- Configure environment variables from Secrets
- Create database users using the container terminal
- Edit a Deployment to add environment variables
- Connect an application to a database using environment variables
- Use Services for internal service discovery (connecting nationalparks to mongodb)
- Add labels to existing deployments
- Load data into a database through application endpoints
- Apply labels to Routes for service discovery
- Understand how the parksmap frontend discovers backends using labels

## Module 14: Application Healthchecks

At the end of this module, the student will be able to:
- Define what readiness probes and liveness probes are
- Explain the difference between readiness and liveness probes
- Understand when OpenShift uses each type of probe
- Add readiness probes to a deployment using the web console
- Add liveness probes to a deployment using the web console
- Configure health check endpoints, ports, and types (HTTP GET)
- Recognize that health check changes trigger a new deployment

## Module 15: Continuous Integration and Pipelines

At the end of this module, the student will be able to:
- Define what continuous delivery (CD) pipelines are
- Explain what OpenShift Pipelines and Tekton are
- Identify Tekton custom resources (Task, Pipeline, TaskRun, PipelineRun)
- Create a Pipeline using the web console (both builder and YAML views)
- Define Pipeline parameters and default values
- Configure Pipeline workspaces (PersistentVolumeClaim, EmptyDir)
- Understand common Pipeline tasks (git-clone, maven, buildah, openshift-client)
- Create a PersistentVolumeClaim for Pipeline storage
- Start a Pipeline run from the web console
- Monitor Pipeline execution through the web console
- View logs for individual Pipeline tasks
- Verify successful Pipeline completion

## Module 16: Webhooks with Pipelines

At the end of this module, the student will be able to:
- Define what webhooks are and their purpose in CI/CD
- Explain what Tekton Triggers are
- Identify the components needed for webhook automation (TriggerTemplate, TriggerBinding, EventListener)
- Create Tekton Triggers using YAML manifests
- Configure a webhook in Gitea to trigger Pipeline runs
- Set webhook payload URL and content type
- Test webhook functionality by making code changes in Git
- Verify that code commits automatically trigger new Pipeline runs
- Monitor automated builds and deployments
- Confirm that application changes are deployed automatically

## Commented/Optional Modules

The following modules appear in the navigation but are currently commented out:

### MLBParks App - Templates
- Instantiate OpenShift Templates

### Binary Builds
- Understand the differences between S2I and binary builds
- Clone source code locally
- Build application artifacts (JAR/WAR files)
- Deploy using binary builds
- Iterate quickly with code changes

### Debugging Apps
- Understand port forwarding concepts
- Enable debugging in application containers
- Port-forward from Services to local machine
- Attach remote debuggers
- Port-forward from Pods to local machine

---

## Summary of Key Skills Across All Modules

By completing this workshop, students will be able to:

1. **Navigate OpenShift**: Use both web console and CLI confidently
2. **Deploy Applications**: Using container images, S2I, and pipelines
3. **Manage Resources**: Projects, Pods, Services, Routes, Deployments
4. **Scale Applications**: Horizontally and understand self-healing
5. **Connect Services**: Using internal DNS and service discovery
6. **Secure Applications**: Using RBAC, Service Accounts, and Secrets
7. **Monitor Applications**: View logs and configure health checks
8. **Implement CI/CD**: Create pipelines and automate deployments with webhooks
9. **Work with Storage**: PersistentVolumeClaims for databases and pipelines
10. **Troubleshoot**: Access containers, view logs, and understand resource relationships
