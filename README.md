apiVersion: v1
kind: Pod
metadata:
  name: "vault"
  namespace: default
  labels:
    app: "vault"
spec:
  containers:
  - name: 
    image: "vault"
    ports:
    - containerPort:  
      name:  http
