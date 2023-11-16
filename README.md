# Case-Study-1
Objective: To familiarize students with the basic GIT operations, AWS EC2 instance management, and simple web hosting.
Tasks:
GIT Setup & Operations: Students will start by creating a simple static website (HTML, CSS). This website will then be pushed to a GIT repository.
AWS EC2 Setup: Students will launch an EC2 instance, ensuring it's set up within the correct VPC and adhering to security best practices. (Use existing AWS EC2 (name:Control:ubuntu))
Deployment: Using Bash scripting, students will write a script to clone the GIT repository and serve the static website on the EC2 instance.
  
GIT Setup & Operations (after zip file download):
  mkdir ~/devops/Case-Study
  cp f*.zip ~/devops/Case-Study/
  cd ~/devops/Case-Study/
  cd Case-Study/
  ls
  git clone https://github.com/cliffso57/Case-Study-1.git
  ls -al
  cd Case-Study-1/
  cp ../finexo-html-20231113T224856Z-001.zip .
  git add .
  git commit -m "Add your-zip-file.zip"
  git push
  *git log
  *git reset --soft HEAD^
  *git commit --amend -m "Commit zip file finexo-html-20231113T224856Z-001.zip"
  *git push --force
  
  *cp Control-1.pem ../Case-Study/Case-Study-1/

Deployment:
  sudo su
  apt update -y
  apt install apache2 -y
  cd /var/www/html
  wget https://github.com/cliffso57/Case-Study-1/raw/main/finexo-html-20231113T224856Z-001.zip
  apt install unzip
  unzip finexo-html-20231113T224856Z-001.zip
  mv index.html orig.index.html
  http://ip_address/finexo-html/

Deployfinal script file:
#!/bin/bash
echo "*********** apt update -y *****************************"
sudo apt update -y
echo "*********** apt install apache2 -y ********************"
sudo apt install apache2 -y
echo "*********** cd /var/www/html **************************"
cd /var/www/html
 echo "*********** git clone repository **********************"
sudo git clone https://github.com/cliffso57/Case-Study-1.git .
echo "*********** apt install unzip ***********************"
sudo apt install unzip
echo "*********** unzip .zip ********************************"
sudo unzip finexo-html-20231113T224856Z-001.zip
# Determine Public IP address
PUBLIC_IP=$(curl -s http://checkip.amazonaws.com)
echo "************** Website is now available at: http://$PUBLIC_IP/********"
 # Move upzipped files to /var/www/html for deployment
echo "******* Move upzipped files to /var/www/html for deployment *********"
cp -r ./finexo-html/* .
echo “******* Delete unwanted files *****************”
rm -r fine*
