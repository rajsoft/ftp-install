# Ftp Server Install on the Linux

Follow the following step for install the FTP SERVER



#Step 1: Install vsftpd

apt-get update

Then let’s install vsftpd and any required packages:

apt-get -y install vsftpd

#Step 2: Configure vsftpd

vim /etc/vsftpd.conf

Disallow anonymous, unidentified users to access files via FTP; change the anonymous_enable setting to NO:

anonymous_enable=NO

Allow local uses to login by changing the local_enable setting to YES:

local_enable=YES

If you want local user to be able to write to a directory, then change the write_enable setting to YES:

write_enable=YES

Local users will be ‘chroot jailed’ and they will be denied access to any other part of the server; change the chroot_local_user setting to YES:

chroot_local_user=YES

Add this command

allow_writeable_chroot=YES

Exit and save the file with the command :wq .

#Restart Service

service vsftpd restart

Create the FTP users

Create  directory for ftp user access

sudo mkdir /home/ftp

Add  /bin/itfshell line  in last line of  /etc/shells file


#Create User Group

sudo groupadd ftp-users

#Create User 

sudo useradd --home /home/ftp --group ftp-users --shell /bin/itfshell ftpadmin

Set Password of ftp user

sudo passwd ftpadmin

Change ownership of folder

sudo chown -R ftpadmin /home/ftp

sudo chmod 755 /home/ftp


Conguratulation you have created the succesfully ftp user,

Host Name : your ip 
user name : ftp-users 
Password : given by you
