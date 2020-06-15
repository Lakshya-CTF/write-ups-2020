## Deprecated



​	Performing an nmap scan using ```nmap -sV -sC -oA deprecated 34.66.134.126``` shows only two ports open, one of them being port 8000.

​	The /about page shows the versions used to develop the blogging platform.

![image-20200614211503452](/Users/chaitanyarahalkar/Downloads/Challenges/Deprecated/image-20200614211503452.png)

The blog is built using a very old version of Werkzeug. This version does not have a debugging PIN number asked in the debug console. A severely vulnerable version that affected the popular website Patreon. The job is now, to break the website and get to a debug console. In the search box, if a blog post that is not present in the database is queried, the application is unable to handle it, and it breaks showing a console prompt. 

![image-20200614211816431](/Users/chaitanyarahalkar/Downloads/Challenges/Deprecated/image-20200614211816431.png)

Now, simply use the Python console to gain command injection. The OS module or SYS module can be used to do so. 

![image-20200614212110639](/Users/chaitanyarahalkar/Downloads/Challenges/Deprecated/image-20200614212110639.png)

Now ssh using ```ssh lakshya@machine-ip``` with the user flag as the password.

Running a Linux enumeration script like [LinPEAS](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS) or [LinEnum](https://github.com/rebootuser/LinEnum/) shows that the lakshya user can run the command ```git pull``` as root.

