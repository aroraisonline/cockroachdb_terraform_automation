# cockroachdb_terraform_automation
Imp. Note: The code is not here yet. will be adding soon. 
This Project includes some bash scripts and terraform to build and destroy 3 node cluster of cockroachdb in aws on https(secured) and http(unsecured)

1.) please extract this tar
    cd terraform
    terraform init

2.) please change the vpc and subnet id's in below files. they are hard coded in tf files.

  c.)  vpc id: (public subnet)
       -------
    variable.tf ### line number 16 in this file
    security-groups.tf ### line number 4 in this file
    load-balancer.tf ### line number 17 in this file 

  b.)  subnet-id:
       ---------
    load-balancer.tf ### line number 5 in this file



  c.) please change this id sg-01f1d71eb192a091e in security-group.tf and give your bastion server security group id.
     
  d.) please change the terraform-server.pub key with your ssh-key incase you want to use yours.


    NOTE: once you made above changes run this below script within this directory
   
3.) if you want to test installation of secure cockroachdb.
 
    cd terraform
 
    bash secure-cockroach-db-terraform-setup.sh ### it will print all steps while executing them. won't need to type yes/no as well. its set on auto-approval
    
    once this above script completes setup it will display the username/password and endpoint using which you can login into browser.

4.) things taking care while doing are:
   a.) file descriptor on server and process level are high number.
   b.) time syncronisation is set on all 3 servers.
   c.) certificates are being created and pushing into respective all 3 servers.
   d.) you can check this script secure-userdata-script.sh

5.) if you want to test installation of insecure cockroachdb as well. 

    run this below command :
    
    cd terraform
    bash insecure-cockroach-db-terraform-setup.sh

6.) once done please run below command to destroy (secure/insecure) infra you just setup using terraform.
    bash secure-cockroach-db-terraform-destroy.sh 



