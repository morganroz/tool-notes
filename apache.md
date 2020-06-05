# Apache Notes

I use Apache to host a local web server for creating and testing dynamic html sites.
[This guide](https://osxdaily.com/2012/09/02/start-apache-web-server-mac-os-x/) has been really helpful in learning how to set up a local server with Apache.

### Steps to set up the web server
Replace "USERNAME" with the appropriate user name.

1. Run the following command: 
```shell
sudo nano /etc/apache2/users/USERNAME.conf
```
2. Paste the following into the file:
```
<Directory "/Users/USERNAME/Sites/">
Options Indexes Multiviews
AllowOverride AuthConfig Limit
Order allow,deny
Allow from all
</Directory>
```
3. Start the server with the command:
```shell
sudo apachectl start
```  
Test that the server is running by navigating to http://localhost/. You should see a message that says "It Works!".

4. Stop the server with the command:
```shell
sudo apachectl stop
```  
To simply restart the server, run:
```shell
sudo apachectl restart
```

### I modified the aliases to allow myself to access the /Sites directory at the following address when Apache is running:
http://www.example.localhost/~morganrozman/

## Enabling Python CGI

1. Uncomment the following lines in /etc/apache2/httpd.conf
```
LoadModule cgi_module libexec/apache2/mod_cgi.so
Include /private/etc/apache2/extra/httpd-vhosts.conf
```

2. In /private/etc/apache2/extra/httpd-vhosts.conf, create a new container as:
```
<VirtualHost *:80>
    ServerAdmin morganleerozman@gmail.com
    DocumentRoot "/Users/morganrozman/Sites/covid-visualizations"
    ScriptAlias /cgi-bin "/Users/morganrozman/Sites/covid-visualizations"
    <Directory "/Users/morganrozman/Sites/covid-visualizations">
        AllowOverride All
        Require all granted
        AddHandler cgi-script .cgi .py
        Options Indexes MultiViews ExecCGI FollowSymlinks
    </Directory>
    ServerName covid-visualizations.localhost
    DirectoryIndex index.html
    ErrorLog "/private/var/log/apache2/covid-error_log"
    CustomLog "/private/var/log/apache2/covid-access_log" common
</VirtualHost>
```

3. Create the two log files via ```sudo touch /private/var/log/apache2/covid-error_log``` and ```sudo touch /private/var/log/apache2/covid-access_log```.

4. Add this line to /etc/hosts:
```
127.0.0.1    covid-visualizations.localhost
```

## Problems

#### Problem 1
localhost is working, but I cannot connect to localhost/~morganrozman/ ("The requested URL /~morganrozman/ was not found on this server.").

What I've tried:

1. Change /etc/apache2/extra/httpd-userdir.conf by uncommenting ```#Include /private/etc/apache2/users/*.conf```.

#### Problem 2
The changes in [Problem 1](problem-1--fixed) seem to have worked, but now I get the error "Forbidden You don't have permission to access /~morganrozman on this server".  

This worked, but not sure if it is technically "safe".

1. Change lines in /etc/apache2/httpd.conf to:
```
<Directory />
    AllowOverride all
    Require all granted
</Directory>
```
