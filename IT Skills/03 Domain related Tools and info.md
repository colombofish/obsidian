In general, we don't administer the network, policies, active directories etc. by logging into the server to manage them. Instead, we use our client machine by logging with Administrative Privilege. 
We can add 'AD' tool by adding as a feature in the Administrative Tools. 
`Make sure there is communication between the client server devices`

To allow RDP (Remote Desktop Connection), first need to allow it in the Server:
- Server Manager -> Local Server. Then Enable by clicking on Remote Management
- Click on Remote Desktop and add the domain user, whom you wanna give access. 
- Ping may not work if Firewall is enabled and set to not to accept ping requests. 

`This training may be good for live users, not to for Udemy, where we expect a systematic approach by listing out the modules and coaching one by one`. Many a times, the same AD installation is repeated, and the instructor tries to inform the students how better they are coaching by showing so many add on features than other academies etc. However, I have learned few things more, able to follow and get some practice using my own labs. That's why giving this 3 grade. Also, many recordings doesn't end smoothly, ends abruptly, and the next video starts. 

Whenever, we login, upgrade system or any other activities, they are logged in the system, which can be viewed through Event viewer.
Ex: if an application crashes, we can check relevant logs in 'Application logs', where you can check the details for reason codes and create a ticket and pass it to the relevant team.


`abdul\M..1!`
`Tiny Pulse`