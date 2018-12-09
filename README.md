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




