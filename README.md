Setup a kubernetes cluster on Linux machines using ansible.

Requirements :
Ansible controller - ansible -- 1 vcpu / 2 gib ram

Kubernetes Master - master - 2 vcpu / 4 gib ram

Kubernetes Node1 - nodeone - 1 vcpu / 4 gib ram

Kubernetes Node2 - nodetwo - 1 vcpu / 4 gib ram


If you can allocate more compute resources, its better 
Use private IP address of Instances

Step-1
	Below commands are for Amzn-Linux Download and Install Ansible
	
	
	yum update -y
	sudo yum install epel-release -y
	sudo amazon-linux-extras install epel
	sudo yum install ansible -y
	ansible --version
	
	
	Generate ssh-key
	ssh-keygen -t rsa
	#see on which location is generated and paste on other ec2 at same location else it won't work
	ex : Your public key has been saved in /root/.ssh/id_rsa.pub.
	cat /root/.ssh/id_rsa.pub

	Paste On Worker-Nodes ec-2 at
	nano /root/.ssh/authorized_keys

Congrats you have successfully made the connection
Now to ssh master (paste ip of master and worker in ) nano /etc/hosts of every Instance.

Step-2
	Configure before Running
	Give the actual path i.e pwd for ansible.cfg 
	
	Ex : inventory      = /home/ec2-user/ansible-k8s-setup
	Define the labels in Host file
 	Ex : 
	[masters]
	master
	[workers]
	Worker
	

Step-3
	Run the files in following sequence
	k8s-pkg.yml
	k8s-master.yml
	k8s-workers.yml
	Commands to run them
	
	
	ansible-playbook k8s-pkg.yml
	ansible-playbook k8s-master.yml
	ansible-playbook k8s-workers.yml

