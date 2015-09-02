Hello!

I recently got a pebble time and was disappointed in what I could do with my iPhone. Until I found how to make scripts for activator so I could have COMPLETE control of my iphone from my pebble. This will be a tutorial for writing scripts for activator using soundcloud as an example.

&nbsp;

**What you will need:**

* A Pebble!

* A jailbroken iPhone

* Smartwatch+ (from cydia)

* Activator (comes with pebblesiri on cydia or search it)

* Activate Command (from cydia)

* SimulateTouch (from cydia)

* ByPass (optional but recommended; allows you to bypass password when executing activator commands; from cydia)

* AutoTouch IOS 7/8 (optional; used for finding pixel positions; from cydia)

&nbsp;

**Instructions:** (for soundcloud; This is written for iphone 5 please read "Using SimulateTouch" below if you have a different model):

1\. Make sure you have the smartwatch+ watchapp installed from pebble time app (if you get stuck on loading then download the version in smartwatch+ app under "Install Watchapps")

&nbsp;

2\. Go into settings on your iphone and scroll down to "Activate Command" (I recommend turning on "Show Titles" for easy identification on your pebble)

&nbsp;

3\. Name your command under "Title 1" and paste this into "Command 1"

    activator send com.bd452.bypass && activator send com.soundcloud.TouchApp && sleep 3 && stouch swipe 300 100 300 800 0.5 1 && sleep 2 && stouch touch 160 200 1 && sleep 1 && activator send libactivator.system.sleepbutton

* This code will bypass your passcode, open soundcloud, swipe down to load latest tracks, tap on the upmost track and then lock your device.

&nbsp;

4\. Then name your second command under "Title 2" and paste this into "Command 2" (this code closes soundcloud)

    activator send com.bd452.bypass && activator send libactivator.system.activate-switcher && sleep 2 && stouch swipe 20 200 20 20 0.2 1 && activator send libactivator.system.sleepbutton

* This code will bypass your passcode then open the multitask switcher and swipe up to remove soundcloud then lock your device

&nbsp;

5\. Then name your third command under "Title 3" and paste this into "Command 3" 

     activator send com.bd452.bypass && activator send com.soundcloud.TouchApp && sleep 1 && stouch touch 52 535 1 && sleep 1 && activator send libactivator.system.sleepbutton

* This code will bypass your passcode, open soundcloud then tap on the like button and lock your device. 

&nbsp;

6\. To bind these commands to smartwatch+ open smartwatch+ (cydia) app on your phone then go into activator screen, then choose the button you want to bind it to and select your command (it should be at the top if not scroll down till you see the "activate command" icon)

&nbsp;

7\. You are done! Now just go into smartwatch+ on your pebble, select activator, select the command you wish to run! To control the songs just go back to the music app installed on Pebble and use that to skip songs and adjust volume. If you have any problems please continue reading as I will explain how to write your own scripts for specific apps.

&nbsp;

**Explaining scripts:**

To start I am going to dissect some of the code above. Here is the code for opening soundcloud

     activator send com.bd452.bypass && activator send com.soundcloud.TouchApp && sleep 3 && stouch swipe 300 100 300 800 0.5 1 && sleep 2 && stouch touch 160 200 1 && sleep 1 && activator send libactivator.system.sleepbutton

&nbsp;

1\. ByPass

     activator send com.bd452.bypass

* This code is what we install ByPass for, this will bypass your passcode until the script is complete then lock your device

&nbsp;

2\. Waiting for completion

    &&

* This means that the next piece of the script will not run until the code before it runs successfully. You will want to use this between almost every command.

&nbsp;

3\. Standard activator command

     activator send com.soundcloud.TouchApp

* This command opens soundcloud. Almost every activator command will start with "activator send". I will explain where to find all the commands further down.

&nbsp;

4\. Sleeping

    sleep 3

* This is a command you will use a lot. This simply waits for a given amount of time (Seconds) before running the next piece of the script.

&nbsp;

5\. SimulateTouch

     stouch swipe 300 100 300 800 0.5 1

* This is one of the few commands that doesn't use "activator send" because it is custom (comes from simulatetouch, hence stouch). I will explain how to use this further down (if the soundcloud scripts above do not work it is because of this command)

&nbsp;

6\. Another standard command for locking

    activator send libactivator.system.sleepbutton

* This should look pretty straight forward, it simply locks your device. If you use bypass your device will automatically lock after a script is run but I include this so if the phone was unlocked it will lock on completion.

&nbsp;

**Finding Activator Commands:**

1\. Go to [this](http://junesiphone.com/actions/) site for a full list

2\. Remove all the slashes and colons from the command

For Example

    Activator://send/libactivator.system.sleepbutton

would be

    activator send libactivator.system.sleepbutton

3\. Use the command in your script!

&nbsp;

**Using SimulateTouch:**

Using SimulateTouch is a lot easier than you think! To simulate a touch simply write:

    stouch touch x y [Orientation]

* x is the x position of the pixel and y is the y position of the pixel. [Orientation]'s value is 1 for Portrait, 2 for UpsideDown, 3 if the homebutton is to the right and 4 if the homebutton is to the left.

&nbsp;

To simulate a swipe simply write:

     stouch swipe fromX fromY toX toY [Duration] [Orientation]

* fromX and fromY is where the swipe will start and toX and toY is where the swipe will end. [Duration]'s value is how long this swipe will take in seconds. [Orientation]'s value is 1 for Portrait, 2 for UpsideDown, 3 if the homebutton is to the right and 4 if the homebutton is to the left.

&nbsp;

To fix soundcloud script (for iphone that isn't a 5):

1. Find the position of the pixels for the top track and the follow button in soundcloud the using method below

2. Replace my "stouch" commands with your pixel values

3. If you get the values for your model of phone if you could post the script in the comments that would be awesome!

&nbsp;

To easily find the position of pixels:

1. Download AutoTouch from cydia.

2. Take a screenshot (press home and lock button) of the screen you want to use the touch command on.

3. Open AutoTouch, select "local", then hit the plus in the top right and select "new script"

4. Select "extensions" then select the "tap(x,y)" function

5. Select your photo and then tap where you want to know the pixel x and y

6. Use the value displayed at the top for your "stouch touch x y [Orientation]" command. This is how you will fix my soundcloud script (if you are using an iphone that is not a 5 or 5c).

&nbsp;

**Closing:**

Wow this got a lot bigger than I thought it was gonna be, hopefully you guys can make some good use of it!

I do have a couple closing notes.

* Smartwatch+ only supports 6 commands (3 buttons and the buttons being held) hopefully /u/robhh can add some sort of folder or group system so I can have my soundcloud commands in a "Music" folder with 6 commands.

* Using these scripts will require smartwatch+ to be open (like everything else smartwatch+ does)

* If you have any cool scripts you have made please feel free to post them in the comments!

