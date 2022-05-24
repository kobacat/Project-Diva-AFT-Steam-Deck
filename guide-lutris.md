## PROJECT DIVA ARCADE FUTURE TONE STEAM DECK GUIDE - LUTRIS METHOD

Special thanks to Decadence for writing an initial guide for this, and for helping me troubleshoot through any errors using this method.

**WARNING:** This method worked for me, but it may not work for you. I don't take any responsibility if you somehow end up bricking or breaking something, and I can't provide tech support for anything relating to that either. This guide isn't going to be _too_ technical, but **make sure you're safe modifying your system if needed, and that you're comfortable with something possibly breaking down the line.** You've been warned.

Still here? Cool, let's get started.

## PREQUISITES

- A Steam Deck. Make sure you have enough storage, the base storage of 64 GB may not be enough for everything. You'll probably need around 35 GB of space for everything.
- A copy of Project Diva Arcade Future Tone. I'm not going to share that here since it'd be piracy, just know that you need the actual game and it needs to be version 7.10.
- A copy of PD-Loader in your PDAFT folder. [Make sure to follow the wiki guide for that.](https://github.com/PDModdingCommunity/PD-Loader/wiki/2\)-Installation)
- [An additional copy of the PD-Loader .zip file that you can download on here.](https://github.com/PDModdingCommunity/PD-Loader/releases/tag/2.6.5a-r4n)
- [A copy of amdgpu-pro-libgl that you can download here](https://drive.google.com/file/d/1LhzgXbzD8k3xfLeJojzKGGOw8Ep6pmxq/view?usp=sharing)

## DOWNLOADING/MOVING THE FILES

Download or move your PDAFT folder and extrac the amdgpu-pro-libgl folder to your Documents folder. You can probably move it to others instead, but **make sure to not put the game in a another flatpak space, like a Bottles folder or something**. I just put it in Documents to make it easier.

Make sure you also have your copy of the PD-Loader .zip file somewhere where you can easily find it, something like Desktop or something. You won't need it anymore after you're done with the guide.

Again, make sure you have enough storage to do this. If you need to, free up some space on your Internal Storage by getting an SD Card and moving stuff over to that.

## LURIS

Install Lutris from the Discover Browser and launch it.

![image](https://user-images.githubusercontent.com/22461806/170128102-08753a99-e912-4108-8f83-7cce30da6b71.png)

Once in the program, click the + in the top right corner of the program and search for installers.

![image](https://user-images.githubusercontent.com/22461806/170128458-34e978b7-4266-484d-bcc0-3f5aefeecb57.png)

Find Project DIVA Arcade and *make sure to install the version that says* ***2021.4***.

![image](https://user-images.githubusercontent.com/22461806/170128565-f54c984e-66c8-4ba3-8afa-e062c3c78bcf.png)

![image](https://user-images.githubusercontent.com/22461806/170128627-f4994efe-d5a7-41e0-891e-79b7313132c6.png)

Make sure to select the PDAFT directory with the .exe as an installation directory. It's going to complain that the path contains files, don't worry about it, just click Install.

![image](https://user-images.githubusercontent.com/22461806/170129104-a5c81e50-7b99-4f83-b02d-18c619bd0929.png)

Once on the next page, change the Source from Dwnload to Select File, and click the PD-Loader .zip file you downloaded from earlier. Then click Continue, and the installation should begin.

![image](https://user-images.githubusercontent.com/22461806/170129285-fa661652-401a-45fe-9447-d91036039dca.png)

**NOTE:** I had some issues using this method when using the installer, where it seems like it would fail for seemingly no reason sometimes. I tried my best fixing it, and I have no idea if the steps I took actually fixed it or if I just got lucky with the installer. **If you have issues getting through the installer and it errors out, you can close the installer and try again, but make sure not to check off the box that says to delete the game files before closing it. Then, delete the bak and wineprefix folders inside your PDAFT folder, and then try doing the installation again using the same steps above.** You may need to do this even if you went through every step I listed, since the installation method is a little bit outdated. Either way, when the installation finally finishes, continue onward to the next part of the guide.

## CONFIGURATION

Next, go to where you extracted amdgpu-pro-libgl and keep track of the path. For example, mine is `/home/deck/Documents/amdgpu-pro-libgl/`.

Go into `amdgpu-pro-libgl/usr/bin` and find the progl executable file. Open it with some text editor, I used KWrite for this. **Change the export lines so it matches with your progl directory.** I just have my own directory listed here, but **change the directory I write if you have it in a different location than the one I wrote above**:

`progl() {
    export LD_LIBRARY_PATH="/home/deck/Documents/amdgpu-pro-libgl/usr/lib/amdgpu-pro/:${LD_LIBRARY_PATH}"
    export LIBGL_DRIVERS_PATH="/home/deck/Documents/amdgpu-pro-libgl/usr/lib/dri/"
}`

`progl32() {
    export LD_LIBRARY_PATH="/home/deck/Documents/amdgpu-pro-libgl/usr/lib/amdgpu-pro/:${LD_LIBRARY_PATH}"
    export LIBGL_DRIVERS_PATH="/home/deck/Documents/amdgpu-pro-libgl/usr/lib32/dri/"
}`

After you're done, make sure you save the file, then exit out of it.

Now, in Lutris, click the icon for Project DIVA once so it's highlighted, then click the arrow on the bottom of the program next to the Wine icon. Open up Winetricks, select the 'Select the default wineprefix' option, then on the next page, select the 'Install a Windows DLL or component'.

Use Winetricks here to install dotnet48 and vc2019 if they aren't already installed. Follow the prompts and exit them when you're finished installing them. You can close Winetricks now.

*NOTE: When I went through this myself, Winetricks seemed to close after starting to install dotnet48 and vc2019. I waited a good 30-40 minutes and then continued on with the process and it seemed to work fine. I don't know if I already had these installed, or if Winetricks was just acting weird here, so I thought I'd just keep that in mind. This probably won't apply to you, though.*

Now, go into Lutris again and right click the Project DIVA icon. Click on 'Configure' to open up the configuration menu. Click on 'Show advanced options' on the bottom left of the window, and then click on the 'Runner Options' tab on the top of the window. Add two dll overrides if they don't exist already: `dinput8.dll` and `dnsapi.dll` with the values of `n,b`.

![image](https://user-images.githubusercontent.com/22461806/170132221-26fbc7c4-8515-40c1-981b-b1affcba21ff.png)

After that, go to the 'System options' tab and add this to the 'Command prefix' box; *Again, if your progl path is different than mine, then change your path.*:

`/home/deck/Documents/amdgpu-pro-libgl/usr/bin/./progl`

![image](https://user-images.githubusercontent.com/22461806/170132658-6b223714-396a-4257-820a-227c94512b42.png)

After that, you can try loading into the launcher by pressing the Play button in Lutris. If you followed the steps correctly, it should hopefully work.

![image](https://user-images.githubusercontent.com/22461806/170132862-23db7c58-d51f-4cfb-a6b1-c9bc2613a810.png)

## GAME CONFIGURATION

Under **Graphics**, you should enable Internal Resolution and change it from `1920x1080` to `1280x720`, since the Steam Deck's display is only 1280x800, and you'll only be pushing the game harder for no real reason if you leave it set to 1920x1080.

Under **Options**, make sure **Disable Movies** is Enabled.

Under **Plugins and Patches**, make sure **DivaSound** and **Novidia** are both enabled. Under **Novidia**, make sure **everything is checked**. (I'm not exactly sure if you need everything checked, but it works fine for me like this. Feel free to experiment, just make sure `Disable AMD Check` is enabled at least.)

Now, press `Launch`. If all went well, the game should now boot up. It might take a minute or two for the game to boot up, so don't worry if the window looks like it's frozen or glitched. Just give it some time.

![image](https://user-images.githubusercontent.com/22461806/169700500-ad224c67-7094-4f71-9c1d-90662c3cbe5b.png)

**NOTE: When launching the game, you may notice the audio isn't working. To fix this, go back into Lutris and click the arrow next to the wine icon on the bottom of the window again, and click 'Wine configuration'. Make sure your Windows Version is set to Windows 7. Mine was Windows XP for some reason, and it seemed to break the audio. Changing it should fix it.

![image](https://user-images.githubusercontent.com/22461806/170133344-064b5a8b-c2c2-4b61-a0b0-1c813fe75373.png)

## EXTRA STUFF

----------------

If your game is running slow still, try adjusting some settings and disabling things you may not need. Remember that you're running this thing on a 800p tablet screen, so you're not going to need to have all the specs maxxed out, especially if it's causing some performance issues.

----------------

If you want to launch the game with Steam, you can add a shortcut through Lutris. **Make sure Steam is closed for this. This means you may need to use something like AnyDesk or use a keyboard and mouse to control it for this part.**

Launch Lutris and highlight Project Diva in Lutris, right click it and click 'Create steam shortcut'. You can return to gaming mode, and you'll be able to play Project Diva through it now.

Make sure to bind one of your trackpads to the mouse (both movement and clicking) so you can navigate PD-Launcher so you can Launch the game.

Also, if you want to make your game look nice with custom artwork, [you can go to SteamGridDB to get art for it so it fits well in Gaming Mode, too.](https://www.steamgriddb.com/game/5252718)

![image](https://user-images.githubusercontent.com/22461806/170134945-44eceab5-e2cd-49a5-9db7-c91b22f4a732.png)

![image](https://user-images.githubusercontent.com/22461806/170134959-19f1daa6-1bfa-44f2-a572-91c17659b8d2.png)

----------------

Adding mods should be about as straightforward as it is on Windows, and you can grab plenty of mods for Aracde in the [Project DIVA Modding 2nd](https://discord.gg/cvBVGDZ) Discord Server. It's possible something can break though, so be prepared to troubleshoot if that happens.

----------------

For more help on PDLoader, [make sure to check the wiki for it here](https://github.com/PDModdingCommunity/PD-Loader/wiki/2\)-Installation).

----------------

If you run into any more issues, you can try contacting me on Discord at **koba#8162**. I can't guarantee I'll be able to help you, but if you have any issues with the guide, feel free to let me know and I'll see what I can do to help or if there's anything that needs to be fixed.

Also, it's completely possible this guide may become obsolete in the future as someone else could come up with a better way to get the game running on Steam Deck ~~or SEGA could bring Mega Mix to Steam, but [there's no way that'll ever happen. right?](https://steamdb.info/app/1905750/)~~. Hopefully this guide helps at least one person though. If the game works for you, hope you're able to enjoy it!

