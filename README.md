<h1>ELK stack SOC home lab</h1>

<h2>Description</h2>
This is a guided project created during "30 day SOC analyst challenge" on MyDFIR YouTube channel. It aims at creating a SOC lab using Elasticsearch, Logstash and Kibana stack. It also uses Mythic framework and Kali Linux to create attacks, as well as Sysmon on Windows Server to feed the logs into ELK.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Elasticsearch</b>
- <b>Logstash</b>
- <b>Kibana</b>
- <b>Mythic framework</b>
- <b>Sysmon</b> 

<h2>Project walk-through:</h2>


First step is to create 7 VMs in VirtualBox: 
- <b>4 Ubuntu servers</b>
- <b>2 Windows servers</b>
- <b>1 Kali Linux machine</b>
 <p align="center"> <img src="https://github.com/user-attachments/assets/a2b7911a-c2e8-43b1-90b9-b53aefae5b39" height="80%" width="80%" alt="IP verification"/>
 </p>
<br />
Next step was to create a NAT Network and attach each VM to it (I have used the default setting in VirtualBox).
<br/><br />
To make configuration and installation of tools in the Ubuntu Server VMs I have created port forwarding rules in NAT network setting to be able to SSH into VMs: <br/><br/> <p align="center">
<img src="https://github.com/user-attachments/assets/328a9099-beb9-455e-b3cc-74cdeb839b43" height="80%" width="80%" alt="VM verify"/></p>
<br />

Then we create a firewall rule to allow connections to our app using following command ```gcloud compute firewall-rules create wss-scan-demo \
--direction=INGRESS --priority=1000 \
--network=default --action=ALLOW \
--rules=tcp:8080 --source-ranges=0.0.0.0/0``` To verify the rule creation we go to Navifation menu > VPC networks > Firewall: <br/><br/> <p align="center">
<img src="https://github.com/user-attachments/assets/76ef8c62-9cb1-43bf-865e-79219c415fcd" height="80%" width="80%" alt="Firewall verify"/></p>
<br/>
Then we SSH into our instance and simply upload the app.py file:
<br/><br/> <p align="center">
 <img src="https://github.com/user-attachments/assets/e8db15f1-0cdd-448e-8d87-8fb7d7f39027" height="80%" width="80%" alt="VM verify"/></p>
<br/>
<br/>

In order to run the app we perform ```python3 app.py``` command
<br/><br/> <p align="center">
 <img src="https://github.com/user-attachments/assets/f9c192ff-ec4c-4682-a484-9c972f55cb2d" height="80%" width="80%" alt="VM verify"/></p>
<br/>
We can now verify if the app contains  XSS vulnerability:
<br/><br/> <p align="center">
<img src="https://github.com/user-attachments/assets/cd756658-f48e-4d83-9e2d-83cd24a9946f" height="80%" width="80%" alt="VM verify"/></p>
<p align="center"><img src="https://github.com/user-attachments/assets/1a73d67c-195a-4864-8cbc-bf8c71b2fedf" height="80%" width="80%" alt="VM verify"/></p>
<br/>
Now we go back to GCP to set up Web Security Scanner. (NOTE: WSS API is not enabled by default so before first usage it must be enabled manually by going into Navigation menu > APIs and Services > Enable APIs and services and typing Web Security Scanner in search bar and clicking on the tile and then on Enable.) The WSS scan setup window:
<br/><br/> <p align="center">
<img src="https://github.com/user-attachments/assets/e728c092-8ffe-441f-9db8-508fb7908053" height="80%" width="80%" alt="VM verify"/></p>
<br/>
After hitting Save and running the scan we can see that there was an XSS vulnerabiliy found. Also we can see in the SSH window how the scan was logged by our vm:
<br/><br/> <p align="center">
 <img src="https://github.com/user-attachments/assets/63e0f920-2967-4164-82df-665807fbf27c" height="80%" width="80%" alt="VM verify"/></p>
<br/>
To remediate the XSS we can use flask method called escape that converts characters &, <, >, ‘, and ” in string to HTML-safe sequences:
<br/><br/> <p align="center">
  <img src="https://github.com/user-attachments/assets/420789ed-e2e1-44b5-bdd3-de790e91e3fa" height="80%" width="80%" alt="VM verify"/></p>
<br/>
When we run the app again and try to paste javascript in search box, instad of previous alert we will get the following result:
<br/><br/> <p align="center">
 <img src="https://github.com/user-attachments/assets/a10d60d8-8200-4800-9dfa-8f4700ec9121" height="80%" width="80%" alt="VM verify"/></p>
<br/>
Now when we run our WSS scan again we can see that indeed the vulnerability has been patched:
<br/><br/> <p align="center">
  <img src="https://github.com/user-attachments/assets/bd50e15e-5088-4085-864a-7e221a95a6da" height="80%" width="80%" alt="VM verify"/>
