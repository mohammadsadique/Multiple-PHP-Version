
# Hi, I'm Sadique! 👋

  
# Multiple PHP version setup in Xampp server

Hey, you can easily run multiple PHP version in your system 
and only on specific drive ( single directory ex: C,D..drive ) 
in your Xampp server.

These technique helps you to run multiple PHP version in an 
instance. suppose your project run only on PHP 5.4 and you 
also have another project which is in PHP 7.4 and you want to
run both the project simultaneously. 

From the below process you can easly run both the project.

## Screenshots

![App Screenshot](https://raw.githubusercontent.com/mohammadsadique/Multiple-PHP-Version/main/images/php-versions.png?text=Multiple-PHP-Versions)

  
## Roadmap

- Change your virtual host

- Add PHP versions

  
## Change Your Virtual Host

To change host go to the link down below.
I installed in D folder so it look like these it might be 
different in your PC it depend on where Xampp is installed. 

```bash
  D:\xampp\apache\conf\extra\httpd-vhosts.conf
```

  Open in editor and remove ## from ##NameVirtualHost *:80
  we basically do uncomment these line

```bash
  NameVirtualHost *:80
```
  and finally add the code on the last.
  my bydefault PHP version is PHP 7.4 so it is come on top
  below default PHP version you can any numbers of PHP version.

  ```bash
    ## PHP 7.4
    <VirtualHost *:80>
        DocumentRoot "D:\xampp\htdocs\php74"
        ServerName localhost.php74
        <Directory "D:\xampp\htdocs\php74">
            Require all granted    
        </Directory>
        <FilesMatch "\.php$">
            SetHandler application/x-httpd-php-cgi
        </FilesMatch>
        ErrorLog "logs/dummy-host2.example.com-error.log"
        CustomLog "logs/dummy-host2.example.com-access.log" common
    </VirtualHost>
```

 ```bash
    ## PHP 5.6.40
    <VirtualHost *:80>
        DocumentRoot "D:\xampp\htdocs\php56"
        ServerName localhost.php56
        <Directory "D:\xampp\htdocs\php56">
            Require all granted    
        </Directory>
        <FilesMatch "\.php$">
            SetHandler application/x-httpd-php56-cgi
        </FilesMatch>
        ErrorLog "logs/dummy-host.example.com-error.log"
        CustomLog "logs/dummy-host.example.com-access.log" common
    </VirtualHost>
```

Now, install the software to add server name go to the link
and download it https://hostsfileeditor.com/
add your server name 'localhost.php56' and save 


![App Screenshot](https://raw.githubusercontent.com/mohammadsadique/Multiple-PHP-Version/main/images/host.PNG?text=Host-File-Editor)


## Add PHP Version

You have to add some code in httpd-xampp.conf file the location 
of these file is D:\xampp\apache\conf\extra my Xampp is store in
D drive. 

 ```bash
        #PHP 7.4
        ScriptAlias /php "D:/xampp/php"
        Action application/x-httpd-php-cgi /php/php-cgi.exe
        <Directory "D:/xampp/php">
            AllowOverride None
            Options None
            Require all denied
            <Files "php-cgi.exe">
                Require all granted
            </Files>
            SetEnv PHPRC "D:/xampp/php"
        </Directory>
```
 ```bash    
        #PHP 5.6.40
        ScriptAlias /php56 "D:/xampp/php56"
        Action application/x-httpd-php56-cgi /php56/php-cgi.exe
        <Directory "D:/xampp/php56">
            AllowOverride None
            Options None
            Require all denied
            <Files "php-cgi.exe">
                Require all granted
            </Files>
            SetEnv PHPRC "D:/xampp/php56"
        </Directory>
```

After adding the code now download all PHP version which you need 
from the link https://windows.php.net/downloads/releases/archives/
.

Let suppose you download php-7.4.20-nts-Win32-vc15-x64.zip file 
here you have to notice one thing go for nts.

The vc15 stand for
( Microsoft Visual C++ 2015 Redistributable package ) or simply 
search vc15 download.

Now extract the zip and make folder like php54 on Xampp folder
and paste the extract file inside php54 if you downloaded php 5.4 
version. 




![App Screenshot](https://raw.githubusercontent.com/mohammadsadique/Multiple-PHP-Version/main/images/xampp-folder.PNG?text=Xampp-Folder)

In the next step go inside htdocs folder and create same folder
name php54 here your all project belongs to these folder.
Remember these is php version 5.4 so these only support php 5.4 
projects.


![App Screenshot](https://raw.githubusercontent.com/mohammadsadique/Multiple-PHP-Version/main/images/inside-htdoc.PNG?text=Inside-htdocs)


Inside the php54 we saw the extracted file and folder we have to 
focus on php.ini-development and php ini production file just copy 
and past any one file and rename it as php.ini file.

![App Screenshot](https://raw.githubusercontent.com/mohammadsadique/Multiple-PHP-Version/main/images/extractfiles.PNG?text=Extract-Files)


Now open php.ini file in editor and search extension_dir = "ext"
and remove ; for un comment.

![App Screenshot](https://raw.githubusercontent.com/mohammadsadique/Multiple-PHP-Version/main/images/extension.png?text=Extension-dir)


Un comment the extension which you need. save the file and your 
are ready to go.

![App Screenshot](https://raw.githubusercontent.com/mohammadsadique/Multiple-PHP-Version/main/images/extension-need.PNG?text=Extension-need)

Now finally start the Xampp server and open the like we setup in 
these artical

http://localhost.php54

http://localhost.php80

.........
## Feedback

If you have any feedback, please reach out to us at

Email: [sadiquedeveloper@gmail.com](mailto:sadiquedeveloper@gmail.com)

WhatsApp Web [(91) 97705-99354](https://web.whatsapp.com/send?phone=9770599354)

WhatsApp Mobile [(91) 97705-99354](https://api.whatsapp.com/send?phone=9770599354)
