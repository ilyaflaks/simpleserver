## How to deploy a Node/React app to AWS EC2

- Go to [aws.amazon.com/](https://aws.amazon.com/), EC2, launch a new instance
- Give your instace a name
  -Under "Application and OS Images (AMI)" select Ubuntu
- Under "Key pair (login)" click "Create new key pair"
- Give your key pair a name (for example "new-ec2-key-pair"), type RSA, extension: .pem, click "Create key pair" button. Save it on your computer, for now Downloads folder is ok
- On your Mac, go to the root folder (~), cd /.ssh, run the command:
  **mv ~Downloads/new-ec2-key-pair.pem ~/.ssh/**
- Back to instance, under "Network Settings" leave the default "Create security group" selected and the default "Allow SSH traffic from Anywhere" checked
- Leave the rest of the settings as is, click "Launch Instance"
- Wait a few seconds for the instance to start,
- Click on the instance, go to "Security", click on the security group, it will be called "launch-wizard-#" by default
- Click "Edit Inbound Rules", "Add Rule", select "Custop TCP", under port range enter the port that your Node app is using, in this case **3030**

- Go back to the list of instances, select the one you just created, click connect, select "SSH Client" tab

- Open the terminal on your computer, cd into .ssh, run the command
  ** chmod 400 new-ec2-key-pair.pem **
- Next, copy the example command from the instructions and run it. It will look like this:
  ** ssh -i "new-ec2-key-pair.pem" ubuntu@ec2-##-###-###-###...amazonaws.com **
- Type 'yes', press Enter. This will connect to the Ubuntu instance
- run **sudo apt-get install curl**
- run **curl -sL https://deb.nodesource.com/setup_16.x | sudo -E bash - **
- run **sudo apt-get install nodejs**
- run **sudo npm install pm2@latest -g **
- clone the repo you want to deploy by running "git clone". Example:
  **git clone https://github.com/ilyaflaks/simpleserver.git**
- cd into the folder, in this case "simpleserver", run **npm i**, run **node index.js** or **app.js** depending on your entry point
- On the EC2 console of your instance, copy the public IPv4 address, paste it into your browser, add ":" followed by the port (in this case 3030), remove the "s" from "https://" and press Enter
- Your Node app should show up!
- [http://13.52.248.247:3030/](http://13.52.248.247:3030/)

### Sources:

[How to deploy Node Express API to an AWS EC2 Ubuntu instance](https://jonathans199.medium.com/how-to-deploy-node-express-api-to-ec2-instance-in-aws-bc038a401156)
