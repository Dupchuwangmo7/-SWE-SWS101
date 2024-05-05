### Executive Summary 
This machine is developed by one of the lecturers and wants to release it to the internet. But before releasing it, he wants to undergo penetration testing for betterment of the server.

## Approach
I performed testing for this server from 15th of April to 5th of  May with a mission to uncover weakness and security flaws. I was like blind attacker so, without causing any damage, I just investigated the vulnerabilities found.

## Scope
Since this server is going to be uploaded to the internet it is important to do the penetration test before that so that there won’t be any unauthorized access to the data inside the server. I will be going through every port that is vulnerable and try to exploit it for the penetration test.

## Assessment Overview and Recommendations
During this penetration testing, I have come across many vulnerabilities which are a threat for the server when it is deployed into the internet. The database server is not secure as the attacker can gain unauthorized access easily. These issues might lead to data bleach in the future and can cause various problems. 

Manger service is also not secure as I have gained access to it and the username and the password for manager is also not so secure as an attacker can gain it by brute force. If the username and password is secure enough they won’t have access to it. Even more, the files under manager service do not have any access password as once the access to manager service is gained all the files are accessed.

I would like to recommand to change username and password for security reason and to close ports that an attacker usually attacks.


### Network Penetration Test Assessment Summary

I began with all testing activities from the perspective of an unauthenticated user on the internal network. 

Summary of Findings

While performing the penetration testing, I was able to break into the server through  different ways.

![findings](<../Vulnversity/search/Pasted image.png>)

### Network Compromise Walkthrough

![nmap scan](<../Vulnversity/SCAN/Screenshot from 2024-05-04 01-19-29.png>)

While doing the nmap scan I found out there are 23 ports open. 

To start with, I tried breaking into port number 80 which is http port. To break into that port I used metasploit.


Run the msfconsole to use metasploit.
![1st step](<../Vulnversity/Evidences/80/Pasted image 1.png>)

I search for php_cgi using a command `search php_cgi` because  it is a specification “protocol” for transferring information between a Web server and a CGI program. A CGI program is any program designed to accept and return data that conforms to the CGI specification.

![2nd step](<../Vulnversity/Evidences/80/Screenshot from 2024-05-05 21-17-31.png>)

Php_cgi only has one exploitable module so I used that one to proceed further. Modules  contain all technical information to gain unauthorized access.

![3rd step](<../Vulnversity/Evidences/80/Screenshot from 2024-05-05 21-18-01.png>)

Then I ran the `show options` command to find out more about that module. 

![4th step](<../Vulnversity/Evidences/80/Screenshot from 2024-05-05 21-18-51.png>)


Here, I can see that RHOST AND LHOST are not set yet. So I am going to set RHOST to our target ip address and LHOST to port 80.

![5th step](<../Vulnversity/Evidences/80/Screenshot from 2024-05-01 22-32-05.png>)

Then I ran the command <exploit > to check if this method works or not. And yes it worked and I was able to gain root access to the server.
![6th step](<../Vulnversity/Evidences/80/Screenshot from 2024-05-01 22-32-52.png>)

![6th step](<../Vulnversity/Evidences/80/Screenshot from 2024-05-01 22-33-14.png>)

Here, I have unauthorized root access and I have viewed all the documents.


The next port that I tried to access was port number 5900 which is Virtual Network Computer. Since this port is open I am going to check whether I gain access or not. For this one, again we will use metasploit to exploit this port.

 First, I will open metasploit
![1st step](<../Vulnversity/Evidences/5900/Screenshot from 2024-05-05 21-10-39.png>)

I search for vnc with command `search vnc `
![alt text](<../Vulnversity/Evidences/5900/Screenshot from 2024-05-04 01-23-20.png>)

![alt text](<../Vulnversity/Evidences/5900/Screenshot from 2024-05-04 01-23-30.png>)


Here I can find lots of modules. I went through these modules and came across module number 109 which will help me gain access in a quicker way.  So I used that module.
![alt text](<../Vulnversity/Evidences/5900/Screenshot from 2024-05-04 01-24-42.png>)

I search for options inside this module
![alt text](<../Vulnversity/Evidences/5900/Screenshot from 2024-05-05 21-12-00.png>)

And i did setups like seting RHOSTS to target and making the search when it username and password matches 

![alt text](<../Vulnversity/Evidences/5900/Screenshot from 2024-05-05 21-13-29.png>)

![alt text](<../Vulnversity/Evidences/5900/Screenshot from 2024-05-05 21-13-54.png>)

And after setuos I ran it.
![alt text](<../Vulnversity/Evidences/5900/Screenshot from 2024-05-05 21-14-14.png>)

Now, to view the virtual machine 
![alt text](<../Vulnversity/Evidences/5900/Screenshot from 2024-05-04 01-27-23.png>)

![alt text](<../Vulnversity/Evidences/5900/Screenshot from 2024-05-04 01-27-41.png>)

Now that I can get into the virtual machine, this port also needs to be secure for security reasons.

The next port I tried was TCP/6667 is an IRC port, which is often used to control the malware/botnet. And this port is a high-number port that does not require elevated privileges. I will use metasploit to exploit this port.

![alt text](<../Vulnversity/Evidences/6667/Screenshot from 2024-05-04 17-23-37.png>)

Now, I will use `search unreal` to search modules.
![alt text](<../Vulnversity/Evidences/6667/Screenshot from 2024-05-04 17-23-49.png>)

Here, I have found 5 different modules but i will use last one because it is easy to break in.
![alt text](<../Vulnversity/Evidences/6667/Screenshot from 2024-05-04 17-24-05.png>)

To find out about options this module offers 
![alt text](<../Vulnversity/Evidences/6667/Screenshot from 2024-05-04 17-24-18.png>)

It gives us options to set RHOSTS which is the target ip address. So I will set my target ip address. 

![alt text](<../Vulnversity/Evidences/6667/Screenshot from 2024-05-04 17-24-34.png>)


Now, I will search for payloads.  A payload is a piece of malicious code that is designed to execute a specific action on a target system

![alt text](<../Vulnversity/Evidences/6667/Screenshot from 2024-05-05 22-46-36.png>)

I will set payload in such that it will break the ruby because Ruby on Rails can be used to build cyber security applications because it provides the best protection against different types of XSS attacks. 

![alt text](<../Vulnversity/Evidences/6667/Screenshot from 2024-05-04 17-25-50.png>)

To check if this is ready to exploit 
![alt text](<../Vulnversity/Evidences/6667/Screenshot from 2024-05-04 17-26-05.png>)

We see that our target ip address is set and it is ready to exploit.

![alt text](<../Vulnversity/Evidences/6667/Screenshot from 2024-05-04 17-26-18.png>)

And, I have found another vulnerability where a hacker might use it to exploit the machine. This port also needs to make secure.


The next port I am going to try is port number 8180 and this port is used  to access the Application Service Controller RESTful APIs. Here also I am going to use metasploit to exploit the port to gain username and password for the application services.

![alt text](<../Vulnversity/Evidences/8180/Screenshot from 2024-05-05 21-28-44.png>)

I am going to use tomcat to search  because the port 8081 is running on Apache Tomcat 

![alt text](<../Vulnversity/Evidences/8180/Screenshot from 2024-05-05 21-29-08.png>)

![alt text](<../Vulnversity/Evidences/8180/Screenshot from 2024-05-05 21-29-13.png>)

I went through these modules and found out that 63 gives us login details. I will use that to proceed further.

![alt text](<../Vulnversity/Evidences/8180/Screenshot from 2024-05-05 21-31-11.png>)

![alt text](<../Vulnversity/Evidences/8180/Screenshot from 2024-05-05 21-31-41.png>)

Here in the options, the target host and port number is not set and when we brute force it won’t stop when the admin name matches the password. I will do the set ups.

![alt text](<../Vulnversity/Evidences/8180/Screenshot from 2024-05-05 21-32-30.png>)

![alt text](<../Vulnversity/Evidences/8180/Screenshot from 2024-05-05 21-35-53.png>)

![alt text](<../Vulnversity/Evidences/8180/Screenshot from 2024-05-05 21-36-00.png>)

Now that the setup is done, I will exploit it.

![alt text](<../Vulnversity/Evidences/8180/Screenshot from 2024-05-05 21-36-47.png>)

![alt text](<../Vulnversity/Evidences/8180/Screenshot from 2024-05-05 21-36-54.png>)

Now, we know our username and password for the application services. We will search for `10.3.21.140:8180/manager/html`

![alt text](<../Vulnversity/Evidences/8180/Screenshot from 2024-05-05 21-38-00.png>)

Yes, I can access this manager file and can view most of the files.

![alt text](<../Vulnversity/Evidences/8180/Screenshot from 2024-05-05 21-39-31.png>)


![alt text](<../Vulnversity/Evidences/8180/Screenshot from 2024-05-05 21-39-56.png>)


This concludes that manager services are also not secure and this might lead to data bleach in the future.


The next port I will try is port number 5432 which is Postgres Database Server. This port will contain every data of the server so, this port must be secure. To exploit it I will use metasploit.

![alt text](<../Vulnversity/Evidences/postgres/Screenshot from 2024-05-05 22-00-43.png>)

I will search for postgres with command `search postgres`

![alt text](<../Vulnversity/Evidences/postgres/Screenshot from 2024-05-05 22-03-37.png>)

I will use module number 27 to exploit further 


![alt text](<../Vulnversity/Evidences/postgres/Screenshot from 2024-05-05 22-03-53.png>)

![alt text](<../Vulnversity/Evidences/postgres/Screenshot from 2024-05-05 22-04-04.png>)

I will set RHOSTS with the ip address of target, lport as 80 and lhost as my current ip address when i am connected to that particular wi-fi where my server is hosted.

![alt text](<../Vulnversity/Evidences/postgres/Screenshot from 2024-05-05 22-05-19.png>)

![alt text](<../Vulnversity/Evidences/postgres/Screenshot from 2024-05-05 22-05-24.png>)

![alt text](<../Vulnversity/Evidences/postgres/Screenshot from 2024-05-05 22-12-07.png>)

Now that setups are done I will exploit 
![alt text](<../Vulnversity/Evidences/postgres/Screenshot from 2024-05-05 22-14-10.png>)

So, I can gain unauthorized access to the database server and I can even view all the data inside it and i can also touch new files. 

![alt text](<../Vulnversity/Evidences/postgres/Screenshot from 2024-05-05 22-16-02.png>)



To conclude most of the ports are not secure and attackers can easily gain access to the server. The database, manager services and virtual machines are not secure and username nad password are easy to guess. I would like to recommend making it secure before posting it to internet for safety. This could help both users and developer in the future. 