Professional community network `Spiceworks`

Tips: Get to know your ISP at work, so when a network is down at least we can google and find out if the issue is global or affecting only us. 

Job Search (include): 'Helpdesk Technician', 'Help Desk Specialis', 'IT Support Specialist', 'Dessktop Support Specialist - Level 1'. So, basically the instructer meant to say that title doesn't mean much, but the content and the requirement looked means. 
So, when you write your CV, provide your skills such as Active Directory, etc. so the the employer knows what you know. 

Domain means talking about 'Active Directory' in this course. 

After installing the Server OS, you need to add AD and other required services into it. 

Home Lab: 
1. Windows Server 2022 \[AD DS Role], promote to DC
2. Windows 11 Joins the DC

Downloads: 
1. Virtual Box (oracle's from virtualbox.org)
2. Download Windows 11 iso evaluation
3. Select Windows 11 Enterprise (not LTSC)

Installations:
A. Create a new VM.
1. set the .iso downloaded. 
2. before starting the server set the network to use Bridge Adapter instead of NAT. This will get the IP from the parent network, which is my laptop. 
3. Start the the VM
Host Key is defined as `Right Ctrl`. Toggle Full Screen with 'Host + F' key
4. Select the Server 2022 Data Center (Desktop Experience) option
5. password for ('Ma...1')
6. Once started, check the IP address, if IP is rendered through local router, then change the name of the server via System
7. Shutdown the server and install the Win11 client from the *.iso (if you see a black screen, then reset the vm, that should restart it)
8. Once the client windows installed, select the 'Domain' join option instead of sign-in to the cloud or using your own MS account (admin/M..1). 
9. Next, we need to turn the MS Server into Domain Controller to manage the clients (win11 in this example)
10. In Windows server Manager, click on the Add Roles and Feature Services, next Add 'Active Directory' services, then install it. 
11. Once installed, go back to the Roles and Features, you will find 'Promote this server to a domain controller' option.
12. Select 'Add a new forest' option if you want to create a new DC, give it a name (jsslab.local in the lab). Give a password, could be the same for the server admin login or different. 
13. Next, then do not select 'Create DNS delegation', select next NetBIOS name will be selected auto.
Once AD (DC) is installed, we can use Tools such as 'Active Directory Computers and Users' or other Tools from the Server Manager. (helpdesk/M..1, then promote as admin). If Domain Admins, then it becomes Super Admin for this env.
14. Next join the win11 to the DC. However, before joining a PC to DC, make sure the network configs are matching, ping to the machines to verify etc. Also, check if you have renamed the win11 as per the policy.(System -> Domain or Workgroup)
15. One more optional this is to setup the DNS to talk to the DC by adding the DC's IP address as the DNS setting in the win11 client network settings. 
Workgroup are good for standalone machines, where the users are not managed centrally (no central dB), or in a very small business. 