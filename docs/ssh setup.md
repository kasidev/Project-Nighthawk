# SSH password free login between windows and Raspberry

1. on your admin/dev machine create a new keypair 
~~~
ssh-keygen -t ed25519
~~~

2. Setup Options
enter <file name>
for testing: leave passphrase empty
for production set strong passprhrase

3. Display the newly created public key and adjust the config

~~~
Get-Content $env:USERPROFILE\.ssh\<file name>.pub

notepad C:\Users\<USERNAME>\.ssh\config
~~~

for linux
~~~
nano ~/.ssh/config
chmod 600 ~/.ssh/config
~~~

add the following config

~~~
Host <HOSTNAME>
    HostName <HOSTNAME>
    User <USERNAME>
    IdentityFile C:\Users\<USERNAME>\.ssh\<YOUR_KEY_NAME>
    IdentitiesOnly yes
~~~

4. login to the raspi via ssh (with password)
~~~
ssh <username>@<hostname>
~~~
    

    1. create the \.ssh directory
    ~~~
    mkdir -p ~/.ssh
    ~~~

    2. Allow read, write, and execute permission for the owner, but prohibit read, write, and execute permission for everyone else
    ~~~
    chmod 700 ~/.ssh
    ~~~

    3. open the authorized keys file and add the new key as one line
    ~~~
    nano ~/.ssh/authorized_keys

    chmod 600 /.ssh/authorized_keys

    cat /.ssh/authorized_keys
    ~~~

5. edit the login text
~~~
sudo nano /etc/motd
~~~