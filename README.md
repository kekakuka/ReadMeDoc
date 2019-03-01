#         Set Up SSH Keys on CentOS


<br>
Your can read from DigitalOcean [How To Set Up SSH Keys on CentOS 7].

# Step 1 — Create the RSA Key Pair 

The first step is to create a key pair on your computer:
<blockquote>
<div style="background-color:black;color:white">$ ssh-keygen</div>
</blockquote>
After entering the command, you should see the following prompt:
<blockquote>
<div style="background-color:black;color:white">Output<br/>
Generating public/private rsa key pair.<br/>
Enter file in which to save the key (/Users/<span style="color:yellow">your_username</span>/.ssh/id_rsa):</div>
</blockquote>
If you had previously generated an SSH key pair, you may see the following prompt:

<blockquote>
<div style="background-color:black;color:white">Output<br/>
/Users/<span style="color:yellow">your_username</span>/.ssh/id_rsa already exists.<br/>
Overwrite (y/n)?</div>
</blockquote>
If you choose to overwrite the key on disk, you will not be able to use the previous key anymore. Be very careful when selecting yes, as this is a destructive process that<span style="color:red"> cannot be reversed</span>.<br/>

You can  use you own ssh-key to login CentOS Server. Please select no and skip to  <span style="font-weight:800;font-size:19px;">Step 2</span>.

You should then see the following prompt:
<blockquote>
<div style="background-color:black;color:white">
Output<br/>
Enter passphrase (empty for no passphrase):</div>
</blockquote>
Here you optionally may enter a secure passphrase. A passphrase adds an additional layer of security to prevent unauthorized users from logging in.

You now have a public and private key that you can use to authenticate. The next step is to place the public key on your server so that you can use SSH-key-based authentication to log in.

#Step 2 — Copy the Public Key to CentOS Server

For this method to work, you must already have password-based SSH access to your server.

The syntax is:
<blockquote>
<div style="background-color:black;color:white">
$ ssh-copy-id <span style="color:yellow">server_username</span>@<span style="color:yellow">remote_host_ip</span></div>
</blockquote>
The "ssh-copy-id" does not work in Windows. You can GIT BASH in your "C:\Users\your_username".


You may see the following message:
<blockquote>
<div style="background-color:black;color:white">
Output<br>
The authenticity of host <span style="color:yellow">'remote_host_ip'</span> can't be established.<br>
ECDSA key fingerprint is fd:fd:d4:f9:77:fe:73:84:e1:55:00:ad:d6:6d:22:fe.<br>
Are you sure you want to continue connecting (yes/no)?<span style="color:yellow"> yes</span></div>
</blockquote>
This will happen the first time you connect to a new host. Type "yes" and press ENTER to continue.

Next, the utility will scan your local account for the id_rsa.pub key that we created earlier. When it finds the key, it will prompt you for the password of the remote user's account:
<blockquote><div style="background-color:black;color:white">
Output<br>
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed<br>
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys<br>
<span style="color:yellow">server_username</span>@<span203.0.113.1's</span> password:</div>
</blockquote>
Type in the password (your typing will not be displayed for security purposes) and press ENTER. The utility will connect to the account on the remote host using the password you provided. It will then copy the contents of your ~/.ssh/id_rsa.pub key into a file in the remote account's home ~/.ssh directory called authorized_keys.

You should see the following output:
<blockquote>
<div style="background-color:black;color:white">
Output<br/>
Number of key(s) added: 1</div>
</blockquote>
Now try logging into the machine, with: 
<blockquote>
<div style="background-color:black;color:white">  $ ssh <span style="color:yellow">server_username</span>@<span style="color:yellow">remote_host_ip</span></div>
</blockquote>
and check to make sure that only the key(s) you wanted were added.
At this point, your id_rsa.pub key has been uploaded to the remote account. 



[How To Set Up SSH Keys on CentOS 7]: https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-centos7 "How To Set Up SSH Keys on CentOS 7"
