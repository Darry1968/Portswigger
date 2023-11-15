## Title: Username enumeration via different responses

url: [URL](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-different-responses)

***Description:***  This lab is vulnerable to username enumeration and password brute-force attacks. It has an account with a predictable username and password, which can be found in the following wordlists:<br>
[Candidate usernames](https://portswigger.net/web-security/authentication/auth-lab-usernames)<br>
[Candidate passwords](https://portswigger.net/web-security/authentication/auth-lab-passwords)<br>
To solve the lab, enumerate a valid username, brute-force this user's password, then access their account page.

***Solution:*** To solve this lab first open the burp suit intercept the login request and you will see the parameters that you have passed for username and password just like this..

![image](https://github.com/Darry1968/Portswigger/assets/104063375/bc9c8c36-5f6a-47bb-9197-ac5a95c33dfe)

Add position for username and choose attack type as sniper and paste the wordlist given by portswigger and start the attack. After attack is finished you can use Grep Extract to see the responses with the payloads and through that there will be one entry which contains response as `invalid password` just like this,

