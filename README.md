# Case-Study-1
Case study repository
Here is the instruction set to follow:
  sudo su
  yum update -y
  yum install -y httpd
  cd /var/www/html
  wget https://github.com/cliffso57/Case-Study-1/finexo-html-20231113T224856Z-001.zip
  unzip finexo-html-20231113T224856Z-001.zip
  *cp -r Case-Study-1-main/* /var/www/html/
  *rm -rf Case-Study-1-main finexo-html-20231113T224856Z-001.zip
  systemctl enable httpd 
  systemctl start httpd
