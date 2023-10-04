## Title: Blind OS command injection with out-of-band interaction.

url: [URL](https://portswigger.net/web-security/os-command-injection/lab-blind-out-of-band)

***Description:*** This lab contains a blind OS command injection vulnerability in the feedback function. The application executes a shell command containing the user-supplied details. The command is executed asynchronously and has no effect on the application's response. It is not possible to redirect output into a location that you can access. However, you can trigger out-of-band interactions with an external domain.<br>
To solve the lab, exploit the blind OS command injection vulnerability to issue a DNS lookup to Burp Collaborator.<br><br>
**Note:**
To prevent the Academy platform being used to attack third parties, our firewall blocks interactions between the labs and arbitrary external systems. To solve the lab, you must use Burp Collaborator's default public server.

***Solution:*** This lab also an extension of previous lab but in this we are not able to create time delay or redirect input into a file which we can access but as they said we can trigger out-of-band interaction with external domains. Because of the the WAF to solve this lab we require Burp's Collaborator which only available in Professional version.
Same as before open Burp Suite, intercept the request modify the content and send that's it.
First intercept:

![image](https://github.com/Darry1968/Portswigger/assets/104063375/ff6db646-4e3e-455e-81b0-78354df6d508)

To solve the lab we have to issue a DNS lookup to Burp's Collaborator. How we can do that let's see, DNS lookup of any doamin can be done by the ` nslookup ` command. how we can use Burp's Collaborator let's see,
First modify the content as we did before and then right click -> insert collabortor payload like this:

![image](https://github.com/Darry1968/Portswigger/assets/104063375/a3e3f20f-8b9b-48a5-a4f1-30d53f66dd8d)

Send your request and open Collabortor tab in burp and then click Poll now and then you will be able to see the results of nslookup. Like this:

![image](https://github.com/Darry1968/Portswigger/assets/104063375/2bc13f56-607b-4e46-a2da-77c8fb55469e)
Solved <3.
