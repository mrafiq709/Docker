# Docker
Install docker

# Docker Ubuntu
update your existing list of packages:

    sudo apt update
    
install a few prerequisite packages which let apt use packages over HTTPS:

    sudo apt install apt-transport-https ca-certificates curl software-properties-common
    
add the GPG key for the official Docker repository to your system:

    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    
Add the Docker repository to APT sources:

    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
    
update the package database with the Docker packages from the newly added repo:

    sudo apt update
    
Make sure you are about to install from the Docker repo instead of the default Ubuntu repo:

    apt-cache policy docker-ce
    
You’ll see output like this, although the version number for Docker may be different:
```
Output of apt-cache policy docker-ce
docker-ce:
  Installed: (none)
  Candidate: 5:19.03.9~3-0~ubuntu-focal
  Version table:
     5:19.03.9~3-0~ubuntu-focal 500
        500 https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
```
Finally, install Docker:

    sudo apt install docker-ce

Check status:

    sudo systemctl status docker
    
###### Executing the Docker Command Without Sudo
add your username to the docker group:

    sudo usermod -aG docker ${USER}
    
To apply the new group membership, log out of the server and back in, or type the following:

    su - ${USER}
    
Confirm that your user is now added to the docker group by typing:

    id -nG
    
If you need to add a user to the docker group that you’re not logged in as, declare that username explicitly using:

    sudo usermod -aG docker username
    
To view system-wide information about Docker, use:

    docker info
