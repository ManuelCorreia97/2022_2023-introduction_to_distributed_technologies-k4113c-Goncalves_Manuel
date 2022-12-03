University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)

Year: 2022/2023

Group: K4113c

Author: Goncalves Manuel

Lab: Lab2

Date of create: 24.11.2022

Date of finished: 3.12.2022

# Лабораторная работа №4 "Сети связи в Minikube, CNI и CoreDNS"

### Creating a minikube cluster with 2 nodes and install the CNI=calico plugin
```
minikube start --network-plugin=cni --cni=calico --nodes 2 --kubernetes-version=v1.24.0
```
![Image text](photo_2022-12-03_13-46-17.jpg)

### Get the list of created nodes:
```
minikube kubectl -- get nodes
```
![Image text](photo_2022-12-03_13-51-47.jpg)
### The status of the nodes can be found using the following command:

`minikube status -p minikube`

![Image text](photo_2022-12-03_13-56-23.jpg)

Deploy calicoctl pod

`kubectl apply -f calicoctl.yaml`

![Image text](photo_2022-12-03_14-01-51.jpg)

### Set labels for nodes
```
kubectl label nodes minikube zone=west
kubectl label nodes minikube-m02 zone=east
```
![Image text](photo_2022-12-03_14-10-29.jpg)

### Creating an ip pool, remove the default pool:
```
kubectl exec -i -n kube-system calicoctl -- /calicoctl create -f - < ip_pool.yaml
kubectl exec -i -n kube-system calicoctl -- /calicoctl  delete ippools default-ipv4-ippool
kubectl exec -i -n kube-system calicoctl -- /calicoctl  get ippools -o wide
```
![Image text](photo_2022-12-03_14-26-10.jpg)

Let's creating resources, a service, a config map.
`kubectl apply -f resources.yaml`
![Image text](photo_2022-12-03_14-28-12.jpg)

### Check out the IP addresses of our pods.
`kubectl get pods -o wide`

![Image text](photo_2022-12-03_14-32-21.jpg)

### Result 

![Image text](photo_2022-12-03_13-31-37.jpg)

### Ping test
`kubectl exec -it lab4-app-krtx9  -- ping -c4 192.168.2.1`

![Image text](photo_2022-12-03_14-57-01.jpg)

### Схема
![Image text](photo_2022-12-03_14-52-46.jpg)
