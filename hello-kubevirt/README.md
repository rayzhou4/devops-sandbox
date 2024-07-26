# Hello KubeVirt
Made a simple Kubernetes cluster with WebApp and MongoDB pods which can be deployed locally through Minikube

### Learning Objectives
- KubeVirt (+ Virtctl)
  - is an extention of Kubernetes, and the purpose is to run and manage virtual machines (VM) workloads alongside container workloads within a Kubernetes cluster. Mainly used when organizations want to keep legacy infrastructure, providing a unified platform for managing both types of workloads.


### How to use
Followed the KubeVirt quickstart and lab documentations.
- https://kubevirt.io/quickstart_minikube/
- https://kubevirt.io/labs/kubernetes/lab1

### Quick-Start
Just followed the documentation for quickstart. It also helped me install KubeVirt + Virtctl

#### Check the deployment

```bash
kubectl get kubevirt.kubevirt.io/kubevirt -n kubevirt -o=jsonpath="{.status.phase}
```

#### Check all the components in the KubeVirt namespace

```bash
kubectl get all -n kubevirt
```

#### To safely remove a KubeVirt deployment

To delete the KubeVirt CR:
```bash
kubectl delete kubevirt kubevirt -n kubevirt
```
To delete KubeVirt Operator
```bash
kubectl delete -f https://github.com/kubevirt/kubevirt/releases/download/{VERSION}/kubevirt-operator.yaml
```

Delete Namespace:
```bash
kubectl delete namespace kubevirt
```

Verify Deletion:
```bash
kubectl get namespaces
kubectl get all -n kubevirt
```


### Lab 1 (Creating a VM)
Prerequisite: Quick-Start instructions

`vm.yaml` originally from https://kubevirt.io/labs/manifests/vm.yaml.

#### Apply `vm.yaml`

```bash
kubectl apply -f vm.yaml
```

#### Start the Virtual Machine

```bash
virtctl start testvm
```

#### Check the status

```bash
kubectl get vmis
kubectl get vmis -o yaml testvm
```

#### Playing with the VMs (disconnect by typing `ctrl+]`): 

```bash
virtctl console testvm
```

Login: cirros \
Password (default): gocubsgo \
Password (root): sudo

#### Stop and delete the Virtual Machine

```bash
virtctl stop testvm
kubectl delete vm testvm
```