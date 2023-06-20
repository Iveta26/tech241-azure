# Intro to Azure

### What is cloud?
It is services to store, process and manage data remotely. The services are available on demand. Has its own cooling (water supply), and power (generators that will keep tings running if it goes down). They usually are a certain distance between each other in case of a disaster.


<br />

### Creating VM

1. Creating SSH key

Generating the key

``` PowerShell
iveta_6esu9b1@DESKTOP-GVT7GPM MINGW64 ~
$ mkdir .ssh

iveta_6esu9b1@DESKTOP-GVT7GPM MINGW64 ~
$ cd .ssh

iveta_6esu9b1@DESKTOP-GVT7GPM MINGW64 ~/.ssh
$ pwd
/c/Users/iveta_6esu9b1/.ssh

iveta_6esu9b1@DESKTOP-GVT7GPM MINGW64 ~/.ssh
$ ssh-keygen -t rsa -b 4096 -C "ivetaa1997@gmail.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/iveta_6esu9b1/.ssh/id_rsa): tech241-iveta-az-key
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in tech241-iveta-az-key
Your public key has been saved in tech241-iveta-az-key.pub
The key fingerprint is:
SHA256:y+bgzvWaXTjdZz/c4qKeXvL+sJKGHofPaXpHnikcc38 ivetaa1997@gmail.com
The key's randomart image is:
+---[RSA 4096]----+
|                 |
|                 |
|                 |
|                 |
|        S        |
|       . oooo.   |
|      . Bo=B=+o +|
|     o =.OOO*oo=E|
|     .+.*O@*++ooo|
+----[SHA256]-----+

iveta_6esu9b1@DESKTOP-GVT7GPM MINGW64 ~/.ssh
$ ls
tech241-iveta-az-key  tech241-iveta-az-key.pub
```

<br />


 Copying the key to use in our VM
 
 ```PowerShell
iveta_6esu9b1@DESKTOP-GVT7GPM MINGW64 ~/.ssh
$ cat tech241-iveta-az-key.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQDny2/VrYUZMAL54pVyTCFDSnA9GwOn0B46XlmFa+LNZP8SuKkTxzT/nyC9eO/cBU8qqeZdZm29T+3l4pUNxMNb9gCAl1BLOsMnHX60rdv1HENCBjsg+OW53NgAsQcMPIx4+Zo2NJ1mUouLzXMf0LF+2eGXlGg0pxXPElS0alBIa/P/4FBGwt/J9TL90A/VAf0fmnV9fC0z4mrGHnQbYZXhv9GIVPcv/yIdCLDZhDicFVLNHuYpy7OVk4K1tBaFsHSr0wspXDPtkd6Hb1e0nXM2jmVi9prVjclgDhpkDUfiDyBSfimKiB4++HDRlEHCo33oP/zcFINgnTN9zCy197nJAKVn0s3D10w6aj10FJggZbcRj/JetJF8AcxvIw6kIZx8KN7D1YrRSjW9iY50lzSLeLNojc1LEX1W8dKtwexYYCpNn824O7U6tGdvbWk7nONn26cVwcwx40LpsL/dCXDP6tC8sUl+L4gZDHdvfViKEgYfWJ4mkQI6PQtWsMlpuOcgclRFAlc/PN2Ig3VXKUFnlbRHtcTITF+mp+fNEOwWw2y6fHOG93ipcbjXkuKJTkcVcWOYenI65av1zCqydUu7ydsVFdY5LhbphsC5y++U5m/3cAPkVD7jNlCZhdjujqIL1LnwwzKgOdGFFicSf/ez+001ktJqfvmx7jmcE0aNPQ== ivetaa1997@gmail.com

 ```

<br />

Making the key read only 

```PowerShell
iveta_6esu9b1@DESKTOP-GVT7GPM MINGW64 ~/.ssh
$ chmod 400 tech241-iveta-az-key

iveta_6esu9b1@DESKTOP-GVT7GPM MINGW64 ~/.ssh
$ ls -l
total 8
-r--r--r-- 1 iveta_6esu9b1 197121 3389 Jun 20 15:47 tech241-iveta-az-key
-rw-r--r-- 1 iveta_6esu9b1 197121  746 Jun 20 15:47 tech241-iveta-az-key.pub

```

<br />

2. Logging into and out of VM

Logging in

```PowerShell
iveta_6esu9b1@DESKTOP-GVT7GPM MINGW64 ~/.ssh
$ ssh -i ~/.ssh/tech241-iveta-az-key adminuser@20.58.17.46

```

Logging out

```PowerShell
exit
```


<br />

### 4 types of systems
1.	**Public cloud** (small business, multiple occupant cloud, typically how its used)
2.	**Private cloud** (cloud infrastructure dedicated to a company, a company has its own cloud structure). Private doesn’t have to be connected to the internet
3.	**Hybrid could**, a mix of on prem servers and public cloud
4.	**Multi cloud**, using different cloud providers 

<br />


### What is Azure?
Microsoft Azure, often referred to as Azure, is a cloud computing platform run by Microsoft, which offers access, management, and development of applications and services through global data centers

<br />


### Scope levels of Azure

[Scope levels img](C:\Users\iveta_6esu9b1\azureNotes\Screenshot_5.png)

**Management groups** – helps to manage access policies compliance for subscriptions. Set a policy on certain things you want. Set permissions. Way to separate billing for marketing team, testing team etc. only specific size of VM for group is located, good for cost. There can be management group within a management group.

**Subscriptions** – separate billing. Each subscription. Most popular – pay as you go. Limits for subscriptions, eg number of recourse groups (limits are usually quite high)

**Resource groups** – containers.  Can’t be resource group within a resource group. You must have it in Azure.

**Resources**

<br />



### Types of cloud services 

[Types of services img](C:\Users\iveta_6esu9b1\azureNotes\Screenshot_6.png)

**IaaS** – infrastructure as a service

**PaaS** – platform as a service. (PaaS) is a complete cloud environment that includes everything developers need to build, run, and manage applications—from servers and operating systems to all the networking, storage, middleware, tools, and more.

**SaaS** – software as a service. Software as a service is a software licensing and delivery model in which software is licensed on a subscription basis and is centrally hosted. SaaS is also known as on-demand software, web-based software, or web-hosted software.
On-Premises - servers are on premises

<br />


### CapEx vs OpEx
Capital expenditure vs operational expenditure.

**Capital expenditure** – upfront costs (e.g equipment, if on prem you must buy servers. Mostly on prem, they still have some operational exp)

**Operational expenditures** – expenses are spread out throughout the year (the cloud)
