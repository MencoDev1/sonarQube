# sonarQube

```
Installation:

AWS T2.medium Instance 4GB RAM
Open security Group for port 9000
Install Java OpenJDK 1.8+ for SonarQube 7.8+



# Create sonar user to manage the SonarQube server
sudo useradd sonar 
sudo echo "sonar ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/sonar
sudo hostname sonar 
sudo passwd sonar 
sudo su - sonar 

# Enable passwordAuthentication in the server:
sudo sed -i "/^[^#]*PasswordAuthentication[[:space:]]no/c\PasswordAuthentication yes" /etc/ssh/sshd_config
sudo service sshd restart

# Install JDK 1.8+ 
cd /opt
sudo yum -y install unzip wget git 

sudo yum install java-11-openjdk-devel java-1.8.0-openjdk-devel -y

# Download the SonarQube server app
sudo wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.0.1.46107.zip
sudo unzip sonarqube-9.0.1.46107.zip
sudo rm -rf sonarqube-9.0.1.46107.zip
sudo mv sonarqube-9.0.1.46107.zip sonarqube

# Permission configuration:
sudo chown -R sonar:sonar /opt/sonarqube/
sudo chmod -R 775 /opt/sonarqube/

#Star SonarQube
sh /opt/sonarqube/bin/linux-x86-64/sonar.sh start/stop/status
```
