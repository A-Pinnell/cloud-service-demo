cloud-service-demo
To practice using Git and Github
Files Included: index.html, README.md
Version control helps a cloud project by tracking changes, enabling collaboration between team members, and allowing previous versions of the code to be restored if problems occur.

Q: Explain the difference between a Docker image and a Docker container in your own words. Suggested length: 2–3 sentences.
A: A Docker image is a blueprint that contains everything needed to run an application, including its code, dependencies, and configuration. A Docker container is a running instance of that image, where the application actually executes. Essentially, an image is the template, while a container is the running application created from it.

1. What Docker is: Docker is a platform that allows developers to package and run applications in isolated environments called containers. It helps ensure applications run consistently across different computers.

2. What a Docker image is: A Docker image is a blueprint that contains everything needed to run an application, including its code, dependencies, and configuration.

3. What a Docker container is: A Docker container is a running instance of a Docker image. It provides an isolated environment where the application executes.

4. How to build and run an application using Docker: First, create a Dockerfile that describes how to build the application. Then, use docker build to create an image and docker run to start a container from that image.

docker build -t cloud-service-demo:1.0 . 
docker run -d --name cloud-demo-container -p 8080:80 cloud-service-demo:1.0

Assignment 3 - Task 5
    1. What is the difference between a Pod and a Deployment?
        A Pod is the smallest unit in Kubernetes that runs an application or container. A Deployment manages Pods by making sure the correct number are running and replacing them if they fail.

    2. What is the purpose of a Kubernetes Service?
        A Kubernetes Service provides a consistent way to access Pods. It lets applications communicate without needing to know individual Pod IP addresses, which can change.

    3. Why might a cloud application need more than one Pod?
        A cloud application might need multiple Pods to handle more users and traffic. Multiple Pods also improve reliability because if one Pod fails, the others can keep running and serving users.

    4. What Kubernetes is and why it is used
        Kubernetes is a container orchestration platform used to deploy, manage, and scale applications. It helps keep applications running by managing containers automatically.

    5. Purpose of a Pod, Deployment, and Service
        - Pod: Runs one or more application containers.
        - Deployment: Manages Pods and ensures the desired number are running.
        - Service: Provides a stable way to access and communicate with Pods.

    6. How to start Minikube and make the Docker image available
        Start Minikube using minikube start. Then build the Docker image and make it available to Minikube using minikube image load image-name.

    7. How to apply the Deployment and Service YAML files
        Use kubectl apply -f deployment.yaml and kubectl apply -f service.yaml to create the Deployment and Service in Kubernetes.

    8. How to access the application using kubectl port-forward
        Run kubectl port-forward service/service-name 8080:80 to forward local port 8080 to the application's port 80. Then open http://localhost:8080 in a browser.

minikube start --driver=docker 
minikube image load cloud-service-demo:1.0 
kubectl apply -f kubernetes/deployment.yaml 
kubectl apply -f kubernetes/service.yaml 
kubectl port-forward service/cloud-service-demo 8080:80 
