<h1>Google cloud Web security scan</h1>

<h2>Description</h2>
One of cloud security professional's job is to prevent vulnerabilities in web apps deployed in the cloud. Cloud Service Providers equip security teams with various tools for the job. One of those tools in Google cloud is Web Security Scanner(WSS).
This project showcases the deployment, scanning and remediation of XSS vulnerability in simple Python Flask app using WSS.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Google cloud platform</b>
- <b>Python</b> 

<h2>Project walk-through:</h2>


For WSS to work properly we first need to set a static ip address using command: ```gcloud compute addresses create ip_address_name --region="REGION"``` where "REGION" is the region we would like to create the ip address in.
 <br/>
 <p align="center">
   <img src="https://github.com/user-attachments/assets/d1bd1d64-1985-469d-9143-45a92934a024" height="120%" width="120%" alt="Create static ip"/>
 </p>
<br />
Then we need to verify if the address was created properly
<br/> <br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/1adf9a94-ac81-4ee0-abd4-f13d3f109ffb" height="80%" width="80%" alt="IP verification"/>
</p>
<br />
Next step is to create vm instance that will host our web app. We can do this using command: ```gcloud compute instances create vm-instance-name --address=static-ip --no-service-account --no-scopes --machine-type=e2-micro --zone="ZONE" --metadata=startup-script='apt-get update; apt-get install -y python3-flask' ``` This command will create vm instance and give it the static ip we have created. The metadata part constains a script that will automatically install Flask upon VM startup. After the VM is created we can verify it under Compute Engine > VM instances in GCP navigation menu: <br/><br/> <p align="center">
<img src="https://github.com/user-attachments/assets/a5a5a316-80b9-4a32-9604-5926a566b00f" height="80%" width="80%" alt="VM verify"/></p>
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
