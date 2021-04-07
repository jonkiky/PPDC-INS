# Install Open Targets To AWS

**Three instances :**

**OTG:**  

      front-end 172.18.10.31:3006

**OTP :** 

      Front-end : 172.18.10.184:3000

     database & Backend: @172.18.10.41:9000

**Connects to instance:**

     Step1 : login bastion host. 

ssh -i  /Users/cheny39/Documents/EC2-Instance/bento-key.pem bento@3.219.1.112

      Step2:   
connects from  bastion host

ssh -i .ssh/devops centos@172.18.10.184

ssh -i .ssh/devops centos@172.18.10.31

ssh -i .ssh/devops centos@172.18.10.41



**Install NVM**

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

**Download OTG output files to VM**

```text
sudo yum install wget
wget -r ftp://ftp.ebi.ac.uk/pub/databases/opentargets/platform/21.02/output/ETL/

```

Visit :

{% embed url="http://bento-alb-qa-529669248.us-east-1.elb.amazonaws.com:3006" %}

{% embed url="http://bento-alb-qa-529669248.us-east-1.elb.amazonaws.com:3000" %}

Nginx 

{% embed url="https://www.javatpoint.com/installing-nginx-on-mac" %}

Nginx issue: why don't work react-router-dom after build?



There is a very `specific reason` behind this scenario.

_**1st solution :**_ react is a single page application so when you have build the application , server know only about index.html so for any other `url` you will have to `configure` server for `fallback mechanism to index.html` and after react app will take care of url handling.

_**2nd solution**_: if you use `hash router` than this issue will not occur.  
the reason behind using hash router is [know more about hashrouter and it's use cases](https://stackoverflow.com/a/51976069/8138584)

```text
import { HashRouter as Router, Route, Switch } from "react-router-dom" 
```

