# K8s Playground

Based on freecodecamp's video [Docker Containers and Kubernetes Fundamentals – Full Hands-On Course](https://www.youtube.com/watch?v=kTp5xUtcalw) and the [Resources Github Repository](https://github.com/K8sAcademy/Fundamentals-HandsOn/tree/main)

## Cheat Sheet

- [K8s Playground](#k8s-playground)
  - [Cheat Sheet](#cheat-sheet)
    - [ConfigMap](#configmap)
    - [Context](#context)
    - [CronJob](#cronjob)
    - [DaemonSet](#daemonset)
    - [Deployment](#deployment)
    - [Job](#job)
    - [Namespace](#namespace)
    - [Pod](#pod)
    - [PersistentVolume](#persistentvolume)
    - [PersistentVolumeClaim](#persistentvolumeclaim)
    - [ReplicaSet](#replicaset)
    - [RollingUpdate](#rollingupdate)
    - [Secrets](#secrets)
    - [Service ClusterIp](#service-clusterip)
    - [Service NodePort](#service-nodeport)
    - [StatefulSet](#statefulset)
    - [StorageClass](#storageclass)

`k` is set as an alias for `kubectl`

### ConfigMap

| Command                                           | Description                                  |
| ------------------------------------------------- | -------------------------------------------- |
| `k get configmap`                                 | List ConfigMaps                              |
| `k get cm`                                        | Shortcut                                     |
| `k describe cm <cmName>`                          | Get details about `<cmName>`                 |
| `k create cm <cmName> --from-literal="key=value"` | Create a ConfigMap the imperative way        |
| `k create cm <cmName> --from-file=<configFile>`   | Create a ConfigMap from a file               |
| `k create cm <cmName> --from-file=<configFolder>` | Create a ConfigMap from a folder             |
| `k apply -f <cm-definition-file>`                 | Create a ConfigMap the declarative way       |
| `k delete cm <cmName>`                            | Delete a ConfigMap by `<cmName>`             |
| `k delete -f <cm-definition-file>`                | Delete a ConfigMap by `<cm-definition-file>` |

[Up](#cheat-sheet)

### Context

| Command                                                  | Description                                                                                 |
| -------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `k config current-context`                               | Get the current context                                                                     |
| `k config get-contexts`                                  | List all contexts                                                                           |
| `k config use-context <context>`                         | Set the current context                                                                     |
| `k config delete-context <context>`                      | Delete a context from the config file                                                       |
| `k config set-context --current --namespace=<namespace>` | Set the current Context to use the specified [namespace](#namespace) for following commands |

[Up](#cheat-sheet)

### CronJob

| Command                                                                                 | Description                                |
| --------------------------------------------------------------------------------------- | ------------------------------------------ |
| `k get cronjob`                                                                         | List CronJobs                              |
| `k get cj`                                                                              | Shortcut                                   |
| `k describe cj <cjName>`                                                                | Get details about `<cjName>`               |
| `k create cj <cjName> --image=<image> --schedule="*/5 * * * *" -- <command_inside_pod>` | Create a CronJob the imperative way        |
| `k apply -f <cj-definition-file>`                                                       | Create a CronJob the declarative way       |
| `k delete cj <cjName>`                                                                  | Delete a CronJob by `<cjName>`             |
| `k delete -f <cj-definition-file>`                                                      | Delete a CronJob by `<cj-definition-file>` |

[Up](#cheat-sheet)

### DaemonSet

| Command                            | Description                                  |
| ---------------------------------- | -------------------------------------------- |
| `k get daemonset`                  | List DaemonSets                              |
| `k get ds`                         | Shortcurt                                    |
| `k describe ds <daemonsetname>`    | Get details about `<dsName>`                 |
| `k apply -f <ds-definition-file>`  | Create a DaemonSet the declarative way       |
| `k delete -f <ds-definition-file>` | Delete a DaemonSet by `<ds-definition-file>` |
| `k delete ds <dsName>`             | Delete a DaemonSet by `<dsName>`             |

[Up](#cheat-sheet)

### Deployment

| Command                                                                     | Description                                       |
| --------------------------------------------------------------------------- | ------------------------------------------------- |
| `k get deployment`                                                          | List deployments                                  |
| `k get deploy`                                                              | Shortcut                                          |
| `k describe deploy <depoymentname>`                                         | Get details about `<deployName>`                  |
| `k create deploy <deployName> --image=<image> --replicas=<I> --port=<port>` | Create a deployment the imperative way            |
| `k apply -f <deploy-definition-file>`                                       | Create a deployment the declarative way           |
| `k delete -f <deploy-definition-file>`                                      | Delete a deployment by `<deploy-definition-file>` |
| `k delete deploy <deployName>`                                              | Delete a deployment by `<deployName>`             |

[Up](#cheat-sheet)

### Job

| Command                                  | Description                             |
| ---------------------------------------- | --------------------------------------- |
| `k get job`                              | List Jobs                               |
| `k describe job <jobName>`               | Get details about `<jobName>`           |
| `k create job <jobName> --image=<image>` | Create a Job the imperative way         |
| `k apply -f <job-definition-file>`       | Create a Job the declarative way        |
| `k delete job <jobName>`                 | Delete a Job by `<jobName>`             |
| `k delete -f <job-definition-file>`      | Delete a Job by `<job-definition-file>` |

[Up](#cheat-sheet)

### Namespace

| Command                              | Description                              |
| ------------------------------------ | ---------------------------------------- |
| `k get namespace`                    | List all namespaces                      |
| `k get ns`                           | Shortcut                                 |
| `k get <resources> --all-namespaces` | List all `<resources>` in all namespaces |
| `k create ns <namespace>`            | Create a namespace                       |
| `k delete ns <namespace>`            | Delete a namespace                       |

[Up](#cheat-sheet)

### Pod

| Command                                                                    | Description                                                 |
| -------------------------------------------------------------------------- | ----------------------------------------------------------- |
| `k get pods`                                                               | List running Pods                                           |
| `k get pod -o wide`                                                        | List running Pods more verbose                              |
| `k get pod -o yaml > <filename>`                                           | Extract `<podname>`'s definition and save it to a file      |
| `k describe pod <podname>`                                                 | Get details about `<podname>`                               |
| `k run <podname> --image=<image> -- <command_inside_pod>`                  | Run a Pod                                                   |
| `k exec -it <podname> -- <command_inside_pod>`                             | Enter a Pod interactivly                                    |
| `k exec -it <podname> --container <containername> -- <command_inside_pod>` | Enter a container inside a Multi-Container-Pod interactivly |
| `k create -f <pod-definition-file>`                                        | Create a Pod the declarative way                            |
| `k delete -f <pod-definition-file>`                                        | Delete a Pod by `<pod-definition-file>`                     |
| `k delete pod <podname>`                                                   | Delete a Pod by `<podname>`                                 |

[Up](#cheat-sheet)

### PersistentVolume

| Command                            | Description                                         |
| ---------------------------------- | --------------------------------------------------- |
| `k get persistentvolume`           | List PersistentVolumes                              |
| `k get pv`                         | Shortcut                                            |
| `k describe pv <pvName>`           | Get details about `<pvName>`                        |
| `k apply -f <pv-definition-file>`  | Create a PersistentVolume                           |
| `k delete -f <pv-definition-file>` | Delete a PersistentVolume by `<pv-definition-file>` |
| `k delete pv <pvName>`             | Delete a PersistentVolume by `<pvName>`             |

[Up](#cheat-sheet)

### PersistentVolumeClaim

| Command                             | Description                                               |
| ----------------------------------- | --------------------------------------------------------- |
| `k get persistentvolumeclaims`      | List PersistentVolumeClaims                               |
| `k get pvc`                         | Shortcut                                                  |
| `k describe pvc <pvcName>`          | Get details about `<pvcName>`                             |
| `k apply -f <pvc-definition-file>`  | Create a PersistentVolumeClaim                            |
| `k delete -f <pvc-definition-file>` | Delete a PersistentVolumeClaim by `<pvc-definition-file>` |
| `k delete pvc <pvcName>`            | Delete a PersistentVolumeClaim by `<pvcName>`             |

[Up](#cheat-sheet)

### ReplicaSet

| Command                            | Description                                   |
| ---------------------------------- | --------------------------------------------- |
| `k get replicasets`                | List ReplicaSets                              |
| `k get rs`                         | Shortcut                                      |
| `k describe rs <rsName>`           | Get details about `<rsName>`                  |
| `k apply -f <rs-definition-file>`  | Create a ReplicaSet                           |
| `k delete -f <rs-definition-file>` | Delete a ReplicaSet by `<rs-definition-file>` |
| `k delete rs <rsName>`             | Delete a ReplicaSets by `<rsName>`            |

[Up](#cheat-sheet)

### RollingUpdate

| Command                                                       | Description                                    |
| ------------------------------------------------------------- | ---------------------------------------------- |
| `k apply -f <deployment-definition-file>`                     | Update a Deployment                            |
| `k rollout status`                                            | Get the progress of the update                 |
| `k rollout history deploy <deployName>`                       | Get the history of `<deployName>`              |
| `k rollout undo <deployName>`                                 | Rollback `<deployName>`                        |
| `k rollout undo <deployName> --to-revision=<revision-number>` | Rollback `<deployName>` to `<revision-number>` |

[Up](#cheat-sheet)

### Secrets

| Command                                                         | Description                                    |
| --------------------------------------------------------------- | ---------------------------------------------- |
| `k get secrets`                                                 | List Secrets                                   |
| `k get secrets <secretName> -o yaml`                            | Get details about Secret `<secretName>`        |
| `k create secret generic <secretName> --from-literal=KEY=Value` | Create a Secret the imperative way             |
| `k apply -f <secrets-definition-file>`                          | Create a Secret the declarative way            |
| `k delete -f <secrets-definition-file>`                         | Delete a Secret by `<secrets-definition-file>` |
| `k delete secrets <secretName>`                                 | Delete a Secret by `<secretName>`              |

[Up](#cheat-sheet)

### Service ClusterIp

| Command                                                                        | Description                                                |
| ------------------------------------------------------------------------------ | ---------------------------------------------------------- |
| `k get service`                                                                | List Services                                              |
| `k get svc`                                                                    | Shortcut                                                   |
| `k get svc -o wide`                                                            | List Services more verbose                                 |
| `k describe svc <svName>`                                                      | Get details about `<svcName>`                              |
| `k expose pod <podname> --port=<port> --target=<target> --name=<svName>`       | Create a Service the imperative way to expose a Pod        |
| `k expose deploy <deployName> --port=<port> --target=<target> --name=<svName>` | Create a Service the imperative way to expose a Deployment |
| `k apply -f <svc-definition-file>`                                             | Create a Service the declarative way                       |
| `k delete svc <svName>`                                                        | Delete a Service by `<svcName>`                            |
| `k delete -f <svc-definition-file>`                                            | Delete a Service by `<svc-definition-file>`                |

[Up](#cheat-sheet)

### Service NodePort

| Command                                                                                        | Description                                                |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| `k get service`                                                                                | List Services                                              |
| `k get svc`                                                                                    | Shortcut                                                   |
| `k get svc -o wide`                                                                            | List Services more verbose                                 |
| `k describe svc <svName>`                                                                      | Get details about `<svName>`                               |
| `k expose pod <podName> --port=<port> --target=<target> --type=NodePort`                       | Create a Service the imperative way to expose a Pod        |
| `k expose deploy <deployName> --port=<port> --target=<target> --name=<svName> --type=NodePort` | Create a Service the imperative way to expose a Deployment |
| `k apply -f <service-definition-file>`                                                         | Create a Service the declarative way                       |
| `k delete svc <svName>`                                                                        | Delete a Service by `<svName>`                             |
| `k delete -f <scv-definition-file>`                                                            | Delete a Service by `<sv-definition-file>`                 |

[Up](#cheat-sheet)

### StatefulSet

| Command                                | Description                                     |
| -------------------------------------- | ----------------------------------------------- |
| `k get statefulset`                    | List StatefulSet                                |
| `k get sts`                            | Shortcurt                                       |
| `k describe sts <stsName>`             | Get details about `<stsName>`                   |
| `k apply -f <sts-set-definition-file>` | Create a StatefulSet the declarative way        |
| `k delete -f <sts-definition-file>`    | Delete a StatefulSet by `<sts-definition-file>` |
| `k delete sts <stsName>`               | Delete a StatefulSet by `<stsName>`             |

[Up](#cheat-sheet)

### StorageClass

| Command                            | Description                                    |
| ---------------------------------- | ---------------------------------------------- |
| `k get storageclass`               | List StorageClasses                            |
| `k get sc`                         | Shortcut                                       |
| `k describe sc <scName>`           | Get details about `<scName>`                   |
| `k apply -f <sc-definition-file>`  | Create a StorageClass the declarative way      |
| `k delete -f <sc-definition-file>` | Delete a StatefulSet by `<sc-definition-file>` |
| `k delete sc <scName>`             | Delete a StatefulSet by `<scName>`             |

[Up](#cheat-sheet)

