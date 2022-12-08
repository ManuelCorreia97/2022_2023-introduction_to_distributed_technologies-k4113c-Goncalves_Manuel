University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)

Year: 2022/2023

Group: K4113c

Author: Goncalves Manuel

Lab: Lab2

Date of create: 17.11.2022

Date of finished: . .2022

# Лабораторная работа №3 "Сертификаты и "секреты" в Minikube, безопасное хранение данных."

## Creating a service, ingress, replicaset file and execute the command:
```
kubectl apply -f cm.yaml
kubectl apply -f replicaset.yaml 
kubectl apply -f svc.yaml 
kubectl apply -f ingress.yaml 
```   
## or 
`kubectl apply -f cm.yaml -f replicaset.yaml -f svc.yaml -f ingress.yaml `

![Image text](photo_2022-12-04_01-17-55.jpg)

## Enabling ingress addons:
```
minikube addons enable ingress   
```
![Image text](photo_2022-12-04_01-26-25.jpg)

### Checking that ingress is enabled
`minikube addons list`

![Image text](photo_2022-12-04_01-30-46.jpg)

## Generate and import of the TLS certificate to minikube
```
openssl genrsa -out ca.key 2048
openssl req -x509 -new -nodes -days 365 -key ca.key -out ca.crt -subj "/CN=lab3.example.com"
```
![Image text](photo_2022-12-04_01-35-11.jpg)

## Importing of the certivicate to minikube
```
kubectl create secret tls lab3-secret --cert=ca.crt --key=ca.key
```
![Image text](photo_2022-12-04_01-47-52.jpg)
![Image text](photo_2022-12-04_01-49-17.jpg)

## Editing hosts
![Image text](photo_2022-12-04_01-52-55.jpg)

## Results
![Image text](photo_2022-12-04_01-57-33.jpg)
### Checking the certificate
![Image text](photo_2022-12-04_01-59-37.jpg)

## Scheme
![Image text](photo_2022-12-04_02-42-48.jpg)