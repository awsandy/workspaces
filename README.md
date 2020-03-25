# workspaces
AWS Workspaces information

## Using the PCioP client with USB devices

* The USB passthrough only works with the Windows software PCioP client.
* Also Within the Workspace Windows instance itself a specific Teradici Group Policy setting must be made

Download the PCioP client:

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

> Open gpedit.msc and press Enter.
> In the left pane, navigate to
> Local Computer Policy
>> Computer Configuration
>> Administrative Templates
>> Classic Administrative Templates (ADM)
>> PCoIP Session Variables
>> Overridable Administrator Defaults

Double-click Configure PCoIP USB allowed and unallowed device rules. The variable editor appears.

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


## References

Reference for adding the Admin Template (on the AWS Session)

http://www.teradici.com/web-help/ter1505005/2.8/Content/_common_topics/Configuration/Windows/importing_the_admin_template_file.htm

GPO Setting (on the AWS Session)
http://www.teradici.com/web-help/ter1505005/2.8/default.htm#_common_topics/Features/Windows/enable_usb_redirect.htm%3FTocPath%3DConfiguring%2520the%2520PCoIP%2520Graphics%2520Agent%7C_____4
