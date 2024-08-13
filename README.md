<p align="center">
<img src="https://i.imgur.com/CtGfsq8.png" alt="osTicket logo"/>
</p>

<h1>Building Intuition for DNS</h1>
In this lab we will be experimenting with DNS. This lab will help us have a better understanding of DNS.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- DNS

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Active Directory Virtual Machine
- Client Machine joined to your domain

<h2>Lab Steps</h2>
<p>
</p>
<p>
First we will be inspecting DNS A-Records on the server A records are hostname to IP address mappings. We are going to create an A record on DC-1 for "mainframe" and have it point to DC-1's private IP address. If we try to ping mainframe without setting the DNS record it will not work. When we ping "mainframe" Client-1 is checking the DNS cache, checking its local host file and checking the DNS server. To create an A-record go to the AD->Tools->DNS->DC-1->Forward lookup zones->mydomain.com-> right click and create a new A record, title it mainframe. An A record is hostname to ip address mapping. If we go back to the client machine and ping mainframe we will get a reply. 
</p>
<br />

<p>

<img src="https://github.com/user-attachments/assets/1343036b-786c-44d3-b159-fd6db0f8ff24" height="80%" width="80%"  />

<img src=https://github.com/user-attachments/assets/6741d1b9-3a43-4987-871c-40621a830aec height="80%" width="80%"  />

<p>
Now we will change the record address of "mainframe" to 8.8.8.8 if we go back to the client machine it will still ping the old address even though we changed it. That is because we have to flush the DNS with the command ipconfig /flushdns. That will clear the DNS cache, when we attempt to ping mainframe again the address of the new record will show. 
</p>
<br />
<img src="https://github.com/user-attachments/assets/d0036f82-ff7e-43b2-a769-32e97e7fc874" height="80%" width="80%"  />
</p>
<img src="https://github.com/user-attachments/assets/a4997149-f02b-46fd-9d0b-be60effc16bb" height="80%" width="80%" />
</p>
<p>
Lastly we will configure a CNAME record that points the host "search" to "www.google.com" If we ping "search" ping will not be able to find the host. we have to go back into the DNS tool on DC-1 and create the CNAME record "search". Once we create the CNAME record is created and we ping "search" it will resolve to www.google.com.
</p>
<br />
<p>
<img src="https://github.com/user-attachments/assets/4e245f77-5a46-4bae-a1c6-e377087ebe85" height="80%" width="80%" />
"/>
</p>
<img src="https://github.com/user-attachments/assets/d1b69502-2eb2-4d32-b9b9-bc91f4e453ac" height="80%" width="80%" />
/>
<p>
