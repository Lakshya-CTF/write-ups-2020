## Tea Breaker



Doing an NMap scan on the box with ```nmap -sV -sC -oA teabreaker machine-ip``` shows three ports open. One of them is 3000. This port has a service [Gitea](https://gitea.io) hosted on it. Looking at the explore tab, shows a repository by John called mytty. 

Cloning this repository with ```git clone url```, we check the git commit history. 

![image-20200615094246548](https://github.com/Lakshya-CTF/write-ups-2020/blob/master/Tea%20Breaker/image-20200615094246548.png)

A suspicious commit comment shows that some credentials were exposed in the previous commits that were hidden via environment variables in the master branch's head commit. Checking out the previous commit (With cooment - "Add runner code") with ```git checkout d6bcd82d59a3a21221e057c2041f361fd35e1871``` we view the ```grab_creds.py``` file.

![image-20200615094557284](https://github.com/Lakshya-CTF/write-ups-2020/blob/master/Tea%20Breaker/image-20200615094557284.png)

We saw a service running on port 8000, but it required authentication. Trying these credentials on that page , we get in. A direct command prompt is visible. We read the user flag with ```cat flag.txt```

![image-20200615094936146](https://github.com/Lakshya-CTF/write-ups-2020/blob/master/Tea%20Breaker/image-20200615094936146.png)



For the root flag, we perform Linux enumeration using [Linenum](https://github.com/rebootuser/LinEnum). This shows that the SUID bit on Curl is set.

![image-20200615095401302](https://github.com/Lakshya-CTF/write-ups-2020/blob/master/Tea%20Breaker/image-20200615095401302.png)

Checking on (GTFOBins)[https://gtfobins.github.io], we see a techinque to read priviledged content on the system using the file protocol. We use the command ```curl file:///root/flag.txt -o flag.txt``` to read the root flag.

![image-20200615095619928](https://github.com/Lakshya-CTF/write-ups-2020/blob/master/Tea%20Breaker/image-20200615095619928.png)
