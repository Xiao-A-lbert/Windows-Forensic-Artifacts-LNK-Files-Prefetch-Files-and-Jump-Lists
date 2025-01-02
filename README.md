# Windows Forensic Artifacts: LNK Files, Prefetch Files, and Jump Lists

<h2>Description</h2>
In this Digital Forensics task, I used tools like exiftool, prefetch parser, and jumplist explorer to explore artifacts in LNK files, prefetch files, and jump lists. 

<h2>Languages and Utilities Used</h2>

- <b>exiftool</b>
- <b>prefetch parser</b>
- <b>jumplist explorer</b>

<h2>Environments Used </h2>

- <b>Windows 10 Enterprise</b> 

<br />
<br />
C:\Users\albert\AppData (hidden file)\Roaming\>Micorsoft\Windows\Recent Items shows lnk files. Looking at the Autoruns properties shows that is a lnk file. 

![1) file explorer  recent items autoruns properties showing lnk file](https://github.com/user-attachments/assets/2b952c5b-1f55-4f9d-bb3b-4cc9dd19df40)

<br />
<br />
After creating a txt file named Delete Me, populating that file with "Hello World", then permenantly deleting this file in the recycling bin, then going to C:\Users\albert\AppData (hidden file)\Roaming\>Micorsoft\Windows\Recent Items will show the lnk file for Delete Me. This helps show files that were deleted. 

![2) deleteme lnk file still here after txt file was deleted](https://github.com/user-attachments/assets/0bf38a9a-cf08-4b41-91c3-c27a03dc919f)

<br />
<br />  
Using the exiftool in the cmd to enumerate the deleted Delete Me lnk file. 

![3) using exiftool to extra metadata from deleted deleteme file](https://github.com/user-attachments/assets/fa8df59a-0cac-4da2-99fc-68a8b2d7440a)

<br />
<br />
The output shows variouts parameters like file size, local base path, and relative path of the deleted Delete Me file through its lnk file. 

![4) metedata for deleteme txt](https://github.com/user-attachments/assets/521da08c-2655-4c66-a2ed-0ffd641b547e)

<br />
<br />
Going to C:\Windows\Prefetch and observing the Calculatorapp executable along with its file hash. 

![5) prefetch files with their associated hash](https://github.com/user-attachments/assets/6903a4ad-d8c9-45d5-a0e2-be530dc9ce8a)

<br />
<br />
After downloading Eric Zimmerman's Prefetch Parser and running it in the cmd with the NOTMALWARE.EXE, it shows a lot of file details for that prefetch including run count, directories referenced, adn files referenced. 

![6) prefetch parser cmd to examine notmalware exe prefetch](https://github.com/user-attachments/assets/5e92989e-06f4-4a9b-8510-0acd835bdd43)

<br />
<br />
Using admin cmd to copy the calculator app from prefetch as conhost.exe onto my desktop. This resulted in two conhost files in prefetch with different file hashes. 

![7) copying calc exe to desktop as conhost](https://github.com/user-attachments/assets/ca91de20-a0c5-4510-8715-0cb39ec9dab9)

<br />
<br />  
Running prefetch parser in the cmd on both conhost.exe files shows the second conhost file referenced to \Users\albert\Desktop\conhost.exe meaning this is the fake file. 

![8) using prefetch parser to show that the second conhost is from DESKTOP instead of system 32](https://github.com/user-attachments/assets/fa2eba37-2e41-4f21-9760-71097c3711a2)

<br />
<br />
In the cmd, running dir /ad on the C:\Users\albert\AppDAta\Roaming\Micorsoft\Windows\Recent directory enumerates hidden files like AutomaticDestinations. Listing out this directory shows a jump list. 

![9) jumplist hidden directory thru cmd](https://github.com/user-attachments/assets/c626db7f-41a0-4273-8b9e-9c2ea2268184)

<br />
<br />
Copying the file path into JumpList Explorer shows file paths for directories accessed within the Window's Explorer row. 

![10) copying path automaticdest to jumplist explorer and looking at artifacts](https://github.com/user-attachments/assets/6eda855a-9dab-4761-af59-8fb626a409e1)

<br />
<br />
