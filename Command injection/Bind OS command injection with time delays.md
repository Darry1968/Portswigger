## Title: Bind OS command injection with time delays

url: [URL](https://0adf00bb03c666a781afd49b00130040.web-security-academy.net/)

***Description***: This lab contains a blind OS command injection vulnerability in the feedback function. The application executes a shell command containing the user-supplied details. The output from the command is not returned in the response.
To solve the lab, exploit the blind OS command injection vulnerability to cause a 10 second delay.

***Blind vulnerabilities*** - This means that you will not be able to see the response of command you have injected because the application does not return the output from the command within its HTTP response. But these kind of vulnerabilities are still exploitable.
One of the best way to detect OS command injection is working or not you can create time delay using some methods so that you can say an application is vulnerable to OS command injection.

To create time delay you can use ping command by specifying how many ICMP (Internet Control Message Protocol) packets.
As they said vulnerability is in feedback function so I directly opened Burp Suite to intercept the request and here's what I get,

![image](https://github.com/Darry1968/Portswigger/assets/104063375/1d9d34ff-8902-40f6-a244-ac2e465963ba)

Now you can see the parameters that are sent when you you click that submit feedback button which are<br>
`
name=b&email=b%40gmail.com&subject=C&message=bc
`
<br>
As they said the application uses mail service for submission of feedback which is given by
<br>
`
mail -s "This site is great" -aFrom:peter@normal-user.net feedback@vulnerable-website.com
`
<br><br>
Now we are ready with everything that is required to know, we just have to inject our command in email section because message is in double quotes and we have to terminate them, that kinda extra work to do.

` payload - x+||+ping+-c+10+127.0.0.1+|| `
and that's it you will be able to see the delay in response of 10 seconds. 
