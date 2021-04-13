# CCDI-Open Target

## **Repositories**

**Forked repositories**

Platform-api-beta : [https://github.com/CBIIT/ppdc-otp-backend](https://github.com/CBIIT/ppdc-otp-backend)

platform-app:  [https://github.com/CBIIT/ppdc-otp-frontend](https://github.com/CBIIT/ppdc-otp-frontend)

genetics-app:  [https://github.com/CBIIT/ppdc-otg-frontend](https://github.com/CBIIT/ppdc-otg-frontend)

**Created Repositories:**



## **Sites' URL** 

open targets platform:  [https://ppdc-otg-dev.bento-tools.org](https://ppdc-otg-dev.bento-tools.org/)

open targets genetics: [https://ppdc-otp-dev.bento-tools.org](https://ppdc-otp-dev.bento-tools.org/)

## Jenkins

{% embed url="https://jenkins.bento-tools.org/job/PPDC/" %}



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

