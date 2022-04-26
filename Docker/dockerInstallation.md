# Docker Installation steps on Amazon linux
    Sudo yum update -y : To update all the packages
    sudo yum install docker -y : To install docker
    sudo systemctl start docker : To start the docker service
    sudo systemctl status docker : To check the status of docker service
    sudo systemctl enable docker : To enable the docker service
    sudo usermod -a -G docker ec2-user : To add user to docker group(After running this command close the terminal and open it again then ec2-user will be able to run all the docker command)

