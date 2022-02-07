# FTP Config for ubuntu

**Install FTP** ➡️ *apt install vsftpd*

**Add a user** ✔️

*adduser client*

**Config your FTP**

*nano /etc/vsftpd.conf*

*Uncomment write_enable=YES*


**Now there are 3 option which you can choose ( Insecure, Explicit and Implicit ).**

**Explicit** ⬇️

**Add your certs**

rsa_cert_file=/etc/ssl/certs/yourcrt.crt

rsa_private_key_file=/etc/ssl/private/yourkey.key

ssl_enable=YES

Now add these lines ⬇️

pasv_enable=YES

pasv_min_port=10000 (The port you add here you have to enable it on the firewall along with the others)

pasv_max_port=10100

allow_anon_ssl=NO

force_local_data_ssl=YES

force_local_logins_ssl=YES

ssl_tlsv1=YES

ssl_sslv2=NO

ssl_sslv3=NO

require_ssl_reuse=NO

ssl_ciphers=HIGH

**For implicit just add this with the config above** ⬇️

implicit_ssl=YES

listen_port=990

**And for insecure (without certs)**

Change ssl_enable=YES

to ⬇️

ssl_enable=NO

**And add this**

pasv_enable=YES

pasv_min_port=10000

pasv_max_port=10100

systemctl restart vsftpd.service

**And your done!**
