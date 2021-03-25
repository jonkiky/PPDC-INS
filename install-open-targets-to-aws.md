# Install Open Targets To AWS

Three instances :

OTG:  

      front-end 172.18.10.31:3006

OTP : 

      Front-end : 172.18.10.184:3000

     database & Backend: @172.18.10.41:9000

Connects to instance:

     Step1 : login bastion host. 

ssh -i  /Users/cheny39/Documents/EC2-Instance/bento-key.pem bento@3.219.1.112

      Step2:   
connects from  bastion host

ssh -i .ssh/devops centos@172.18.10.184

ssh -i .ssh/devops centos@172.18.10.41

ssh -i .ssh/devops centos@172.18.10.31



Install NVM

{% embed url="https://github.com/nvm-sh/nvm" %}



```text
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
```



```text
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```





**Install Yarn**

```text
sudo yum install -y make gcc*
npm install --global yarn
```

**Install git**

```text
sudo yum install git
```



**git clone repos**

```text
git clone https://github.com/opentargets/platform-etl-backend.git
```

```text
git clone https://github.com/opentargets/platform-api-beta.git
git clone https://github.com/opentargets/platform-app.git
git clone https://github.com/opentargets/genetics-app.git
```

**run front-end**

```text
cd platform-app
yarn install
yarn
```



Visit :

{% embed url="http://bento-alb-qa-529669248.us-east-1.elb.amazonaws.com:3000" %}



