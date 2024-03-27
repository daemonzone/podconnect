# podconnect
Quick and easy command-line tool to explore Kubernetes pods and shell connect to them

## Usage

This is the simplest way to explore your cluster, `podconnect` will guide you through the `namespaces` choice and their `pods`

```
$ podconnect
```

Example output :
```
NAME               STATUS
default            Active
kube-public        Active
kube-system        Active
monitoring         Active

Choose a namespace: 
```
Choosing a namespace allows you to explore the related `pods`

Example output:
```
Namespace: kube-public
pod_01-9dc99b85d-prppk
pod_02-deployment-b98d7485-xwzss

Choose a pod to connect to: 
```
"Choosing a pod to connect to" prompt allows you to specify partial values as search patterns.

As soon as the search pattern will return a unique match, the following input will connect you to the matching pod, i.e. `pod_01-9dc99b85d-prppk` 

```
(...)
Choose a pod to connect to: 9dc99
```

## Advanced Usage

Once you know the details required to connect to a specific namespace/pod, you could call `podconnect` with a single-line command syntax like the following ones

## Get a shell on a pod

```
$ podconnect sh my-namespace jkhax 
```

## Display pod's logs

```
$ podconnect logs my-namespace jkhax

```

Check the help page for further information

```
$ podconnect -h

usage: podconnect [logs|sh] [<namespace>] [<pod:pattern*>]
```

### Assisted connections

Whether you know all the details related to your pods or not, `podconnect` could accept partial values helping you to reach a specific `pod` even if some information are not correct or missing

E.g. you can connect to a pod (using the `sh` command) or access logs of a pod (using `logs` command) with one of the following command-lines

```
$ podconnect sh

$ podconnect logs

$ podconnect sh my-namespace

$ podconnect logs my-namespace jkhax

$ podconnect sh my-namespace pod000_test-jkhax

$ podconnect sh my-namespace jkhax

```

Feel free to contact me and suggest any improvement.


