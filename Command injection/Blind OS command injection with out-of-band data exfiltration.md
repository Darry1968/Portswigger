## Title: Blind OS command injection with out-of-band data exfiltration.

url: [URL](https://portswigger.net/web-security/os-command-injection/lab-blind-out-of-band-data-exfiltration)

***Description:*** This lab contains a blind OS command injection vulnerability in the feedback function. The application executes a shell command containing the user-supplied details. The command is executed asynchronously and has no effect on the application's response. It is not possible to redirect output into a location that you can access. However, you can trigger out-of-band interactions with an external domain.<br>
To solve the lab, execute the whoami command and exfiltrate the output via a DNS query to Burp Collaborator. You will need to enter the name of the current user to complete the lab.<br><br>
**Note:**
To prevent the Academy platform being used to attack third parties, our firewall blocks interactions between the labs and arbitrary external systems. To solve the lab, you must use Burp Collaborator's default public server.

***Solution:*** Same as previous lab we have to use the same concept as we did in the last lab. But this time we have to execute some commands using DNS lookup lets see how we can do that:
Firstly Intercept request then modify content like this:

![image](https://github.com/Darry1968/Portswigger/assets/104063375/32a60803-a225-44f8-93e3-d3dbe2d1a77e)
Now wait before sending your request we haven't modify the content correctly. OS command we haven't specified and portswigger has shown us how we can do that using DNS lookup like this

![image](https://github.com/Darry1968/Portswigger/assets/104063375/1ce7b0a0-cdad-4dff-acce-5c2af08a42a4)

So according to this modify your payload 
![image](https://github.com/Darry1968/Portswigger/assets/104063375/40716d4d-4d28-4cef-aa58-2a39a005c180)

And that's it send your request and open Collaborator and you will see the DNS response.
![image](https://github.com/Darry1968/Portswigger/assets/104063375/7b5e97c1-b757-4dcf-bd3c-350a64be1c11)

In Description you will see the output of whoami command. Submit that name and solved.
