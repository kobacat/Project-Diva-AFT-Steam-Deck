## PROJECT DIVA ARCADE FUTURE TONE STEAM DECK GUIDE - BOTTLES METHOD

Special thanks to [EIREXE](https://github.com/EIREXE) and [Nastys](https://github.com/nastys) for the help getting this method working properly.

**WARNING:** This method worked for me, but it may not work for you. I don't take any responsibility if you somehow end up bricking or breaking something, and I can't provide tech support for anything relating to that either. This guide isn't going to be _too_ technical, but **make sure you're safe modifying your system if needed, and that you're comfortable with something possibly breaking down the line.** You've been warned.

Still here? Cool, let's get started.

## PREQUISITES

- A Steam Deck. Make sure you have enough storage, the base storage of 64 GB may not be enough for everything. You'll probably need around 35 GB of space for everything.
- A copy of Project Diva Arcade Future Tone. I'm not going to share that here since it'd be piracy, just know that you need the actual game and it needs to be version 7.10.
- A copy of PD-Loader in your PDAFT folder. [Make sure to follow the wiki guide for that.](https://github.com/PDModdingCommunity/PD-Loader/wiki/2\)-Installation)
- [A copy of amdgpu-pro-libgl that you can download here](https://drive.google.com/file/d/1LhzgXbzD8k3xfLeJojzKGGOw8Ep6pmxq/view?usp=sharing)

## DOWNLOADING/MOVING THE FILES

Download or move your PDAFT folder and extract the amdgpu-pro-libgl folder to your Desktop on your Steam Deck, just to keep track of where it is.

Again, make sure you have enough storage to do this. If you need to, free up some space on your Internal Storage by getting an SD Card and moving stuff over to that.

## BOTTLES

Install Bottles from the Discover browser and launch it.

![image](https://user-images.githubusercontent.com/22461806/169699517-5576e71e-688d-463b-96c6-a2a5209225e8.png)

Create a Bottle and name it whatever you want. I had mine in a Gaming Enviornment and the name is 'Diva', so the guide will reflect that. Just keep that in mind.

![image](https://user-images.githubusercontent.com/22461806/169699584-2de772dd-8653-4b1a-a229-8c2f2f632155.png)

In the Dependencies tab, **install both dotnet48 and vcredist2019**. This might take a bit of time, just stick through it and let them all finish installing.

![image](https://user-images.githubusercontent.com/22461806/169699903-67022096-9dba-481e-9014-eb5e2f346f4f.png)

![image](https://user-images.githubusercontent.com/22461806/169699906-18fab498-e994-4b41-a1c8-78f9eb30555d.png)

In the Preferences tab, click on **Manage drives**, and then **take note where the C drive is**. If you used the same name as mine, your C drive will be under `/home/deck/.var/app/com.usebottles.bottles/data/bottles/bottles/Diva/drive_c/`. Replace `/Diva/` with whatever other name you used, if you ended up using another name. **Remember to do this from here on out if there's another file path I write down, or else stuff might break.**

## TRANSFERRING FILES TO YOUR BOTTLE

Next, move your SBZV_7.01 folder (or whatever folder has all your game files in it) into `/Diva/drive_c/`. This might take a bit of time.

Then, move your `amdgpu-pro-libgl` (or whatever folder has `etc` and `usr` folders in it) into `/Diva/drive_c/`. This will probably take a lot less time.

It should look like this after you finish:

![image](https://user-images.githubusercontent.com/22461806/169699411-9d930285-be88-430d-b3be-a811a771aa34.png)

## CONFIGURING YOUR BOTTLE

Next, go into your **DLL Overrides** and add two new overrides: `dinput8` and `dnsapi`, both should be set to *Native then Builtin*. It should look like this.

![image](https://user-images.githubusercontent.com/22461806/169699265-ae054cc0-bc1f-414f-87b8-8120b2eec190.png)

Then, go to your **Enviornment Variables** and add two variables, `LD_LIBRARY_PATH` and `LIBGL_DRIVERS_PATH`. Make sure the values are set to this:

`LD_LIBRARY_PATH` = `/home/deck/.var/app/com.usebottles.bottles/data/bottles/bottles/Diva/drive_c/amdgpu-pro-libgl/usr/lib/amdgpu-pro:$LD_LIBRARY_PATH`

`LIBGL_DRIVERS_PATH` = `/home/deck/.var/app/com.usebottles.bottles/data/bottles/bottles/Diva/drive_c/amdgpu-pro-libgl/usr/lib/dri`

**MAKE SURE THE PATHS YOU POINT TO EXIST, IN CASE YOUR FOLDERS ARE NAMED SOMETHING DIFFERENT.**

It should look something like this after you're done.

![image](https://user-images.githubusercontent.com/22461806/169699372-bf33eafb-6b8d-4412-a64c-e88897e494c9.png)

Lastly, go into the Programs tab and click the + on the top of the window, and choose `diva.exe` to create a new program. You're free to rename this whatever you want, but for convenience, name this something like `PDLauncher`. This is going to be what you use to boot up the Launcher for the game. Press the play button for it, and if all goes well, you should be in the PD Launcher now.

![image](https://user-images.githubusercontent.com/22461806/169700184-6c06b715-3079-4e18-989c-ddec28e55ba9.png)

## GAME CONFIGURATION

Under **Graphics**, you should enable Internal Resolution and change it from `1920x1080` to `1280x720`, since the Steam Deck's display is only 1280x800, and you'll only be pushing the game harder for no real reason if you leave it set to 1920x1080.

Under **Options**, make sure **Disable Movies** is Enabled.

Under **Plugins and Patches**, make sure **DivaSound** and **Novidia** are both enabled. Under **Novidia**, make sure **everything is checked**. (I'm not exactly sure if you need everything checked, but it works fine for me like this. Feel free to experiment, just make sure `Disable AMD Check` is enabled at least.)

Now, press `Launch`. If all went well, the game should now boot up. It might take a minute or two for the game to boot up, so don't worry if the window looks like it's frozen or glitched. Just give it some time.

![image](https://user-images.githubusercontent.com/22461806/169700500-ad224c67-7094-4f71-9c1d-90662c3cbe5b.png)

Finally, under your **Programs**, you can add another `Diva.exe` like you did before, but this time go into the launch options and add `--launch` to bypass the launcher and create a method to boot up the game directly. You can name this something different from to differentiate it from PDLauncher.

## EXTRA STUFF

----------------

If your game is running slow still, try adjusting some settings and disabling things you may not need. Remember that you're running this thing on a 800p tablet screen, so you're not going to need to have all the specs maxxed out, especially if it's causing some performance issues.

----------------

**THIS METHOD TO LAUNCH THROUGH GAMING MODE IS KINDA BROKEN**

If you want to launch the game with Steam, you need to create a shortcut for your Bottle. Install Flatseal from the Discover browser, launch it and go into Bottles' settings. Scroll down to `Other files` and add `/home/deck/.local/share/applications`. 

Now, you can go back to Bottles and click on the Application for the game, and click on `Add desktop entry`. Then, add the .desktop file pointing to the game, which is in `/home/deck/.local/share/applications/`. 

Go into the properties of the .desktop file, and copy the Command used for it. For example, mine was `flatpak run --command=bottles-cli com.usebottles.bottles run -p 'Hatsune Miku Project DIVA Aracde Future Tone' -b 'Diva'`. 

Finally, back in Steam, go to the non-Steam game you added, wipe the `TARGET` and `START IN` fields, and add the Command you copied earlier into `LAUNCH OPTIONS`. If the command starts with `flatpak run --command=`, then you should be good to go.

----------------

Adding mods should be about as straightforward as it is on Windows, and you can grab plenty of mods for Aracde in the [Project DIVA Modding 2nd](https://discord.gg/cvBVGDZ) Discord Server. It's possible something can break though, so be prepared to troubleshoot if that happens.

----------------

For more help on PDLoader, [make sure to check the wiki for it here](https://github.com/PDModdingCommunity/PD-Loader/wiki/2\)-Installation).

----------------

If you run into any more issues, you can try contacting me on Discord at **koba#8162**. I can't guarantee I'll be able to help you, but if you have any issues with the guide, feel free to let me know and I'll see what I can do to help or if there's anything that needs to be fixed.

Also, it's completely possible this guide may become obsolete in the future as someone else could come up with a better way to get the game running on Steam Deck ~~or SEGA could bring Mega Mix to Steam, but [there's no way that'll ever happen. right?](https://steamdb.info/app/1905750/)~~. Hopefully this guide helps at least one person though. If the game works for you, hope you're able to enjoy it!
