minikube start process
![Image text](https://github.com/ManuelCorreia97/2022_2023-introduction_to_distributed_technologies-k4113c-Goncalves_Manuel/blob/main/Lab/lab1/photo_2022-1.jpg)
writing a manifest to deploy a HashiCorp Vault "pod"

![Image text](https://github.com/ManuelCorreia97/2022_2023-introduction_to_distributed_technologies-k4113c-Goncalves_Manuel/blob/main/Lab/lab1/photo_2022-2.jpg)

We create a port on the yaml file
minikube kubectl apply –f myfirst.yaml
![Image text](https://github.com/ManuelCorreia97/2022_2023-introduction_to_distributed_technologies-k4113c-Goncalves_Manuel/blob/main/Lab/lab1/photo_2022-3.jpg)

create a service to access this container
run the command: minikube kubectl -- expose pod vault --type=NodePort --port=8200
![Image text](https://github.com/ManuelCorreia97/2022_2023-introduction_to_distributed_technologies-k4113c-Goncalves_Manuel/blob/main/Lab/lab1/image_2022-4.png)
![Image text](https://github.com/ManuelCorreia97/2022_2023-introduction_to_distributed_technologies-k4113c-Goncalves_Manuel/blob/main/Lab/lab1/photo_2022-5.jpg)

The service has been created, now let's access the container
minikube kubectl -- port-forward service/vault 8200:8200
![Image text](https://github.com/ManuelCorreia97/2022_2023-introduction_to_distributed_technologies-k4113c-Goncalves_Manuel/blob/main/Lab/lab1/photo_2022-6.jpg)
![Image text](https://github.com/ManuelCorreia97/2022_2023-introduction_to_distributed_technologies-k4113c-Goncalves_Manuel/blob/main/Lab/lab1/photo_2022-7.jpg)
![Image text](https://github.com/ManuelCorreia97/2022_2023-introduction_to_distributed_technologies-k4113c-Goncalves_Manuel/blob/main/Lab/lab1/photo_2022-8.jpg)

minikube will forward the computer port to the container and we can access the vault using the link http://localhost:8200
![Image text](https://github.com/ManuelCorreia97/2022_2023-introduction_to_distributed_technologies-k4113c-Goncalves_Manuel/blob/main/Lab/lab1/photo_2022-9.jpg)
