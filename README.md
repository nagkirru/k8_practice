# k8_practice
practice k8 

followed --
https://courses.edx.org/courses/course-v1:LinuxFoundationX+LFS158x+1T2018/courseware/55ac7d3bed884e9cac68fbbfb892e9a3/bf7d2b08dfe74bcbb030d3ae91154510/?child=first


root@naga:~# sudo apt-get install virtualbox

root@naga:~# curl -Lo minikube https://github.com/kubernetes/minikube/releases/download/v0.30.0/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/

root@naga:~# minikube start

root@naga:~# minikube status


=======================================
kubectl could not be found on your path. kubectl is a requirement for using minikube
To install kubectl, please run the following:

curl -Lo kubectl https://storage.googleapis.com/kubernetes-release/release/v1.10.0/bin/linux/amd64/kubectl && chmod +x kubectl && sudo cp kubectl /usr/local/bin/ && rm kubectl

To disable this message, run the following:

minikube config set WantKubectlDownloadMsg false
========================================
minikube: Running
cluster: Running
kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.100


=======================================================

To install kubectl on Linux, follow the instructions below:

root@naga:~# curl -Lo kubectl https://storage.googleapis.com/kubernetes-release/release/v1.10.0/bin/linux/amd64/kubectl && chmod +x kubectl && sudo cp kubectl /usr/local/bin/ && rm kubectl
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 51.7M  100 51.7M    0     0  9180k      0  0:00:05  0:00:05 --:--:-- 10.6M
root@naga:~# 
root@naga:~# which kubectl
/usr/local/bin/kubectl
root@naga:~# 


--------------

naga@naga:~$ kubectl version --client
Client Version: version.Info{Major:"1", Minor:"10", GitVersion:"v1.10.0", GitCommit:"fc32d2f3698e36b93322a3465f63a14e9f0eaead", GitTreeState:"clean", BuildDate:"2018-03-26T16:55:54Z", GoVersion:"go1.9.3", Compiler:"gc", Platform:"linux/amd64"}

--------------------


root@naga:~# kubectl config current-context
minikube


root@naga:~# kubectl get nodes
NAME       STATUS    ROLES     AGE       VERSION
minikube   Ready     master    46m       v1.10.0


we cab switch context later 



----------------------





===============================================
kubectl Configuration File

To look at the connection details, we can either see the content of the ~/.kube/config

root@naga:~# view ~/.kube/config


root@naga:~#  kubectl config view
apiVersion: v1
clusters:
- cluster:
    certificate-authority: /root/.minikube/ca.crt
    server: https://192.168.99.100:8443
  name: minikube
contexts:
- context:
    cluster: minikube
    user: minikube
  name: minikube
current-context: minikube
kind: Config
preferences: {}
users:
- name: minikube
  user:
    client-certificate: /root/.minikube/client.crt
    client-key: /root/.minikube/client.key


==================================================

root@naga:~# kubectl cluster-info
Kubernetes master is running at https://192.168.99.100:8443
CoreDNS is running at https://192.168.99.100:8443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
root@naga:~# 

==============================================================

$ kubectl proxy
Starting to serve on 127.0.0.1:8001

After running the above command, we can access the dashboard at http://127.0.0.1:8001/api/v1/namespaces/kube-system/services/kubernetes-dashboard:/proxy/#!/overview?namespace=default


--- To see all end points :

Go and access from browser --   http://127.0.0.1:8001/

or

hit the curl command

naga@naga:~$ curl http://localhost:8001/


{
  "paths": [
    "/api",
    "/api/v1",
    "/apis",
    "/apis/",
    "/apis/admissionregistration.k8s.io",
    "/apis/admissionregistration.k8s.io/v1beta1",
    "/apis/apiextensions.k8s.io",
    "/apis/apiextensions.k8s.io/v1beta1",
    "/apis/apiregistration.k8s.io",
    "/apis/apiregistration.k8s.io/v1",
    "/apis/apiregistration.k8s.io/v1beta1",
    "/apis/apps",
    "/apis/apps/v1",
    "/apis/apps/v1beta1",
    "/apis/apps/v1beta2",
    "/apis/authentication.k8s.io",
    "/apis/authentication.k8s.io/v1",
    "/apis/authentication.k8s.io/v1beta1",
    "/apis/authorization.k8s.io",
    "/apis/authorization.k8s.io/v1",
    "/apis/authorization.k8s.io/v1beta1",
    "/apis/autoscaling",
    "/apis/autoscaling/v1",
    "/apis/autoscaling/v2beta1",
    "/apis/batch",
    "/apis/batch/v1",
    "/apis/batch/v1beta1",
    "/apis/certificates.k8s.io",
    "/apis/certificates.k8s.io/v1beta1",
    "/apis/events.k8s.io",
    "/apis/events.k8s.io/v1beta1",
    "/apis/extensions",
    "/apis/extensions/v1beta1",
    "/apis/networking.k8s.io",
    "/apis/networking.k8s.io/v1",
    "/apis/policy",
    "/apis/policy/v1beta1",
    "/apis/rbac.authorization.k8s.io",
    "/apis/rbac.authorization.k8s.io/v1",
    "/apis/rbac.authorization.k8s.io/v1beta1",
    "/apis/storage.k8s.io",
    "/apis/storage.k8s.io/v1",
    "/apis/storage.k8s.io/v1beta1",
    "/healthz",
    "/healthz/autoregister-completion",
    "/healthz/etcd",
    "/healthz/ping",
    "/healthz/poststarthook/apiservice-openapi-controller",
    "/healthz/poststarthook/apiservice-registration-controller",
    "/healthz/poststarthook/apiservice-status-available-controller",
    "/healthz/poststarthook/bootstrap-controller",
    "/healthz/poststarthook/ca-registration",
    "/healthz/poststarthook/generic-apiserver-start-informers",
    "/healthz/poststarthook/kube-apiserver-autoregistration",
    "/healthz/poststarthook/rbac/bootstrap-roles",
    "/healthz/poststarthook/start-apiextensions-controllers",
    "/healthz/poststarthook/start-apiextensions-informers",
    "/healthz/poststarthook/start-kube-aggregator-informers",
    "/healthz/poststarthook/start-kube-apiserver-informers",
    "/logs",
    "/metrics",
    "/openapi/v2",
    "/swagger-2.0.0.json",
    "/swagger-2.0.0.pb-v1",
    "/swagger-2.0.0.pb-v1.gz",
    "/swagger.json",
    "/swaggerapi",
    "/version"
  ]
}


===========================================================


https://courses.edx.org/courses/course-v1:LinuxFoundationX+LFS158x+1T2018/courseware/05eb503ab837469cae8637755d55fa79/7b044c7dafae45a7a3c4773195b8f11b/?child=first



Get the API server endpoint

$ APISERVER=$(kubectl config view | grep https | cut -f 2- -d ":" | tr -d " ")

root@naga:~# APISERVER=$(kubectl config view | grep https | cut -f 2- -d ":" | tr -d " ")
root@naga:~# echo $APISERVER
https://192.168.99.100:8443


=================================================================


To list all the Namespaces, we can run the following command:

$ kubectl get namespaces

root@naga:~# kubectl get namespaces
NAME          STATUS    AGE
default       Active    14h
kube-public   Active    14h
kube-system   Active    14h
root@naga:~# 

Using Resource Quotas, we can divide the cluster resources within Namespaces. 

============================================================

Authentication and Authorization (Demo)

https://courses.edx.org/courses/course-v1:LinuxFoundationX+LFS158x+1T2018/courseware/d7e0b7d9bd57499a9265e0093ff7d8d6/f6f8a73dc38647eeb576dce791500901/?child=first


======================

creating pods..


root@naga:~# kubectl get nodes
NAME       STATUS    ROLES     AGE       VERSION
minikube   Ready     master    18h       v1.10.0



write pod.yml


kubectl create -f pod.yml


kubectl get pods

-- containerCreating ( status)

kubectl describe pods -- pod status - pending  , container status - waiting  .. it will be pulling image 

then the status again 

kubectl get pods  -- shows all pods in default namaspace

kubectl get pods/hello-pod

kubectl get pods --all-namespaces


kubectl delete pods hello-pod


but we don't create PODS directly


------------


kind: ReplicationController 
spec:
  replicas: 10

rc.yml

kubectl apply -f rc.yml

kubectl get pds

====================================

services:


kubectl expose rc helloc-rc --name=hello-svc --target-port=8080 --type=NodePort ( sample, not recommendated.. use declaratively )


kubectl delete svc hello-svc

----------  
create service manifest file

Kind: Service

spec: NodePort


kubectl create -f svc.yml

kubectl get svc

kubectl describe svc hello-svc

->when we create service it creates endpoint

kubectl get ep

=======================================================

deployment- stand alone app in local


root@naga:/home/naga/k8-practice# cat webserver.yaml


root@naga:/home/naga/k8-practice# kubectl create -f webserver.yaml
deployment.apps "webserver" created


root@naga:/home/naga/k8-practice# kubectl get replicasets
NAME                   DESIRED   CURRENT   READY     AGE
webserver-77d8994b6f   3         3         3         3m


root@naga:/home/naga/k8-practice# kubectl get pods
NAME                         READY     STATUS    RESTARTS   AGE
webserver-77d8994b6f-h6rq8   1/1       Running   0          4m
webserver-77d8994b6f-ndscb   1/1       Running   0          4m
webserver-77d8994b6f-nmvgd   1/1       Running   0          4m


--> Creating a Service and Exposing It to the External World with NodePort




root@naga:/home/naga/k8-practice# kubectl create -f webserver-svc.yaml
service "web-service" created


root@naga:/home/naga/k8-practice# kubectl get svc
NAME          TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
kubernetes    ClusterIP   10.96.0.1       <none>        443/TCP        19h
web-service   NodePort    10.96.241.131   <none>        80:30975/TCP   1m



It is not necessary to create the Deployment first, and the Service after. They can be created in any order. A Service will connect Pods based on the Selector.


root@naga:/home/naga/k8-practice# kubectl describe svc web-service
Name:                     web-service
Namespace:                default
Labels:                   run=web-service
Annotations:              <none>
Selector:                 app=nginx
Type:                     NodePort
IP:                       10.96.241.131
Port:                     <unset>  80/TCP
TargetPort:               80/TCP
NodePort:                 <unset>  30975/TCP
Endpoints:                172.17.0.5:80,172.17.0.6:80,172.17.0.7:80
Session Affinity:         None
External Traffic Policy:  Cluster
Events:                   <none>


web-service uses app=nginx as a Selector, through which it selected our three Pods, which are listed as endpoints. So, whenever we send a request to our Service, it will be served by one of the Pods listed in the Endpoints section.

-->>  Accessing the Application Using the Exposed NodePort

Our application is running inside the Minikube VM. To access the application from our workstation, let's first get the IP address of the Minikube VM:


root@naga:/home/naga/k8-practice# minikube ip
192.168.99.101


get port number from --  command "kubectl describe svc web-service"
NodePort:                 <unset>  30975/TCP


now access 
http://192.168.99.101:30975/


We could also run the following minikube command to access the application on the browser:

root@naga:/home/naga/k8-practice# minikube service web-service





