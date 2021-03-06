
# DSR Texture Packer & Unpacker

[NexusMods Page](https://www.nexusmods.com/darksoulsremastered/mods/9)  
A tool to extract and replace textures in Dark Souls: Remastered. Running as Administrator is recommended.  
Requires [.NET 4.7.2](https://www.microsoft.com/net/download/thank-you/net472) - Windows 10 users should already have this.  
and [Visual C++ 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48145) - Make sure to get the x64 installer.

TPUP serves two purposes:
* To allow mod authors to unpack every texture in the game in order to edit them, and
* To allow players to easily merge and install texture packs from said authors.

# Instructions

If you're more of a visual learner, please watch [this video](https://youtu.be/D7zEDHe-Acw) going over the instructions; however, if you intend to create your own mods, please read the rest of this file as well.

First, download the tool and extract the entire folder wherever you like. After launching it, make sure the Game Directory field points to the folder where your game is installed (the folder that contains DarkSoulsRemastered.exe.) You may also change where unpacked textures are dumped to or where texture overrides are loaded from, but I recommend leaving those with the default.

### Creating Texture Mods

Unpacking the game's textures is only required if you want to make your own mods. Once the Game Directory is set correctly, switch to the Unpack tab, click the Unpack button, then go make yourself a sandwich; it will take quite a while to finish. You must have at least 7 GB of free disk space to complete a full unpack.

Once it finishes, find the texture you want to edit in the Dump folder, and place your replacement in the same relative directory in the Override folder. For instance, if you want to override *Texture Dump\menu\menu_0\Title.dds*, the replacement file should be at *Texture Override\menu\menu_0\Title.dds*.

If you're trying to port old dsfix textures, search for the hash in dsfix.txt; in many cases the DSR path will be different from the DS1 path, but it should give you a good idea of where to start looking. Some hashes will not appear in the file at all due to technical reasons that may or not be resolved at some point.

When repacking the textures, you will be warned if any files are in formats which do not match the vanilla files. It is highly recommended to go back afterwards and resave these textures yourself instead of relying on the automatic conversion.

Additionally, DSR uses some modern .dds formats which are not well supported in most image editors. Paint.NET users will need [this plugin](https://forums.getpaint.net/topic/111731-dds-filetype-plus-2018-06-03/) to open them, and Photoshop users will need [this one](https://gametechdev.github.io/Intel-Texture-Works-Plugin/).

To distribute your textures, I recommend including the entire override folder (with unwanted textures removed, of course,) so that users can easily merge it with their own.

### Installing Texture Mods

To install texture mods, copy the contents of their override folder into your own, or otherwise follow the author's instructions. Once the files are in place, open the app, verify that the Game Directory is set correctly, then switch to the Repack tab and click the Repack button. The game's files will be edited to include your texture overrides, and any modified files will be backed up. To revert all modded textures, click the Restore button in the app to restore all backed-up files.

# Troubleshooting

If the app crashes immediately after starting an operation or you see any errors related to file reading or writing, running the app As Administrator will usually help.

If there are problems with texture conversion, make sure you have the Visual C++ redist linked above installed, and that it's the x64 version.

If you run into "out of memory" issues, reduce the thread count to lower the peak load on your system.

If you're trying to install a mod but no files end up being repacked, pay close attention to the instructions for whatever mod you're using. The folders in the override should mirror the folders in your game install (chr, map, obj, etc.)

# Credits

[Costura.Fody](https://github.com/Fody/Costura) by Simon Cropp, Cameron MacFarland

[DirectXTex](https://github.com/Microsoft/DirectXTex) by Microsoft Corp

[Octokit](https://github.com/octokit/octokit.net) by GitHub

[Semver](https://github.com/maxhauser/semver) by Max Hauser

[TeximpNet](https://bitbucket.org/Starnick/teximpnet) by Nicholas Woodfield

# Changelog

### 1.5
* Reduced peak memory usage by up to 50% (especially under heavy load)
* Added an option for number of threads to use
* Less crashing

### 1.4
* UI improvements: progress bar, separate logs and errors, open in explorer buttons
* Added Convert tab if you want to convert some specific files yourself
* Added an option to keep auto-converted texture files
* Aborting an operation is much faster
* Unpacking textures now generates a report in each folder listing sizes and correct formats
* Accidentally improved performance by about 40%

### 1.3
* Format detection should be more reliable now
* More robust error handling
* Window can be resized
* Fix browsing for a repack folder changing the unpack folder instead
* Removed secret .png support (sorry)

### 1.2
* Fixed crash when repacking certain files

### 1.1
* Improperly formatted textures will now be automatically converted when repacking
* Included dsfix.txt to aid porting DS1 texture packs
