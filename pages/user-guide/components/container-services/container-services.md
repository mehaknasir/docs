# Container Services

UltreMesh provides full support for container services. 4 types of container services that Ultramesh supports are Container, Kubernetes Secret, Config Maps and Docker Hub. These can be configured in platform and can be a part of solution mesh. 

## Container

Standard unit of software that packages all its dependencies and code so that application runs reliably from one computing environment to another. Docker container is a lightweight and standalone executable package that contains all the things needed to run an applications i.e. code, system tools, libraries, runtime etc. Container images become containers on runtime and in case of docker containers, images becomes containers when they run on Docker engine. 

Details of the configurations that can be done for Kubernetes Containers are explained below and also highlighted in the image.

![4](imgs\4.jpg)

1. **K8s Resource**: Drop-down to add container services. 

2. **Secret Icon**: Click the icon to configure container. 

3. **Name**: Name for the service.

4. **Version:** Version of the service.

5. **Namespace**: Namespace for the service. 

6. **Type**: Type of Pod or Controller i.e. Deployment, StatefulSet, DaemonSet, CronJob, Job.

   > **Deployment:** A Deployment controller provides declarative updates for Pods and ReplicaSets. It changes the actual state to the desired state at a controlled rate. You can define Deployments to create new ReplicaSets, or to remove existing Deployments and adopt all their resources with new Deployments.
   >
   > **StatefulSet:** StatefulSet is the workload API object used to manage stateful applications. Manages the deployment and scaling of a set of Pods , and provides guarantees about the ordering and uniqueness of these Pods. Like a Deployment , a StatefulSet manages Pods that are based on an identical container spec. Unlike a Deployment, a StatefulSet maintains a sticky identity for each of their Pods. These pods are created from the same spec, but are not interchangeable: each has a persistent identifier that it maintains across any rescheduling.
   >
   > **DaemonSet:** A DaemonSet ensures that all (or some) Nodes run a copy of a Pod. As nodes are added to the cluster, Pods are added to them. As nodes are removed from the cluster, those Pods are garbage collected. Deleting a DaemonSet will clean up the Pods it created.
   >
   > **Job:** A Job creates one or more Pods and ensures that a specified number of them successfully terminate. As pods successfully complete, the Job tracks the successful completions. When a specified number of successful completions is reached, the task is complete. Deleting a Job will clean up the Pods it created.
   >
   > **CronJob:** A Cron Job creates Jobs on a time-based schedule. It runs a job periodically on a given schedule, written in Cron format.

![5](imgs\5.jpg)

1. **Enable Deployment Pipeline**: Check to enable deployment pipeline e.g. Canary. 
2. **Configure Pipeline**: To configure deployment pipeline. 
3. **Registry**: Select any saved docker registry from drop-down or create a new one. 
4. **Username** of docker registry.
5. **Password** of docker registry. 

![6](imgs\6.jpg)

1. **Image Name**: Name of the docker image. 

2. **Tag**: Tag of the docker image.

3. **Environment Variables**: To add environment variables i.e. Static, Dynamic, Load Balancer.

   > **Static:** Only Key, Value pair will be needed
   >
   > **Dynamic:** For getting the values dynamically on run time from other services in the solution. 
   >
   > **Load Balance:** Exposes the Service externally using a cloud provider’s load balancer.

4. **Ports**: To add Ports. You can also add multiple ports. Name, Host and Container will be needed.

![7](imgs\7.jpg)

1. **Command And Arguments**: To add command and arguments in the fields provided below. 
2. **Advance Settings**: To open a panel of advanced settings. 

![8](imgs\8.jpg)

1. **Enable CID**: To enable CID

2. **Enable Init Container**: Specialized containers that run before app containers in a Pod . Init containers can contain utilities or setup scripts not present in an app image.

3. **Scaling**: To setup scaling. Check our scaling guide [here](/pages/user-guide/components/scaling/scaling).

4. **Resource Quota**: To setup resource quota limits. Currently, CPU and Memory resource quota is supported.

   > When allocating compute resources, each container may specify a request and a limit value for either CPU or memory. The quota can be configured to quota either value.
   >
   > **Request:** If the quota has a value specified for requests.cpu or requests.memory, then it requires that every incoming container makes an explicit request for those resources.
   >
   > **Limit:** If the quota has a value specified for limits.cpu or limits.memory, then it requires that every incoming container specifies an explicit limit for those resources.

![9](imgs\9.jpg)

1. **Probe**: To configure Liveness and Readiness probes. 

   > **Liveness:** The kubelet uses liveness probes to know when to restart a Container. For example, liveness probes could catch a deadlock, where an application is running, but unable to make progress. Restarting a Container in such a state can help to make the application more available despite bugs
   >
   > **Readiness:** The kubelet uses readiness probes to know when a Container is ready to start accepting traffic. A Pod is considered ready when all of its Containers are ready. One use of this signal is to control which Pods are used as backends for Services. 

2. **Handler:** Handler for probe i.e. Exec, Http Get, TCP Socket. 

3. **Command**: Exec action command. 

4. **Initial Delay Seconds**: Number of seconds after the container has started before liveness or readiness probes are initiated. 

5. **Timeout Seconds:** Number of seconds after which the probe times out.

![10](imgs\10.jpg)

1. **Period Seconds:** How often (in seconds) to perform the probe.
2. **Success Threshold:**  Minimum consecutive successes for the probe to be considered successful after having failed. 
3. **Failure Threshold:** When a Pod starts and the probe fails, Kubernetes will try Failure Threshold times before giving up. Giving up in case of liveness probe means restarting the Pod. In case of readiness probe the Pod will be marked Unready. Defaults to 3. Minimum value is 1.

![11](imgs\11.jpg)

1. **Security Context:** A security context defines privilege and access control settings for a Pod or Container.
2. **Capabilities:** With Linux capabilities, you can grant certain privileges to a process without granting all the privileges of the root user. To add or drop Linux capabilities for a Container, select the capabilities from the drop-down
3. **Run As Group:** Run As User field specifies the user ID that all processes will run with for any Containers in the Pod. 
4. **Run As Group:** Run As Group field specifies the primary group ID for all processes within any containers of the Pod. If this field is omitted, the primary group ID of the containers will be root(0).

![12](imgs\12.jpg)

1. **Proc Mount:** N/A

![13](imgs\13.jpg)

1. **SE Linux Options:**  Linux kernel security module that provides a mechanism for supporting access control security policies.
2. **Users:**  Name of the user. 
3. **Role**: Name of the role.
4. **Type**: Type of option. 
5. **Level**: SE Linux security levels.

## Kubernetes Secret

Objects that let user store and manage sensitive information e.g. passwords, OAuth, ssh keys etc. Storing all this private information in a secret is a much more secure and flexible way than putting it verbatim in Pod definition or in a container image. It also reduces the risk of accidental exposure. To use secret, pod must reference the secret. 

Details of the configurations that can be done for Kubernetes Secret are explained below and also highlighted in the image.

![1](imgs\1.jpg)

1. **K8s Resource**: Drop-down to add container services. 
2. **Secret Icon**: Click the icon to configure Secret. 
3. **Name**: Name for the service.
4. **Version:** Version of the service.
5. **Namespace**: Namespace for the service. 

![2](imgs\2.jpg)

1. **Type**: Type of secret i.e. Opaque or TLS.
2. **Upload**: To upload a file for Value. 
3. **AddString Secrets**: To add string secrets. You can add more than one string secrets. 
4. **AddBase64 Secrets**: To add Base64 secrets. You can add more than one base64 secrets.

## Config Maps

Allow to decouple configuration artifacts from image content to keep containerized applications portable. ConfigMap stores configuration data as key-value pairs. The data can be consumed in pods or provide the configurations for system components such as controllers. ConfigMap is similar to Secrets, but provides a means of working with strings that don’t contain sensitive information. Users and system components alike can store configuration data in ConfigMap.

Details of the configurations that can be done for Config Maps are explained below and also highlighted in the image.

![3](imgs\3.jpg)

1. **K8s Resource**: Drop-down to add container services. 

2. **Configmaps Icon**: Click the icon to configure config maps. 

3. **Name**: Name for the service.

4. **Version:** Version of the service.

5. **Namespace**: Namespace for the service.

6. **Upload**: To upload a file for Value

7. **Add DataS**: Directory, file, or literal value to draw the data from.

   > **Key**: File name or the key you provided on the command line.
   >
   > **Value**: File contents or the literal value you provided on the command line.

## Docker Hub

World’s largest repository of container images with an array of content sources including community developers, open source projects and independent software vendors building and distributing their code in containers. Users can get access to free public repositories for storing and sharing images or can choose subscription plan for private repos.
