<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>List of Prerequisites</h2>

- <b>PHP manager for IIS</b> - ensures PHP is correctly configured to run IIS
- <b>Rewrite module </b> - facilitates URL rewriting and redirect users to URLs
- <b>VC_redist.x86</b> (redistributable) - osTicket relies on libraries that are part of Microsoft Visual C++ and ensures the program runs smoothly
- <b>MySQL</b> - for storing data into databases
- <b>HeidiSQL</b> - interface for accessing MySQL 


<h2>Installation Steps</h2>
<p>
After setting up the Windows 10 VM in Azure, log in with your credentials. Open Microsoft Edge, download osTicket-Installation-Files.zip, and extract the files. You should then see the contents.

</p>
<br />

<p>
<img src="https://i.imgur.com/29gqX2m.png" height="80%" width="80%" alt="extracted osticket zip file"/>
</p>


<p>
Next, enable Internet Information Services (IIS). Go to Uninstall a Program, select Turn Windows features on or off, and check the box for Internet Information Services. Then, under World Wide Web Services -> Application Development Features, enable CGI.
</p>
<br />

<p>
<img src="https://i.imgur.com/CdojXsp.png" height="80%" width="80%" alt="enable IIS and CGI"/>
</p>
<br/>
<p>
Now nstall the PHP manager for IIS. Open on the file and click OK to all the default selections. 
</p>
<img src="https://i.imgur.com/Uh4Zwlj.png" height="80%" width="80%" alt="install php manager and rewrite"/>

<br />

<p>
Next we create a directory in C:\ called PHP, basically C:\PHP. Click on the folder at the bottom the Taskbar or search for File Explorer. This is so that we can extract osTicket to work with PHP.
</p>
<p>
  <img src="https://i.imgur.com/BCMLUId.png" height="80%" width="80%" alt="extract php to c php"/>
</p>
<br/>

<p>
Next install the redistributable and accept all defaults. Then install MySQL, select Standard Configuration and then enter root and root as the username and password. This is just for simplicity and you'd likely use a stronger password in real life.
  
</p>
<p>
  <img src="https://i.imgur.com/dbDt0um.png" height="50%" width="50%" alt="install redistr and mysql"/>
</p>
<br/>

<p>
Now open Internet Information Services, type IIS in the search bar and then Run as administrator. Click on PHP manager then register new PHP version. Select C:\PHP\php-cgi.exe
  
</p>
<p>
  <img src="https://i.imgur.com/3twI19f.png" height="80%" width="80%" alt="configure PHP new version in PHP manager"/>
</p>
<br/>

<p>
Reload IIS by clicking stop then start on the right hand side. This will help load the new PHP version.
</p>
<p>
  <img src="https://i.imgur.com/iO7K6aO.png" height="30%" width="30%" alt="reload IIS"/>
</p>
<br/>

<p>
Extract the osticket zipped folder and move the extracted upload folder into C:\inetpub\wwwwroot, then rename upload to osTicket (it must be exact).
  
</p>
<p>
  <img src="https://i.imgur.com/xJw174Y.png" height="80%" width="80%" alt="extract osticket zipped folder and move to wwwroot"/>
</p>
<br/>

<p>
Reload IIS again. On the left side pane, go to Sites, click the down arrow until you reach osTicket and then click on Browse in the right side pane, then you should get this.
</p>
<p>
  <img src="https://i.imgur.com/4ahLEvm.png" height="80%" width="80%" alt="osticket landing page"/>
</p>
<br/>
<p>
Now, enable some extensions. In the osTicket folder, select PHP Manager in the middle pane. Click Enable or disable an extension, and enable php_imap.dll, php_intl.dll, and php_opcache.dll. Then refresh the osTicket webpage to see the updates.
<p>
  <img src="https://i.imgur.com/87i9Gxs.png" height="80%" width="80%" alt="updated osticket landing page"/>
</p>
<br/>
<p>
Now rename C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php to C:\inetpub\wwwroot\osTicket\include\ost-config.php. Then we need to change permissions for this file. Right click on this and then Properties -> Security tab -> Advanced -> Disable inheritance (remove option) -> Add -> Select a principal -> Type everyone in the box -> Check names -> OK. Make sure you click on Full control as well.
</p>
<p>
  <img src="https://i.imgur.com/wABTm3C.png" height="80%" width="80%" alt="ost config permissions"/>
</p>
<br/>
<p>
In the osTicket browser window, click Continue and enter your chosen login and password for the helpdesk system. Ensure the MySQL database name is osTicket, with both username and password as root.

Before proceeding, go to the extracted folder and install HeidiSQL. Use the default settings, then create a new session and log in to the SQL database with root/root. Right-click on Unnamed, select Create new -> Database, and name it exactly osTicket.
</p>
<p>
  <img src="https://i.imgur.com/Lfw0PXJ.png" height="80%" width="80%" alt="heidisql"/>
  <img src="https://i.imgur.com/pWKEjjz.png" height="80%" width="80%" alt="create new database in heidisql"/>
</p>
In the browser, click Install Now to complete the osTicket installation. You should then see a confirmation page with links to log into osTicket as a general user (http://localhost/osTicket) or as staff (http://localhost/osTicket/scp).
<br/>
<p>
   <img src="https://i.imgur.com/CBKO7Qs.png" height="80%" width="80%" alt="osticket installed"/>
</p>
