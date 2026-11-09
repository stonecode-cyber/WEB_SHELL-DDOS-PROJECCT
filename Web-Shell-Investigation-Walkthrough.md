Denial-of-Service (DoS) attacks can take many forms, but their ultimate aim is to disrupt or completely block access to a website or web service.
 Distributed Denial-of-Service (DDoS) attacks utilize botnets in their attack,an army of compromised devices under their control.

**### Types of DOS**

- Slowris - Sending many partial HTTP requests to tie up server resources
- HTTP flood- Sending a large number of HTTP requests to overwhelm the server
- Cache Bypass-Bypassing CDN edge servers and forcing the origin server to respond
- Oversize query-Forcing the server to process large, resource-intensive requests
- Login/Form Abuse-Overloading authentication logic with login attempts or password resets
- Faulty Input Validation Abuse-Exploiting poorly designed input handling

**### INDICATORS OF COMPROMISED**
**Hight request rate** -A resource-heavy page like /login is flooded with requests to overwhelm authentication processes
**Odd User-Agents**-Attackers spoof outdated or unusual User-Agents to blend in or bypass filters.
**Geographic Anomalies**-  A globally distributed botnet may utilize IP addresses from around the world
**Burst Timestamps**- A sudden spike of requests packed into the same second creates an unnatural traffic pattern that points to automation
**Server Error-**-  Sudden surge of server error responses (500 - 511) indicates resources are maxed out and the service is struggling under attack traffic.
**Login Abuse-**- Attackers craft queries that overload the server, forcing it to load huge amounts of information and slowing it down for everyone.

**### HAND ON SCENERIO**
Your bicycle parts website has undergone a denial-of-service attack. Open up the access.log file on the user's Desktop to begin your investigation. The logs include a mix of normal user-generated traffic and attacker traffic. While you comb the logs, be on the lookout for repeated requests to the same page and remember the indicators you learned about in this task. Best of luck!

**TASK 1:What is the attacker’s IP address?**

<img width="467" height="284" alt="Image" src="https://github.com/user-attachments/assets/b9eee649-9a94-452e-b2b6-a0ce46e6ef0a" />

<img width="467" height="284" alt="Image" src="https://github.com/user-attachments/assets/e22d65f7-6b05-42ae-ba79-860531e5743b" />

As i ahve noted the indicators above, i serach through the log to look for any trace of DDOS, i found out there was a particular IP that sent mutiple request within seconds before nthe website stop responding as shown in the screenshot below:

<img width="472" height="295" alt="Image" src="https://github.com/user-attachments/assets/ec4248e2-78d3-4ae9-a00a-e2f1a1b2a730" />

**TASK 2:Which page is repeatedly targeted by the attacker’s requests?**

 The attacker use flooded the website with  login requst which is k now to be one of the heavy traffic due to authentication.

<img width="470" height="326" alt="Image" src="https://github.com/user-attachments/assets/a069eeaf-487a-4a54-b19d-354d64fd1422" />

**TASK 3:After the attack, what error code do legitimate users receive?**

After the attacker flooded the webiste with the excessive login request,the website was brought down and return the 503 code which indicate  server unavailable.

<img width="467" height="284" alt="Image" src="https://github.com/user-attachments/assets/75269295-19d6-458f-aa1c-4e77912bc605" />
 
**### USING SPLUNK TO ANALYSE WEB NETWORK TRAFFIC FOR DDOS**

TASK 1:What was the most frequently requested uri?
In this task , i opened my splunk, select the search &Reporting application. after which i putbthe filter **index = "main"** , this show the  most frequent request to be  **SEARCH ** request, and select the url filter as shown below:

<img width="474" height="302" alt="Image" src="https://github.com/user-attachments/assets/a083f161-96d0-4aa0-89fb-2ef46cb63489" />

<img width="349" height="273" alt="Image" src="https://github.com/user-attachments/assets/1acd53a5-9c05-407c-a93d-11d534c15084" />


<img width="384" height="281" alt="Image" src="https://github.com/user-attachments/assets/d69b9a00-313a-4383-8b1b-55a10c6adf7f" />

**TASK 2:Which clientip made the most requests to the target uri?**

I select the client Ip filter as shown below the  ip with most request is **203.0.113.7** as shown below:

<img width="452" height="347" alt="Image" src="https://github.com/user-attachments/assets/15623273-2126-46fc-bcbc-11efe9ba6322" />

<img width="340" height="284" alt="Image" src="https://github.com/user-attachments/assets/e8b323d3-9aef-4787-97f6-fb02eab46ec5" />

TASK 3: How many IP addresses were part of the botnet that attacked your website?
In this task i filter the traffiuc from top ip addresss withnthe filter **index ="main"| top limit=100 clientip**   this diplay the top Ip address   in which 60  of itare from  botnet as shown below:

<img width="451" height="209" alt="Image" src="https://github.com/user-attachments/assets/3abb9e9b-c55d-4397-b82f-bdf92a9a1638" />

TASK 4: Which useragent was most commonly used by the attacking traffic?
In this task, i select Useragent field which reveal the  most used User agent  and the most common User Agent in the traffic is **Java/1.8.0_181** which was used 135 for 135 traffics.

<img width="477" height="319" alt="Image" src="https://github.com/user-attachments/assets/d1adf372-c9cf-47f0-9381-bb21727a68db" />

<img width="388" height="297" alt="Image" src="https://github.com/user-attachments/assets/10d0d181-e47b-45a8-a633-c59e85aaf0ae" />

TASK 5:Use the timechart command to visualize the requests.
What is the peak number of requests made per second during the attack?

In this task, i made use of the request time (req_time) filter , this display the peak number of request per seconds to be 207 request at _**13:12:22**_ as shown below:

<img width="484" height="338" alt="Image" src="https://github.com/user-attachments/assets/fd6ec1e7-691e-4dae-9789-6c49daedca74" />

<img width="373" height="305" alt="Image" src="https://github.com/user-attachments/assets/1033c73f-fdfc-427f-97b1-d7f96ad04e06" />
 


