![image](https://github.com/user-attachments/assets/f2afb8f8-43f9-485c-bc16-0252dcdeb1c5)![image](https://github.com/user-attachments/assets/820c5869-2a5e-4b1a-90d4-97263830c582)![image](https://github.com/user-attachments/assets/b24dc16e-869e-46d7-ae16-7df4b218f770)![image](https://github.com/user-attachments/assets/2b4c305b-9c58-4f93-8aea-b78ad5ec80c1)![image](https://github.com/user-attachments/assets/03dfd263-5cf2-4f85-abb6-928b7b969425)# unraid-emby-zurg

Welcome and feel free to use my guide
special thanks goes to @kentuckyrunner for helping me along the way otherwise none of this would exist. Kudos to you man!.



Tutorial to implement zurg with strm files and emby server on UNRAID instance.


Things you need before we start:
1.	Unraid version 7.0.1 instance working, with array up. – this guide expects you to know your way around the unraid.
2.	An installed and functioning Emby Server – grab a official emby repo. in the apps
3.	A paid account from Real-Debrid
4.	Pull the zurg lib it into docker, Here are the links from the github page: https://github.com/debridmediamanager/zurg-testing?tab=readme-ov-file

 # Lets start:

# Step 1  - create a share and a folder  in /mnt/cache/appdata
You can do that by going to :

Unraid webui > Share > Create user share - create a new root share give it a name “zurg”
For Primary storage option select: cache
Nothing else to change for now, just click on add share button
<img width="390" alt="image" src="https://github.com/user-attachments/assets/62d93cf5-288f-4e41-8607-1270cb914497" />

After you Click add share, then the settings for the newly created share will automatically pop up, then set it up as follows:
Scroll down to nfs security settings (you should have nfs enabled in settings – do check it please)
Export: YES
Security: Public
<img width="452" alt="image" src="https://github.com/user-attachments/assets/ee097ef1-804c-4855-981e-9455baab3dfa" />

Scroll down to smb settings
<img width="452" alt="image" src="https://github.com/user-attachments/assets/20c8606b-98d2-4633-8cc9-c86fdf4691a4" />

Make sure u select 
export – YES, if u fail to do so, share wont be visible and none of this will work! 
security – Public
click on APPLY

Now open that newly created share, and create folders: data and strm inside the zurg folder

      - /mnt/cache/zurg/data
      - /mnt/cache/zurg/strm

In the /mnt/cache/zurg you will also put the config.yml later on...

# Step 2 

Now its time to fill up the config file - config.yml
Example of the config is available here: 

For RD api key head to website real-debrid.com click on the “My devices”
Copy your rd token in the API Private token part down bellow and copy that key in the config

<img width="331" alt="image" src="https://github.com/user-attachments/assets/b1744ffe-c42f-4f8b-8b85-d61bea7f5a1d" />

When done adjusting the config, put it to /mnt/cache/zurg before proceeding


Now head to portainer web ui, you can access it in the Docker menu, click on the icon and select webui, or open in browser via ip address – up to you

<img width="327" alt="image" src="https://github.com/user-attachments/assets/75bc86f5-2c98-4068-a9ec-7774fb5b0aa8" />

Login: admin:admin

To authorize the portainer for it to pull the image, u need to set a registry in the portainer first, this will give the portainer auth so it can pull the zurg nightly release with ease…

U need to have token created, to do so follow this instructions> https://www.patreon.com/posts/guide-to-pulling-105779285

When u have the token, head to host then registries > create registry and fill accordingly: 
Username: your github name
Password : token u generated

<img width="452" alt="image" src="https://github.com/user-attachments/assets/f0727849-a713-402a-9002-f263e0505e8d" />

When u authorized the portainer, head to local environment

<img width="366" alt="image" src="https://github.com/user-attachments/assets/dc07ac8c-ac8b-4a3f-b4f5-120da0a22978" />

Next head to stacks click on it

<img width="201" alt="image" src="https://github.com/user-attachments/assets/7ba90c46-0e68-40b3-a9fc-3c70c715076e" />

Find Add stack and click on it

<img width="452" alt="image" src="https://github.com/user-attachments/assets/e6c669e5-1213-407a-b62a-782213752981" />

Give it a name > mine is zurg

Paste the following docker-compose into the web-editor: 

scroll all the way down

<img width="148" alt="image" src="https://github.com/user-attachments/assets/438e9e71-e6ac-424c-9ea6-f37a53539724" />

Click deploy the stack this will pull zurg with auth


This means step 2 is done.

# Step 3

Check the portainer about the zurg 


