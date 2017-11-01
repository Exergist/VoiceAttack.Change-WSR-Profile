## What is it?
A VoiceAttack profile for changing the active Windows Speech Recognition profile. 

## A VoiceAttack and Windows Speech Recognition Primer
### Wait, what is VoiceAttack (VA)?
More information about the VoiceAttack voice control and macro creation software may be found at www.voiceattack.com. It is an amazingly powerful application that will change the way you think about gaming and interacting with your PC in general.

### Why should I care about Windows Speech Recognition (WSR) and corresponding profile switching?
WSR allows you to use your voice to control your (Windows) computer, and VA dramatically expands upon this capability. To effectively use WSR you need to have a microphone (of course) and "train" your computer to better understand you. A WSR profile contains the information from the voice training. Besides needing different profiles for different users, the effectiveness of voice recognition is impacted by your microphone and your ambient surroundings (as well as other stuff). So WSR profile switching is very important if you have multiple users who want to employ voice control and, to a lesser extent, if you want to use voice control with different microphones or within different ambient noise environments. 

<img src="https://github.com/Exergist/VA.Change-WSR-Profile/blob/master/Images/Windows%207%20Speech%20Properties.png" title="Windows 7 Speech Properties" width="40%">

The catch is that switching profiles through the Windows interface is cumbersome. That is where VA.Change-WSR-Profile comes in. 

## How does it work?
The VA profile "Change WSR Profile" (corresponding to "Change WSR Profile.vap") provides two VA commands: 
 - Change WSR profile by voice command
 - Change WSR profile based on variable

As you might guess the first command allows the user to change WSR profiles using a voice command, and the second command allows the user to change to a specific WSR profile based on the value stored in a text variable. Both commands rely on a C# inline function that leverages the [Microsoft Speech API 5.4](https://msdn.microsoft.com/en-us/library/ee125663(v=vs.85).aspx) (Interop.SpeechLib.dll) to perform the actual profile switch. Feel free to check out the source code to better understand what's happening "under the hood."

## How do I install it?
This is going to be wordy, but I'm trying cater this to all users and be thorough. 

1. According to www.voiceattack.com "VoiceAttack works with Windows 10 all the way back to Vista." So you've got to have one of those versions of Windows to even use VA. Note though that I've only tested VA.Change-WSR-Profile in Windows 7 and Windows 10. 
2. There are currently two versions of the VoiceAttack software available: a purchasable full version and a free limited trial version (the trial version of VoiceAttack "gives you one profile with up to twenty commands"). You will need the licensed version of VoiceAttack to import the "Change WSR Profile.vap" file. This may be obtained at www.voiceattack.com or through [Steam](http://store.steampowered.com/app/583010/VoiceAttack/). I believe it would be possible to manually recreate the commands contained within the VA.Change-WSR-Profile for use with the trial version, however I will not be covering that. In my opinion the low cost for the VoiceAttack license was totally worth it. 
3. If you're unfamiliar with VoiceAttack this is a great time to check out the [VoiceAttack manual](http://voiceattack.com/VoiceAttackHelp.pdf) to acquant yourself with the application. 
4. Navigate to the [releases section](https://github.com/Exergist/VA.Change-WSR-Profile/releases) and download the most recent version (.7z file). Unzip the archive somewhere you can easily navigate to (like the desktop). 
5. Launch VoiceAttack (licensed version), open the "More Profile Actions" tool (one of the "Profile management buttons"...read the manual if you don't know what this is), and select "Import Profile." 
6. Navigate to the location where you unzipped the archive, select "Change WSR Profile.vap," and confirm the selection. Now you should have the "Change WSR Profile" available to you within VoiceAttack. At this point the "Change WSR Profile.vap" file is now longer needed and may be deleted since the profile is now loaded in VoiceAttack's internal files. 
7. Move the "Interop.SpeechLib.dll" file that you extracted from the archive to the root directory of VoiceAttack. Basically this .dll file needs to be placed in the same folder as the VoiceAttack.exe file. For me this is at "C:\Program Files (x86)\VoiceAttack\"
8. At this point all you need to do is edit the WSR profile name information inside the VA commands within the imported profile to match what is on your PC.
   - If you plan on using the "Change WSR profile based on variable" command you just have to edit the text variable "ActivatedProfile" to match the exact name of the WSR profile you want to switch to.
   - If you want to use the "Change WSR profile by voice command" then you need to edit the text contained within the brackets in the "When I say" field of the command. By default "When I say" reads "Change Recognition Profile to [one; two; three]. The manual calls this bracket portion a "dynamic command section." You just need to change the "one," "two," and "three" text entries to exactly match the names of the profiles you want to possibly switch to using voice commands. A minimum of one profile name is needed to make the command function (and remove the brackets for this case), and I don't know if there's a maximum limit to the number of profiles options you can provide VA. Note that one entry would look like `Change Recognition Profile to Profile1` and 2 entries would like like `Change Recognition Profile to [Profile1; Profile2]`. Note that the last entry when multiple options are entered needs to NOT contain a semicolon after the entry (again, read the manual). 
9. Profit!

**BE ADVISED. If you try to change WSR profiles with VA while the Windows Speech Properties window is open (see above image) you will receive confirmation from VA that the switch occurred but it will not be implemented by Windows. The Windows Speech Properties window must be closed for the profile change to take effect.**

## Help I have issues!
First and foremost, **[read the VA manual](http://voiceattack.com/VoiceAttackHelp.pdf)**. Yes it's long but it covers most of what is needed for you to understand and use VoiceAttack. Plus it covers more advanced stuff which is great to know so you can do other super cool things. 

If you are having problems with the VA software itself there is a dedicated [VoiceAttack User Forum](http://voiceattack.com/SMF/index.php) where you may seek help. The community is active and full of dedicated users who will help you with your general VA issues. Plus it's a great place to learn more about VA so you can do other super cool things as well as check out profiles and commands that other users have shared. 

If you are having problems specifically with the VA.Change-WSR-Profile then head over to the VoiceAttack User Forum, check out the "Issues" section to get an idea for how to provide enough information to request assistance, and then post to the "VA.Change-WSR-Profile" thread within the "Profiles, Commands and Plugins" section. 

## Full Disclosure
I am one of the moderators on the VoiceAttack User Forums, and I receive no benefits from the use or promotion of the VoiceAttack software. 
