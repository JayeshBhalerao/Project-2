## capstone Project
1. 2 projects with 2 GitHub repository
2. CI/CD Pipeline
3. container Image creation
4. push docker hub
5. pull image in Kubernetes and run a pod


1. Files from another Repo to MyRepo

$ git clone https://github.com/phadatul/skillupnodejs.git
$ cd skillupjava 
$ git remote add origin https://github.com/JayeshBhalerao/Project-2.git           #tried add like this didn't worked
$ git remote -v 
$ git remote set-url origin https://github.com/JayeshBhalerao/Project-2.git
$ git remote -v
$ git status
$ git push

If you want to maintain the connection to both repositories:
git remote add upstream https://github.com/phadatul/skillupnodejs.git
git remote add origin https://github.com/JayeshBhalerao/Project-2.git

2. Creating Docker Image

created docker file

$ docker build -t project-2 .
$ docker run -dp 9595:9595 --name=project-2 project-2    <!-- optional if running through kubernetes -->
$ docker images                                          <!-- optional if running through kubernetes -->
$ docker exec -it project-2 sh                           <!-- optional if running through kubernetes -->

3. Pushing image to DockerHub

$ docker login
$ docker tag project-2 jayeshdockerhub/project-2:latest
$ docker push jayeshdockerhub/project-2:latest
$

4. Pulling images to kubernetes

created deploment, configmap, secret and service files
secret and configmap are not used.

$ kubectl apply -f service.yml
$ kubectl apply -f pod.yml

5. Troubleshoot service unable to match the pod

$ kubectl get pods -o wide
$ kubectl get pod project-2 --show-labels
$ kubectl describe svc project-2-service
$ kubectl get endpoints project-2-service


