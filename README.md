# Biohazard
The Biohazard room is a story-driven cybersecurity challenge that simulates a Resident Evil-themed environment. Participants must investigate a mysterious mansion, collect hidden items, solve multiple puzzles, decode encoded messages, access FTP and SSH services, and ultimately compromise the target system to obtain root access. 

<img width="1152" height="864" alt="image" src="https://github.com/user-attachments/assets/f18855b3-f69f-4d8b-8ea0-1ad271092c23" />


<h2>Executive Summary</h2>

The Biohazard lab simulates a real-world penetration testing environment. The objective was to identify vulnerabilities in the target system, exploit them to gain unauthorized access, and retrieve sensitive information (flag). The assessment successfully identified multiple weaknesses including exposed services, misconfigurations, and exploitable vulnerabilities.


<h2>Scanning:</h2>

Use this (CMD) nmap -sS <10.49.165.241>

<img width="838" height="272" alt="image" src="https://github.com/user-attachments/assets/0c18ae36-3e81-4eb0-a3dc-808409b40b54" />

we have three ports open, port 21 (Ftp), port 22 (ssh) and port 80 Apache web server. As there appears to be no anonymous login allowed on the ftp server, I will start with port 80, the Apache webserver.

<h2> Start a Enumeration.</h2>

<h2>Port 80: </h2>

(Opened browser and visited http:// 10.49.165.241)

<img width="975" height="743" alt="image" src="https://github.com/user-attachments/assets/8318e445-0b52-4c0f-8025-cfe8b2605704" />

Checking the source code there is nothing here; however, there is a link to /mansionmain.

(Opened browser and visited http:// 10.49.165.241 /mansion/)

<img width="902" height="573" alt="image" src="https://github.com/user-attachments/assets/1a78b381-eb71-41f7-908a-195b5a99f59f" />

Check the source code we can find the following directory in the comments ‘/diningRoom/’. Lets navigate to that room.

Press enter or click to view image in full size

<img width="975" height="288" alt="image" src="https://github.com/user-attachments/assets/314a3481-a223-4f8a-bf58-a0d12e9507f9" />

<h2>Access the Dining Room:</h2>

<img width="975" height="457" alt="image" src="https://github.com/user-attachments/assets/fba99785-108d-4f00-9041-409d5a8dff07" />

There is a link asking whether you will take the emblem on the wall, also in the page source there is what looks like a base64 encoded string.

<img width="975" height="413" alt="image" src="https://github.com/user-attachments/assets/e3b46f09-5a36-4ee2-a024-09a0dec5cdca" />

Decoding then Hidden Flag using Base64 

(Used CyberChef tool = From base64)

<h2>Explanation:</h2>

Took the Hidden string 

SG93IGFib3V0IHJvemF2Z2h1bV9vbHViUw== from page source and decoded it using Bases64 in CyberChef. The output revealed the next hint: “How about the /tearoom/”.

<img width="941" height="485" alt="image" src="https://github.com/user-attachments/assets/309c1af2-7178-45d3-94aa-a30c40ebc3d6" />

Clicking on the Lockpick link gives us the Lockpick Flag.

<img width="975" height="157" alt="image" src="https://github.com/user-attachments/assets/cf21f403-26b0-438f-b503-e2b3f267171d" />

<h2>Accessing the Tea Room Page.</h2>

<h2>Let Explore the Tea Room:</h2>

<img width="975" height="500" alt="image" src="https://github.com/user-attachments/assets/1f789154-e427-40a7-9639-7849912b43f0" />

In the notes it also states that Jill should visit the /artRoom.

<h2>Access the Art Room:</h2>

<img width="741" height="736" alt="image" src="https://github.com/user-attachments/assets/eb62d135-04bb-4714-b3f3-763fdd3dad39" />

From the Art Room, investigated the paper stick on the wall. The page loaded showing a map of the mansion with the following locations:

<h2>Action:</h2>

(Opened browser and visited http:// 10.49.191.39/artRoom/MansionMap.html)

<img width="298" height="414" alt="image" src="https://github.com/user-attachments/assets/32996b35-ecc8-4c93-8f04-ac760c1d9c0d" />

<h2>Access the Bar Room:</h2>

<img width="975" height="615" alt="image" src="https://github.com/user-attachments/assets/3e2fc30c-07ea-4392-8e51-2b2ac05e577c" />

<img width="452" height="173" alt="image" src="https://github.com/user-attachments/assets/5820e587-9ab3-4c46-b5d0-72ea924a56d8" />

Trying the lockpick flag and clicking ‘Submit’ opens the door to the barRoom.

<img width="509" height="172" alt="image" src="https://github.com/user-attachments/assets/b0c56bd2-6475-4c30-91da-30cb3f111b03" />

Trying the lockpick flag and clicking ‘Submit’ opens the door to the Bar Room.

<h2>Access the Bar Room:</h2>

<img width="975" height="539" alt="image" src="https://github.com/user-attachments/assets/fa19f061-4821-420b-aa36-ad0fc7dc0b01" />

<img width="975" height="254" alt="image" src="https://github.com/user-attachments/assets/73589743-c32e-47c0-80fe-3d6f903dcab6" />

Access the Music Note Page.

<h2>Action:</h2>

(Opene¬d browser and visited http://<ip>/barRoom/.../musicNote.html)

Clicked on READ for the "moonlight somata" note found in the bar room. The page loaded showing a music note:

<img width="975" height="125" alt="image" src="https://github.com/user-attachments/assets/5326a725-8b80-4da1-9102-50c9ec70e40e" />

Decoding the Music Note.

<h2>Action:</h2>

I would strongly suggest using a very good decoder, I tend to use CybreChef, see link below:
(Opened CyberChef and applied Base32 decode)

<h2>Explanation:</h2>

Took the string from musicNote.html:
NV2XG2LDL5ZWQZLFOR5TGNR5MQ3TEZDFMFTDMNLGGVRGIYZWGNSGCZLDMU3GCMLGGY3TMZL5
Used Base32 (A-Z2-7, removed non-alphabet chars).
Decoded output:

<img width="975" height="528" alt="image" src="https://github.com/user-attachments/assets/60e5392d-43c9-43d8-a854-9d0270ebc3d7" />

Music sheet{362d72deaf65f5bdc63daece6a1f676e}

<h2>Access the Hidden Bar Room Page.</h2>

Navigated to the hidden bar room page. The page shows a gold emblem embedded on the wall. Text displayed: "There is a gold emblem embedded on the wall. Will you take it? YES"

