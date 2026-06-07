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

<img width="975" height="472" alt="image" src="https://github.com/user-attachments/assets/ed97bb08-2305-433d-9cc9-b0e9cbebf29b" />

<img width="402" height="84" alt="image" src="https://github.com/user-attachments/assets/0a5d0069-3abe-4f5a-ae40-5039b8529996" />

There is a gold emblem on the wall, take it and we get the gold_emblem flag.

<img width="975" height="209" alt="image" src="https://github.com/user-attachments/assets/518e35bc-e7d1-4f8b-ab5f-8471740487e6" />

<h2>Access the Dining Room:</h2>

<img width="975" height="557" alt="image" src="https://github.com/user-attachments/assets/d5caaecb-e5fe-44d8-937a-de56e9e339b9" />

<img width="922" height="155" alt="image" src="https://github.com/user-attachments/assets/6071d6a7-5aa4-4b8b-9a54-7025ba81a534" />

Accessed the emblem slot page. A jumbled text appeared: "klfvg ks r wimgnd biz mpuiui ulg fiemok tqod. Xii jvmc tbkg ks tempgf tyi_hvgct_jljinf_kvc"

<img width="975" height="155" alt="image" src="https://github.com/user-attachments/assets/72b24627-29e4-44f6-8911-31b5bb84e875" />

Decoded the ciphertext using "rebecca" as key. Output revealed: "there is a shield key inside the dining room. The html page is called the_great_shield_key"

<img width="975" height="349" alt="image" src="https://github.com/user-attachments/assets/4630925f-a566-45f5-80eb-1ef2142c0ecb" />

<h2>Access the Great Shield Key Page:</h2>

<h2>Action: </h2>

Navigated to http:// 10.48.142.50/diningRoom/the_great_shield_key.html

<img width="975" height="211" alt="image" src="https://github.com/user-attachments/assets/f905b420-aacb-46b8-b4b4-a974d04583df" />

<h2>Next, let’s Access /DiningRoom2F:</h2>

<img width="975" height="478" alt="image" src="https://github.com/user-attachments/assets/56765efb-b2b2-4082-b2e8-7424f932a25c" />

Check the source code we see the following comment:

<img width="975" height="417" alt="image" src="https://github.com/user-attachments/assets/00ef6a59-61b3-4f9f-b44e-02fb2151583e" />

During the assessment, a hidden HTML comment was discovered containing an encoded message. The message was encoded using the ROT13 cipher technique, which is a simple letter substitution method.

<img width="940" height="364" alt="image" src="https://github.com/user-attachments/assets/19330fbc-8c58-4a10-b6cb-d402cdecd55e" />


You get the blue gem by pushing the status to the lower floor. The gem is on the diningRoom first floor. Visit sapphire.html.

We can now navigate back to /diningRoom/sapphire.html and we get the blue_jewel flag.

<img width="975" height="127" alt="image" src="https://github.com/user-attachments/assets/284f9340-78e6-4bed-a261-d55ec36a9b70" />


<h2>Next, Access /Tiger Status Room:</h2>

<img width="975" height="538" alt="image" src="https://github.com/user-attachments/assets/94fb99bd-78c8-4b84-ac00-1097534815c1" />

Paste the blue gem flag into and submit:

<img width="645" height="183" alt="image" src="https://github.com/user-attachments/assets/0258b714-f735-4f22-abad-443b6c8ee09b" />


<img width="975" height="199" alt="image" src="https://github.com/user-attachments/assets/b0e39e71-063d-4cff-b1c1-4e954c390fe0" />




<h2>crest 1</h2>

I’ve got crest 1. It’s been encoded twice, so let’s decode it twice: from base64 and then base32:

<img width="975" height="661" alt="image" src="https://github.com/user-attachments/assets/19bf0bbd-acd8-4883-b8b6-34e1182c7a22" />


So my crest 1 will be: RlRQIHVzZXI6IG


<h2>Next, Access /Gallery Room:</h2>

<img width="975" height="526" alt="image" src="https://github.com/user-attachments/assets/330fe4b8-ca11-4d97-9cbf-c00c7961c7fa" />


<h2>“EXAMINE”:</h2>

<h2>Crest 2 </h2>

<img width="975" height="237" alt="image" src="https://github.com/user-attachments/assets/937b85f8-cd24-4c76-b1de-f248cf79abca" />


Decode crest 2 from base32 and base58:

<img width="975" height="489" alt="image" src="https://github.com/user-attachments/assets/3344834f-4648-4570-b56d-9ef152f29f31" />


So my crest 2 will be: h1bnRlciwgRlRQIHBh

<h2>Access the Next /Study Room:</h2>

<img width="875" height="719" alt="image" src="https://github.com/user-attachments/assets/cf948a4c-1da6-4a44-9add-4e91d43821d9" />


<img width="539" height="186" alt="image" src="https://github.com/user-attachments/assets/6b307bd7-2814-4d48-852b-30fff8209e27" />


<img width="472" height="131" alt="image" src="https://github.com/user-attachments/assets/8de5d07b-87a3-4818-83c4-191f421b572b" />


Oh shit this is also locked.

<img width="975" height="170" alt="image" src="https://github.com/user-attachments/assets/f74fd749-ab9d-4dd0-9e58-a95398537f28" />


<h2>Next, Access /Armor Room:</h2>

<img width="975" height="667" alt="image" src="https://github.com/user-attachments/assets/47c93384-5369-4b54-9499-a07d84ab4a22" />


Paste the shield key flag into and submit:

<img width="975" height="724" alt="image" src="https://github.com/user-attachments/assets/c97df137-6c9c-4952-ab98-d8470844e09d" />


<h2>“READ”</h2>

<h2>Crest 3</h2>

<img width="975" height="202" alt="image" src="https://github.com/user-attachments/assets/c8aa4d4d-6b1e-416c-a24a-7423b4d2ff02" />

Crest 3: decoded

Decode crest 3 from base64, from binary and from hex:

<img width="975" height="386" alt="image" src="https://github.com/user-attachments/assets/8f24d807-1305-4a3e-9446-3f7d7348f033" />


So my crest 3 will be: c3M6IHlvdV9jYW50X2h

<h2.Next, Access /Attic:

<img width="975" height="749" alt="image" src="https://github.com/user-attachments/assets/ae5c416e-52f5-438a-817f-7626c8a4d7be" />

Well, paste the shield key flag and submit:


<img width="538" height="153" alt="image" src="https://github.com/user-attachments/assets/39d84fa0-0436-4eb8-ad5a-f8943ae9d850" />



<img width="975" height="611" alt="image" src="https://github.com/user-attachments/assets/37da77fe-3da1-49e8-bbaf-b112ebbf1066" />


<h2>“READ”:</h2>

<h2>Crest 4:</h2>


<img width="975" height="196" alt="image" src="https://github.com/user-attachments/assets/9dd6130c-080c-4458-9e8d-20589a6ac9a0" />


Crest 4: Decode:
Decode crest 4 from base58 and from hex:


<img width="975" height="355" alt="image" src="https://github.com/user-attachments/assets/d1e956e3-ff4e-4c11-97db-082423ae56bd" />


So my crest 4 will be: pZGVfZm9yZXZlcg==


<img width="975" height="308" alt="image" src="https://github.com/user-attachments/assets/9a452538-1523-4272-9880-da4972443eba" />


Combine 4 crests, I’ve got the complete a base64 encoded string:


<img width="975" height="377" alt="image" src="https://github.com/user-attachments/assets/eddef94a-7cb5-4a2a-be68-fdcae170eab6" />


We now have the FTP credentials to access port 21, back to our terminal.
FTP user: hunter, FTP pass: you_cant_hide_forever
FTP Server Port 21

Log into the ftp server using the found credentials.

<h2>I’ve got the FTP username and password.</h2>


Used Command: ftp <10.48.172.28>

<img width="972" height="614" alt="image" src="https://github.com/user-attachments/assets/d9a55910-e99d-44aa-8de6-5d130bbf9fab" />


<img width="972" height="614" alt="image" src="https://github.com/user-attachments/assets/76f73cc5-3fc1-4422-84c9-43290cc76204" />


Next I mget * all the files and download them for analysis.

Let’s read the content of ‘important.txt’:


<h2>So, the hidden dir will be: /Hidden Closet/. Access it:</h2>


Well again, I need the helmet flag. It will be in the “helmet_key.txt.gpg”, but in order to decrypt gpg file, I need the password. Look at the hint:


<img width="573" height="225" alt="image" src="https://github.com/user-attachments/assets/0a36bec1-5cc7-4b86-8fd0-3151f5cf01db" />


So the password to decrypt will be inside the 3 photos. I will use steghide to extract data inside the 1st photo:
Using this  (CMD) steghide extract -sf 


<h2>Image: 001-key.jpg</h2>

<img width="975" height="348" alt="image" src="https://github.com/user-attachments/assets/9ca8d75d-ca72-42d7-8a94-d6aa279e5b16" />


<h2>Image: 002-key.jpg.</h2>

Using Strings we find a code contained within the comments.
Using Command this exiftool 002-key.jpg  (exiftool)


<img width="855" height="680" alt="image" src="https://github.com/user-attachments/assets/ebd52c21-b207-4cb2-8a3a-fd902ac8f570" />


<h2>v</h2>

Initially I tried Steghide; however, it required a passphrase.

Using this (CMD) (binwalk)

<img width="975" height="324" alt="image" src="https://github.com/user-attachments/assets/abe14d02-0a8a-4cd8-afab-285fe3c16515" />


Combining all the keys we get:

cGxhbnQ0Ml9jYW5fYmVfZGVzdHJveV93aXRoX3Zqb2x0

This is base64 encoded, decoding the string:

<img width="975" height="349" alt="image" src="https://github.com/user-attachments/assets/b551f6d1-6a70-406f-afe5-711909c90b87" />


<h2>Decrypting helmet_key.txt.gpg</h2>

<h2>Action:</h2>

Action: (Run command: gpg -d helmet_key.txt.gpg) Explanation: Used the gpg tool to decrypt the file with the passphrase plant42 _can_be_destroy_with_vjolt. The decryption was successful and revealed the final flag:


<img width="592" height="181" alt="image" src="https://github.com/user-attachments/assets/a9a9d772-4aed-41f9-902a-010791b041f3" />


helmet_key{458493193501d2b94bbab2e727f8db4b}



<h2>Next, Access /study Room:</h2>


<img width="975" height="423" alt="image" src="https://github.com/user-attachments/assets/6a111e4f-9849-493a-a1c9-d1d318e5982e" />


Armed with the helmet_key flag we can now enter the Study Room.


<img width="534" height="161" alt="image" src="https://github.com/user-attachments/assets/da08b096-6ce9-4a72-8682-52f6cb3ad0db" />


<h2>Access the Study Room</h2>

<img width="589" height="180" alt="image" src="https://github.com/user-attachments/assets/264cd189-b9d2-43a8-af3f-cf270f0314b9" />


<img width="914" height="288" alt="image" src="https://github.com/user-attachments/assets/e7742e09-a75e-4610-b1ea-d005e304272d" />


<h2>Examine the book? “EXAMINE”</h2>

<img width="820" height="681" alt="image" src="https://github.com/user-attachments/assets/70e2d468-f949-49f7-b4f5-d931d725d2b1" />


We can examine the book which allows us to download a Gunzip file called doom.tar.gz.


<img width="1083" height="345" alt="image" src="https://github.com/user-attachments/assets/9dddd6d4-f34a-4986-88ad-bcab7d962862" />


We decompress the file first using Gunzip and then Tar. The extracted file is called eagle_medal.txt

Reviewing the file we get the SSH user: umbrella_guest

Reading the Important.txt File Command Used: cat important.txt Explanation: Executed cat important.txt command. The file contained a message from Barry mentioning a helmet key, decryption difficulty, and a locked /hidden_closet/ door.


<img width="975" height="120" alt="image" src="https://github.com/user-attachments/assets/d7f78d34-ddbc-43e1-9edc-15ff44e018b4" />


<h2>Next, Access /Hidden_Closet/:</h2>

<img width="527" height="175" alt="image" src="https://github.com/user-attachments/assets/233876ce-c2df-4d3a-8208-532d192830fe" />


<img width="975" height="571" alt="image" src="https://github.com/user-attachments/assets/ff59dc7a-84f3-4220-83a2-5df73dbde815" />


Again a locked door, but it has the helmet symbol, so lets try and use the helmet_key flag.


<img width="495" height="159" alt="image" src="https://github.com/user-attachments/assets/87027ed5-734b-43af-9683-e56152ef1062" />



<img width="975" height="172" alt="image" src="https://github.com/user-attachments/assets/33c95676-8ab3-4d05-ba8f-31172c52b5d5" />



<img width="975" height="448" alt="image" src="https://github.com/user-attachments/assets/215fa30f-f6db-4258-8e96-ed1d1ac8a36c" />



First Reading the MO disk 1? we get the following encoded message:


<img width="975" height="176" alt="image" src="https://github.com/user-attachments/assets/dfa9d044-1353-4e5f-ac1f-6519d1ccb9b5" />


Another Vigenere encoded string. I haven’t known the key, so let’s skip it.

<h2>Examining the the wolf medal: “EXAMINE”:</h2>

<img width="975" height="153" alt="image" src="https://github.com/user-attachments/assets/9016645b-d644-422f-842f-1162fe764c4d" />


I’ve got the SSH password: T_virus_rules


<h2>As I’ve got the SSH credential, let’s login to SSH:</h2>


Using this (CMD) ssh umbrella_guest@<ip>


<img width="975" height="425" alt="image" src="https://github.com/user-attachments/assets/dffcc48d-38be-4758-833e-814d04b392c0" />


 Move around to view files:


 <img width="975" height="270" alt="image" src="https://github.com/user-attachments/assets/a48b5852-94e5-4057-881a-34d474f1cbe5" />


Navigating to this directory we see a file called chris.txt:


<img width="975" height="459" alt="image" src="https://github.com/user-attachments/assets/e7af005f-d1cc-4316-b556-2e7b7c3f6d61" />


Command Used: ls -la 
cd .jailcell/
ls cat chris.txt


<h2>Remembering back to the Closet Room we decoded a cypher:</h2>

<img width="975" height="152" alt="image" src="https://github.com/user-attachments/assets/c03ee162-2b33-4724-99b0-719df4b7dbc8" />




<img width="975" height="390" alt="image" src="https://github.com/user-attachments/assets/1e6f6524-c8a5-438f-b13e-74afb30306c4" />



<h2>Read the MO disk 1?  “READ”</h2>

CyberChef - Vigenere Decode)

<img width="975" height="435" alt="image" src="https://github.com/user-attachments/assets/a07e1247-d454-4789-9c55-ccda53e0f129" />


Again, login ssh new credential (albert weasker password: stars_members_are_my_guinea_pig)







<h2>Privilege Escalation to Root</h2>


Using this (CMD): sudo -l
 sudo su
 cd /root
 ls
 cat root.txt


<h2> Explanation:</h2>

 Checked sudo privileges with sudo -l (user weasker had full sudo access). Used sudo su to switch to root user, navigated to /root directory, and read the final flag file root.txt


 <img width="975" height="318" alt="image" src="https://github.com/user-attachments/assets/0a0210e8-235b-45a6-892f-b4593ab53cce" />



I really enjoyed this box. Although it really was a more CTF than exploiting system vulnerabilities, I lived the Resident Evil theme, plot and challenges.
