# Credential Hunting (HackTheBox)

## Goal
Inspect the target and extract the user Will’s password from browser-stored credentials.


## Tools
- ssh
- python ftp server
- firefox_decrypt



### Process
Connecting to the target using ```ssh```. 

![alt text](screenshots/image.png)

While inspecting the current working directoty I noticed that there is a hidden file ```.mozilla```.

![alt text](screenshots/image-1.png)

I know that credentials for a web page in the Firefox browser are encrypted and stored in ```logins.json``` on the system.

![alt text](screenshots/image-2.png)

Next, I examined the contents of the ```logins.json``` file within that profile. This file contained the stored usernames and passwords for websites, but as shown in the output, the credentials are encrypted using Firefox's built-in mechanism.

![alt text](screenshots/image-3.png)


```firefox_decrypt``` tool is a Python utility designed to recover passwords from Firefox's profile files by using the database and keys found in the profile directory.

I found this tool on my ```attack host``` and prepared ```ftp server``` to transfer the ```firefox_decrypt``` to my ```target machine```.

![alt text](screenshots/image-4.png)

![alt text](screenshots/image-5.png)

![alt text](screenshots/image-6.png)

Finally I executed the decryption tool on the ```target machine``` and got a user's password.

![alt text](screenshots/image-7.png)