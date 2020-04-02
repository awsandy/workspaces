# Handy AWS WorkSpaces Information


## Using the PCoIP client with USB devices

* The USB passthrough only works with the Windows software PCoIP client.
* Also within the WorkSpace Windows instance itself a specific Teradici Group Policy setting must be made

Download the PCoIP client:

https://docs.teradici.com/find/product/software-and-mobile-clients/2019.05/software-client-for-windows/20.01.1

### Enabling USB part 1:

* Open the Local GPO Editor: gpedit.msc 
* Navigate to the Local Computer Policy > Computer Configuration > Administrative Templates directory.
* Right-click the Administrative Templates folder and select Add/Remove Templates from the context menu.
* Click Add, and navigate to thefollowing directory:
```
C:\Program Files (x86)\Teradici\PCoIP Agent\configuration
```
* Select pcoip.adm, and click Open and then Close.

The template file is imported.


### Enabling USB part 2:

* Open gpedit.msc and press Enter.
* In the left pane, navigate to
  * Local Computer Policy
  - Computer Configuration
  - Administrative Templates
  - Classic Administrative Templates (ADM)
  - PCoIP Session Variables
  - Overridable Administrator Defaults

* Double-click Configure PCoIP USB allowed and unallowed device rules. The variable editor appears.

[//]: # (Pull in image this way to control size in markdown)
<img width="320" height="250" src="https://github.com/awsandy/workspaces/raw/master/img/configure-usb-devices.png" />


Read the instructions in the help pane for detailed information about rule formats and restrictions.
Specify your USB allowed and unallowed rules in the Options pane and click OK.

### :star: Tip: Allow all USB devices
To globally allow all USB devices, add the following authorization rule:
```
23XXXXXX
```

Close the Local Group Policy editor.
The change will be effective on the next PCoIP connection to the host workstation.

## Adjusting the hostname / computer name

At the time of writing (April 2020) there is a quirk with the Teradici PCoIP client that means it will fail to connect to an AWS WorkSpace if that WorkSpace's hostname (Linux) or computer name (Windows) begins with a number.

### Workaround

Connect to the workspace using the AWS WorkSpaces client and change the hostname or computer name so it begins with a letter.


For Windows 10, you can do this via Settings, System, About & Rename this PC:

[//]: # (Pull in image this way to control size in markdown)
<img width="320" height="340" src="https://github.com/awsandy/workspaces/raw/master/img/win10-cn.png" />

## References

### Teradici

Reference for adding the Admin Template (on the AWS Session):
http://www.teradici.com/web-help/ter1505005/2.8/Content/_common_topics/Configuration/Windows/importing_the_admin_template_file.htm

GPO Setting (on the AWS Session):
http://www.teradici.com/web-help/ter1505005/2.8/default.htm#_common_topics/Features/Windows/enable_usb_redirect.htm%3FTocPath%3DConfiguring%2520the%2520PCoIP%2520Graphics%2520Agent%7C_____4

### WorkSpaces

Proof of Concept:
https://d1.awsstatic.com/whitepapers/workspaces-poc-guide.pdf

Best practices:
https://d0.awsstatic.com/whitepapers/workspaces/Best_Practices_for_Deploying_Amazon_WorkSpaces.pdf

Ingtegrating Microsoft Azure MFA Server with Amazon WorkSpaces: 
https://aws.amazon.com/blogs/desktop-and-application-streaming/integrating-microsoft-azure-mfa-server-with-amazon-workspaces/
