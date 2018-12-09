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



