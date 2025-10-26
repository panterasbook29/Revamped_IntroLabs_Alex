![image](https://github.com/user-attachments/assets/068fae26-6e8f-402f-ad69-63a4e6a1f59e)


# Password Cracking

In this lab we will be getting started with the fundamentals of password cracking.  We will be using **Hashcat** to do this.

To start, disable **Defender** and open **PowerShell** to run the following command:

![](attachments/OpeningPowershell.png)

<pre>Set-MpPreference -DisableRealtimeMonitoring $true</pre>

This will disable **Defender** for this session.

If you get angry red errors, that is Ok, it means **Defender** is not running.

We need to launch a **Kali** terminal. Click the **Kali** icon in the taskbar.

![](attachments/TaskbarKaliIcon.png)

When the terminal opens, we need to gain root access by running the following:

<pre>sudo su -</pre>

Now, let's delete any old leftover pot files

<pre> rm /root/.local/share/hashcat/hashcat.potfile</pre>

If you get an error that the file does not exist, that is fine.  It just means the file does not exist.  Carry on.

We need to navigate to the appropriate directory. Run the following:

<pre>cd /opt/Password_Cracking</pre>

Lets begin by attempting to crack some **MD5 hashes**. 

Run the following command:

<pre>hashcat -a 0 -m 0 -r /usr/share/hashcat/rules/Incisive-leetspeak.rule MD5.txt password.lst</pre>

The result will look like this:

![](attachments/md5run.png)

Running this command will not show us the cracked hashes. As seen above, in order to see cracked hashes, we need to run our command again and add the **--show** option onto the end.

After running the command again with the **--show** option, you should see something like this:

![](attachments/md5hashes.png)

Lets crack some NT hashes.  These are the hashes that almost all modern **Windows** systems store these days.  Older systems may store **LANMAN**, but that is very rare.

Lets run the following command:

<pre>hashcat -a 0 -m 1000 -r/usr/share/hashcat/rules/Incisive-leetspeak.rule sam.txt password.lst</pre>

When this command is complete, it should look like this:

![](attachments/nthashrun.png)

We will not see the cracked hashes unless we append **--show** onto the end of the command. Lets do that.  Run it again to see the cracked hashes:

![](attachments/ntcracked.png)


***                                                                 
<b><i>Continuing the course? </br>[Next Lab](/IntroClassFiles/Tools/IntroClass/PasswordSpray/PasswordSpray.md)</i></b>

<b><i>Want to go back? </br>[Previous Lab](/IntroClassFiles/Tools/IntroClass/Nmap/Nmap.md)</i></b>

<b><i>Looking for a different lab? </br>[Lab Directory](/IntroClassFiles/navigation.md)</i></b>

***Finished with the Labs?***

Please be sure to destroy the lab environment!

[Click here for instructions on how to destroy the Lab Environment](/IntroClassFiles/Tools/IntroClass/LabDestruction/labdestruction.md)

---


