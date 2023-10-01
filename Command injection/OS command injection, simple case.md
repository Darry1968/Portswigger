## Title: OS command injection,simple case.

url: [URL](https://0a1c00780318af91838f254000b60010.web-security-academy.net/)

They said this lab contains an OS command injection vulnerability in the product stock checker. And to solve this lab we have to execute the whoami command to determine the name of the current user.
As they said vulnerability is in product stock checker so I directly opened Burp Suite to intercept the request and here's what I get,

![image](https://github.com/Darry1968/Portswigger/assets/104063375/2cf6e913-f698-4c5e-94cf-7095eaa79dc1)

so as we know vulnerability lies in product stock checker, let's try to echo something and check the response. Here's the response:

![image](https://github.com/Darry1968/Portswigger/assets/104063375/825b7a31-fa82-4b61-b176-ef1692fdccf0)

I used that '#' symbol to comment the rest of the part,That makes easier to read the response. Now we know we can execute commands so to solve the lab just we have to replace that echo command to 'whoami'. And this will provide the name of current user.

Final command: productId=| whoami # &storeId=1
<br>
Which is = peter-VU0R4z
