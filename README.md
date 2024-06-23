# Deploying a Node Js Application on AWS EC2

### Testing the project locally

1. Clone this project
```
git clone this project
```
2. Setup the following environment variables - `(.env)` file
```
DOMAIN= "http://localhost:3000"
PORT = 3000
STATIC_DIR = "./client"

#API KEYS
PUBLISHABLE_KEY = "SAMPLE_pk_test_51PT9q5P4imvl0i3bJ3J5IuwqInz1HSfv2polzXDIBTz2tPmil3K6ZC69IGTbWOQ1MXYRUkmO1GNHzp2bu9VS6V3B00xBmdhM7A"

SECRET_KEY = "SAMPLE_sk_test_51PT9q5P4imvl0i3bPGIkTankSsf9GvGCdIP4Q5V6BvjJxZkRyOA5OtOvw382twUnf1tFErb1k4kz8J7SK8Vs18XB00ZsrRGhlV"
```
3. Initialise and start the project
```
npm install
npm run start
```

### Set up an AWS EC2 instance

1. Create an IAM user & login to your AWS Console
    - Access Type - Password
    - Permissions - Admin
2. Create an EC2 instance
    - Select an OS image - Ubuntu
    - Create a new key pair & download `.pem` file
    - Instance type - t2.micro
3. Connecting to the instance using ssh
```
ssh -i instance.pem ubunutu@<IP_ADDRESS>
```

### Configuring Ubuntu on remote VM

1. Updating the outdated packages and dependencies
```
sudo apt update
```
3. Install Git - [Guide by DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-22-04) 

    Check your git version 


```
git --version

```

If Git not found 

```
Run the following commands in sequence: 

sudo apt update 

sudo apt install git

git --version
```
4. Configure Node.js and `npm` - [Guide by DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-22-04)

```
Run the following commands : 

sudo apt install nodejs

sudo apt install npm


```


### Deploying the project on AWS

1. Clone this project in the remote EC2

2. Setup the following environment variables - `(.env)` file
```
DOMAIN= ""
PORT=3000
STATIC_DIR="./client"

PUBLISHABLE_KEY=""
SECRET_KEY=""
```
> For this project, we'll have to set up an [Elastic IP Address](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html) for our EC2 & that would be our `DOMAIN`

3. Initialise and start the project
```
npm install

npm run start
```

> NOTE - We will have to edit the **inbound rules** in the security group of our EC2, in order to allow traffic from our particular port

