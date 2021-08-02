Install a stand-alone SQL Server 2019 Enterprise Server
--

In this article I will install both SQL Server Database Engine and SQL Server Management Studio on Windows 10 Enterprise.

Note: In Vmware create 4 Disks and add Folders labeled:
- E:\MSSQL
- F:\SQLLOGS
- G:\SQLBACUP
- H:\SQLTEMPDB

![disks](/pic/1a.png)





Install SQL Server Database Engine

Open the Installation media, and run setup.exe

![install](/pic/1.png)


Click on “New SQL Server stand-alone installation or add features to an existing installation” We have the option here to install new a secure server standalone installation or add features to an existing installation. So if you already have a secure server installed and you want to add features to the existing installation, you can still use this link. But I am installing a single instance of a secure server, so I'm going to click on that and that will launch the installation wizard.

![stand](/pic/2.png)

Enter your product key and press Next

![key](/pic/3.png)

Check the checkbox to accept the license terms and privacy statement, press Next

![accept](/pic/4.png)

Now here where we have check for updates, it's recommend, however if your installing sql server for a company, they probably have there own patching process so see what the update procedure is. I'm just going to click next.

 ![update](/pic/4a.png)


So click on Next and it will do some basic checks. It will install some set of files. So I just wait for it to finish on the step of the installation here.


Have had some checks here, says I've passed three, failed zero. You can see here that I have a warning on. You can click on the warning and see what that says.. This is not serious. So I'm going to click next to progress to the next stage of the installation.

![warn](/pic/5.png)


The next step is you are provided with the feature selection so that you can select the component you want. At minimum I always install

- Database Engine Services
- Full Text
- Client Tools Connectivity
- Intergrated Services
- Client Tools Backwards -Compatibility

In my instance root directory, I'm going to selct E:\MSSQL



After you select your features, press Next.


![select](/pic/6.png)


The benefit of the default instance is that you connect just by specifying the server name, whereas a named instance will require an instance name as well (MYSERVER\INSTANCE_NAME). If you’re only going to install one version of SQL Server on this machine, go with a default. If you’re planning on multiple instances on this machine, it’s up to you whether you want one named and one default, or both named. NEXT

![default](/pic/7.png)


In server configuration set both the SQL Server Agent, SQL Server Database Engine,SQL Server Intergration, and SQL Server browser to Automatic, and select Grant perform volume maintence task, then press Next

![auto](/pic/8.png)

We are now on the database engine configuration I will go though the Tabs on the top of the Database Engine Configuration
page. The first tab, Server Configuration I am setting the server to Mixed Mode, so I can use both Windows accounts and SQL Accounts, I am also adding my current user as an administrator.

![mode](/pic/9.png)

On the second tab, Data Directories I'm setting my data root to E:\MSSQL, and my backup directory to G:\SQLBACKUPS

![directoies](/pic/10.png)

On the third tab, TempDB, I am setting this to H:\SQLTEMPDB


![temp](/pic/11.png)

On the fourth tab, MaxDOP, I set the MaxDOP to 2, so it will not eat up all my resources. If you will be using SharePoint this needs to be set to 1 to work correctly.

![max](/pic/12.png)

On the fifth tab, Memory, I set the memory to Recommended and 4096 Max, this means SQL Server cannot use more than 4GB of RAM. 1GB is the minimum SQL Server needs.

![mem](/pic/13.png)


On the sixth tab, FILESTREAM, I left this disabled.
Press Next


Verify all the components you want to install are there, Press Install

![verify](/pic/14.png)

Install SQL Server Management Tools (SQL Server Management Studio)
--
Press “Install SQL Server Management Tools”

![tools](/pic/16.png)

It will bring you to this link. [Download the latest version](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?redirectedfrom=MSDN&view=sql-server-ver15)

Scroll down the page and select Download SQL Server Management Studio (SSMS)

![download](/pic/17.png)

Go to properties of the exe and unblock the file. Then run the executable as administrator.


![unblock](/pic/18.png)


I'm going to leave the default configuration on my C drive.

![install](/pic/19.png)

And then select install.

After install Press Restart to restart your machine

![restart](/pic/20.png)


You should now see SQL Server Management Studio 18 in your start menu and you should be able to connect to the instance that you just created.

![start men](/pic/21.png)

When it starts up just press connect

![start](/pic/22.png)

And there we go Im successfully connected to my SQL server instances.

![sql](/pic/23.png)


Now right click on SQL Server and select properties.

![select](/pic/24.png)


Now if you want, you can go thru and check all the configuration settings that we set up during the SQL server installation.

![conf](/pic/25.png)


Well that's all for this tutorial.
