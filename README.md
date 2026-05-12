I am currently setting up my Windows Server to have a backup. In a real enterprise we set up backups constantly just in case an issue with the system or even the files arises. 
When you have constant backups with your server you are able to restore from the last best position your system was in. 

Tools: 
Windows 2022 Server
Powershell
CMD
Remote Manager

1. Install Backup Feature in Powershell
   
<img width="581" height="433" alt="image" src="https://github.com/user-attachments/assets/4e680cf7-7ca4-42ce-8dfc-6f925d0e1fe4" />

3. Verify that the install was successful
   
   <img width="524" height="384" alt="image" src="https://github.com/user-attachments/assets/654ade00-8e15-46fe-9d35-24263afabcb5" />

5. Add the Second Virtual Disk. ( This disk was added through my VM through the settings and now I am configuring it for my Server)
   
   <img width="515" height="385" alt="image" src="https://github.com/user-attachments/assets/6cf8bf10-b73d-4183-867a-9fed4922e823" />
   
In the screenshot above I intialized the Disk and created a partition and assigned a drive letter.

It's important to intialize the disk becuase once it's added to the server it shows up as a raw hardware. When we set up these steps it 
allows the disk to actually be used by the Operating System. 


<img width="508" height="305" alt="image" src="https://github.com/user-attachments/assets/d131765b-b788-4a80-a029-5b5ba2de4936" />
Lastly we are formating the volume becuase without it windows cannot properly store and retrieve files.

4. Configure Scheduled Backup
   
   <img width="516" height="385" alt="image" src="https://github.com/user-attachments/assets/ddcb0b61-7a74-4fc1-a279-d50db97f0acc" />

-addtarget:E:  
Backup Destination

-allCritical   
Critical System Volumes

-schedule:23:00 
Daily at 11:00pm

-quiet          
No confirmation prompts

5. Verify the backup
   
   <img width="435" height="130" alt="image" src="https://github.com/user-attachments/assets/c46b6146-873c-412e-8317-1ed9f2ff2aac" />

7. Start the Manual Backup Test
   
   <img width="510" height="341" alt="image" src="https://github.com/user-attachments/assets/2ea4fc25-682d-4a9b-ac0b-3ae77e55daca" />

9. Recovery File Test
    
   <img width="498" height="187" alt="image" src="https://github.com/user-attachments/assets/2b9e9ba3-e209-4b62-8935-945cecc43766" />
In the screenshot above I created a test file and added it to a test folder this is going to allow me to see if my backup works.

11. Add content to the file
    
   <img width="496" height="190" alt="image" src="https://github.com/user-attachments/assets/3e3cc7b9-67a9-4ef4-aa37-7607e976e3f1" />

13. Create Another Backup
    
   <img width="494" height="133" alt="image" src="https://github.com/user-attachments/assets/5611a5ed-6c84-429f-9157-bdcb4fe51463" />
In earlier steps I orginally ran my intial backup to verify it and make sure that it works. Now we are testing it
to make sure we can retrieve files if my system were to ever crash. We need to do another backup since I created a "Test File" after I
completed the intial backup so my disk does not know about this file without another backup.

15. Verify that the most recent backup exists
    
<img width="488" height="145" alt="image" src="https://github.com/user-attachments/assets/49c244f3-1d4f-4d05-939c-d0b9e2cef324" />

17. Delete the file and verify that it is no longer there
    
    <img width="407" height="148" alt="image" src="https://github.com/user-attachments/assets/4c6ff6f3-d888-4c3e-9f23-f94319340805" />

19. Create a Directory for the recovered files to go to
    
    <img width="492" height="211" alt="image" src="https://github.com/user-attachments/assets/4d9471ad-0ffe-4a90-8d8e-29ab6d563740" />
    
Orginially I tried to restore the recovered files into a different directory on the C: file path. Instead I went on to create a new file in
a different pathway. This worked better becuase I was not restorying directly into the same source volume

20. Run the recovery command in Powershell
    
    <img width="504" height="234" alt="image" src="https://github.com/user-attachments/assets/dc49ae70-aaf9-4748-a0c3-1783762421eb" />
    
When you are running this command it's important that you get the version number of your backup and not the time that it was completed becuase
those were actually 2 different numbers.

22. View the Recovered Files
    
<img width="500" height="256" alt="image" src="https://github.com/user-attachments/assets/54bb341d-0c29-4dbd-a88b-3754c24c4635" />

23. View the File Contents
    
    <img width="496" height="149" alt="image" src="https://github.com/user-attachments/assets/1c14f91d-4f45-4084-a177-510ee2599e25" />
    
Now we have successfully set up our backup for our server and also tested that it was able to recover files once deleted. 

    





