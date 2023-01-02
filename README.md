# User Service

An API (Application Programming Interface) that servers CRUD (Create, Read, Update, Delete) operations for user data would allow a client to create new user records, retrieve existing user records, update existing user records, and delete user records.

### Setup

#### Docker

```sh
docker build -t quizroulette/user-service:v1.0.0 .
docker push quizroulette/user-service:v1.0.0
```
#### K8

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: user-service-deployment
  labels:
    app: user-service
spec:
  replicas: 3
  selector:
    matchLabels:
      app: user-service
  template:
    metadata:
      labels:
        app: user-service
    spec:
      containers:
      - name: user-service
        image: quizroulette/user-service:v1.0.0
        ports:
        - containerPort: 8080
```

Expose:

```sh
kubectl expose deployment user-service-deployment --type=LoadBalancer --name=user-service-service
```