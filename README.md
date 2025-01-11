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
After installing operating systems and updateing and upgrading all the packages in Ubuntu VMs I began installing software. First I installed Elasticsearch and Kibana by downloading them using wget command and then running dpkg -i command passing each deb file. Diring Elasticsearch installation a admin account is created the credentials should be copied and saved somewhere safe.
After installing Elastic search there is one update to the configuration that has to be done. I have edited the config file using sudo nano /etc/elasticsearch/elasticsearch.yml. In the YAML file I have uncommented the following two lines and also changed the IP to my VMs IP leaving the port number as is<br/><br/> <p align="center">
<img src="https://github.com/user-attachments/assets/2c336fbc-a810-4c0c-890f-1ded05679fce" height="80%" width="80%" alt="IP verification"/>
 </p>
<br />
After saving the file I ran the elasticsearch service by using following commands: sudo systemctl daemon-reload, sudo systemctl enable elasticsearch.service, sudo systemctl start elasticsearch.service
<br />
After installing Kibana I have edited it configuration and uncommenting the following lines and setting values for URL and host putting in VMs IP:<br/><br/> <p align="center">
<img src="https://github.com/user-attachments/assets/ff9c60fc-eb47-4417-8ec8-44cbdbd3687a" height="80%" width="80%" alt="IP verification"/>
 </p>
<br />

