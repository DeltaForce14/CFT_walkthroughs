**CTF - TryHackMe - Learn Linux Room**

Objective: find content of a file /root/root.txt

STEP1: check if any of known users have sudo privileges
su -l 

None of the known users had sudo privileges. 

STEP2: check what other existing user we have 
View /etc/passwd 

We found that we had two other users noot and nootnoot 

STEP3: as we found passwords for the other users hidden in different files we can assume that 
password for either user noot or nootnoot is hiding within files of one of existing users. 

We run command for every user: 
find / -user <user name> -type f 2>>/dev/null

We find an interesting file hiding within shiba2 files:
/var/log/test1234

STEP 4: We login as shiba2 if we aren’t already logged and open the file:
cat /var/log/test1234

We find message:
nootnoot:notsofast

We login as nootnoot

STEP5: We check privileges of nootnoot and we find out that we have sudo privileges! 

I tried to open the file with command but was getting error: 
sudo cat /root/root.txt 

So checked became a root user type with command:
sudo -i 

After that I was able to open the file and get the flag! 

HAPPY HUNTING!
