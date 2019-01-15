# docker-K8s-helm

Docker:Docker is a container mangement tool.
K8s:K8s is a container-orchestration system for automating deployment, scaling and management of containerized applications.
Helm :K8s Package Manager


Follow :https://kubernetes.io/docs/setup/   Easy way as per your requirement

or
Below commands for Setting Up Helm inside K8(Single Node ) using docker containers:

steps:
1:Login into your AWS Console and launch an EC2 Instance .
	Here i am taking Ubuntu 16.04 
	
	Type:t2.medium 
			

2: Login into console 
	steps:https://linuxroutes.com/how-to-login-to-aws-ec2-instance/

3: Install Docker:

	How to install Docker Community Edition via YUM?
	 Step 1 - Install required packages. yum-utils provides the yum-config-manager utility, and device-mapper-persistent-data and lvm2 are required by the devicemapper storage driver.
		$ sudo -s
		$ 
		$ sudo yum install -y yum-utils device-mapper-persistent-data lvm2
	 step 2 - Use the following command to set up the stable repository
		$ sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
	 Step 3 - Install the latest version of Docker CE
		$ sudo yum install –y https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
		$ sudo yum-config-manager --enable rhui-REGION-rhel-server-extras
		$ sudo yum install -y docker-ce
		$ sudo yum install docker-ce
		# Verify Docker Installations
		$ docker -v

		# Docker is installed but not started. The docker group is created, but no users are added to the group.
	 Step 4 - Enable Docker
		$ sudo systemctl enable docker
	 Step 5 - Start Docker
		$ sudo systemctl start docker
		$ docker info
	 Step 6 - Verify that docker is installed correctly by running the hello-world image.
		$ sudo docker run hello-world

4:Install Kubernetes (Single Node (Master and slave(Minion) on same machine )): ROOT ONLY
	
		To install Kubernetes tools execute below commands :

		$ cat <<EOF > /etc/yum.repos.d/kubernetes.repo
		[kubernetes]
		name=Kubernetes
		baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
		enabled=1
		gpgcheck=1
		repo_gpgcheck=1
		gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
		EOF
		
		$ setenforce 0

		$ yum install -y kubelet kubeadm kubectl

		For command auto completion:
		$ yum install bash-completion -y

		To enable and start kubernetes(kubelet service) tools:
		$ systemctl enable kubelet && systemctl start kubelet

		$ yum update -y


		To initialize/Start Kubernetes Services:

		$ kubeadm config images pull

		$ kubeadm init --pod-network-cidr=192.168.0.0/16 

		Your Kubernetes master has initialized successfully!

		
		if any error like cant connect with locahost host RUN THIS COMMAND:(This happens when u start new session some times)
		As root user : $ export KUBECONFIG=/etc/kubernetes/admin.conf
				
		Installing a pod network add-on with the following command:
		$ kubectl apply -f https://docs.projectcalico.org/v3.1/getting-started/kubernetes/installation/hosted/rbac-kdd.yaml
		$ kubectl apply -f https://docs.projectcalico.org/v3.1/getting-started/kubernetes/installation/hosted/kubernetes-datastore/calico-networking/1.7/calico.yaml

		To schedule pods on the master(for a single-machine Kubernetes cluster for development, run):
		$ kubectl taint nodes --all node-role.kubernetes.io/master-
		
		verify K8s installtion:
		As a proof of concept we will now deploy a Nginx server into our new Kubernetes cluster. Now, run the following two commands on your master node :
		$ kubernetes-master:~$ kubectl run --image=nginx nginx-server --port=80 --env="DOMAIN=cluster"
		$ kubernetes-master:~$ kubectl expose deployment nginx-server --port=80 --name=nginx-ht
		
		
		
		
		
4:Install Helm inside K8s:

	https://github.com/helm/helm/blob/master/docs/install.md
	
	Helm now has an installer script that will automatically grab the latest version of the Helm client and install it locally.
	You can fetch that script, and then execute it locally. It's well documented so that you can read through it and understand what it is doing before you run it.

	$ curl https://raw.githubusercontent.com/helm/helm/master/scripts/get > get_helm.sh
	$ chmod 700 get_helm.sh
	$ ./get_helm.sh
	
	verify Helm installation:
	follow steps :https://github.com/helm/helm/blob/master/docs/quickstart.md#install-an-example-chart
		

		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		

