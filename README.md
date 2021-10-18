# ansible-k8s-setup
This will setup a kubernetes cluster on Centos7 machines using ansible.
You need these machines:
1. Ansible controller - ansible - 10.0.0.99 - 1 vcpu / 2 gib ram
2. Kubernetes Master - master - 10.0.0.100 - 2 vcpu / 4 gib ram
3. Kubernetes Node1 - nodeone - 10.0.0.1 - 1 vcpu / 4 gib ram
4. Kubernetes Node2 - nodetwo - 10.0.0.2 - 1 vcpu / 4 gib ram

If you can allocate more compute resources, its better
If you change your machine IP's then you have to change those whereever
those were referred.

Below commands are for Amzn-Linux
Download and Install Ansible

 yum update -y
 
 sudo yum install epel-release -y
 
 sudo amazon-linux-extras install epel
 
 sudo yum install ansible -y
 
 ansible --version
 

Generate ssh-key

ssh-keygen -t rsa

#see on which location is generated and paste on other ec2 at same location else it won't work

# ex : Your public key has been saved in /root/.ssh/id_rsa.pub.

cat /root/.ssh/id_rsa.pub 

Paste On second ec-2 at 

 nano /root/.ssh/authorized_keys 
 
Congrats you have successfully made the connection




