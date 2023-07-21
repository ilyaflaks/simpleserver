# AWS EC2 COMMANDS

Sample App is from this video: https://www.youtube.com/watch?v=BAGTrupuE70&t=10s. The Github repo: https://github.com/haresrv/sqldeploy

sudo yum update -y
sudo amazon-linux-extras list | grep nginx
sudo amazon-linux-extras enable nginx1
sudo yum clean metadata
sudo yum -y install nginx
nginx -v
sudo su
cd /
ls
mkdir testapp
cd testapp
aws s3 cp s3://nodemysqlmkmk --region us-east-1 . --recursive
ls

sudo curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
. ~/.nvm/nvm.sh
nvm install node
node -e "console.log('Running Node.js ' + process.version)"
ls
cd NodeJS
ls
npm install express body-parser cors mysql
While still in NodeJS folder...
Now make sure to allow the security group of your ec2 instance allow connection from a custom tcp port 3000-4000 from anywhere i.e. 0.0.0.0
Now, do
node server.js (leave this running)

In a new session manager tab, go back to the testapp folder and do the following
cd /
ls
sudo su
ls
cd testapp/
ls
rm -rf package-lock.json
ls
npm install
ls
npm start
To see the app, open your browser and enter the IP of your instance and append i.e. 3000, e.g. http://3.238.157.100:3000
