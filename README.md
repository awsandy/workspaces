# workspaces
AWS Workspaces information

## Using the PCioP client with USB devices

* The USB passthrough only works with the Windows software PCioP client.
* Also Within the Workspace Windows instance itself a specific Teradici Group Policy setting must be made

Download the PCioP client:

https://docs.teradici.com/find/product/software-and-mobile-clients/2019.05/software-client-for-windows/20.01.1

To Enable USB:

* Open the Local GPO Editor: gpedit.msc 
* Navigate to the Local Computer Policy > Computer Configuration > Administrative Templates directory.
* Right-click the Administrative Templates folder and select Add/Remove Templates from the context menu.
* Click Add, and navigate to thefollowing directory:
```
C:\Program Files (x86)\Teradici\PCoIP Agent\configuration
```
* Select pcoip.adm, and click Open and then Close.

The template file is imported.





## References

Reference for adding the Admin Template (on the AWS Session)

http://www.teradici.com/web-help/ter1505005/2.8/Content/_common_topics/Configuration/Windows/importing_the_admin_template_file.htm

GPO Setting (on the AWS Session)
http://www.teradici.com/web-help/ter1505005/2.8/default.htm#_common_topics/Features/Windows/enable_usb_redirect.htm%3FTocPath%3DConfiguring%2520the%2520PCoIP%2520Graphics%2520Agent%7C_____4
