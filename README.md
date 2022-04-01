# AutoADB-ScrCpy

Auto ADB for ScrCpy Setting Up Documentation for Windows

As an Android Developer ScrCpy is Very Usefull Application. I have been using scrcpy for a long time to test the applications in real devices and scrcpy let you do it without holding the device on your hand to control it.

It was built by Romain Vimont


The flow goes like this :

- Connect the device
- Fire up a terminal/cmd and run scrcpy
- Your device screen is now mirrored in a window and let you control the device.
- Limitations of this setup

Flaws in the Setup
I need to run the command scrcpy every time a device is connected, also need to maintain that terminal session.

Simply running the command scrcpy works great if only a single device is connected. In case of multiple devices connected, we have to obtain the serial of each device by using adb devices, then use scrcpy -s device_serial for each device.


in practice, the scene we encounter is often, such as going to a bathroom or going downstairs to go to a courier, and then re-opening the scrcpy reconnection after returning, which is a more tedious thing, how to automatically reconnect scrcpy when re-approaching away from the connected computer? the answer is: AutoAdb 
Auto ADB is made by the RUST language.

What needs DIY is to compile and run AutoAdb by yourself 
AutoADB does not have a proper Documentation guide For this process. So i thought to make one.

Tools Needed 
1. ScrCpy

- Windows: [Click to Download][direct-win64]
	
2. Auto ADB
3. RUST


## How to Setup AutoADB for Windows

<details>
	<summary> <h2> Step 1 </h2> </summary>
<p align="center">

Step 1
  
First Get the Rust Language for your Windows

https://www.rust-lang.org/tools/install

Download and Install Rust, According to your Computer Architecture 32 or 64bit.

or else If you're willing to install this on the Winsows Subsystem for Linux (WSL)  you can Use this Code 
	
	curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
	
Next we have to make sure RUST is installed correctly for that, open a shell and enter this line:
	
	$ rustc --version
	
![rustc](https://user-images.githubusercontent.com/64683688/160978976-a51934b2-55ba-4d47-ad5b-59be501d79c5.gif)

                     
</p>
</details>
                     
----

<details>
	<summary> <h2> Step 2 </h2> </summary>
<p align="center">
	
Step 2

After Installing the Rust Download the AutoADB Repo

https://github.com/rom1v/autoadb

![DownloadAutoADB](https://user-images.githubusercontent.com/64683688/160541520-bb24aeb8-016a-4194-96eb-a299df36ea81.gif)
	
Extract the File to a Proper Location
	
Here I'm Extracting the file to 
	
	C:\
	
Now upto part 2 is done completely
                     
</p>
</details>
                     
----

<details>
	<summary> <h2> Step 3 </h2> </summary>
<p align="center">

Now we are Going to Compile and Build the Extracted File which is made with RUST 
	
Now open 
	Powershell or CMD

Then Navigate to the Extracted File Location within the Terminal
`
	pushd C:\autoadb-master

then Run this Command to begin the  Process
	
	cargo build --release
	
![Compile](https://user-images.githubusercontent.com/64683688/160646585-8ed88580-88eb-4318-a896-6b6cb8f0e2cf.gif)

after that
Hope you can see a folder named Target Is Created
	

	
\target\release
	

there's a Application named autoadb.exe

Okay if You have this you have completely Done all the Step Upto Now.
	

</p>
</details>
                     
----

<details>
	<summary> <h2> Step 4 </h2> </summary>
<p align="center">
	
	STEP 4

So now you have to add this application as a Path variable

![PathVariableLocation](https://user-images.githubusercontent.com/64683688/160341895-b9fdaad9-a91a-4363-82ca-13120f032944.gif)

Add the Extracted root folder location of autoadb to the Path

![2 PathVariableAdding](https://user-images.githubusercontent.com/64683688/160344582-fff3ddf2-8f69-40e2-a3b1-2e8166cc5162.gif)

Lets Check whether Auto ADB is Working Succesfully

```
autoadb scrcpy -s {}
```
If it's Working Correctly You are Done!

Proceed from Here For Bonus Steps

If you want this to run as a Background Process when Logged into the Windows
	1. Create a Bat File
	2. Create a VBS Script

## Step 4

First You Have to Create a Batch File

For that Open the NotePad and Type this Code

```
@echo off
autoadb.exe scrcpy.exe -s {}
```

Save this as a .bat file. 
Here I'm Saving it as auto.bat

Run this and check whether the Batch file we created is working Fine.

If you willing to run the Batch file when the windows Startup Simply put the Batch file into the “All Users” Startup folder

To access the “All Users” Startup folder in Windows 10/11, 
open the Run dialog box (Windows Key + R), 
then type 

```
shell:common startup 
```

and click OK. 
When Folder Opens Drag and Drop the Batch File


So always opening a CMD is really Annoying So that I thought It's Better to Run this as a Hidden Background Service (to Hide and Run this)
	
Then you don't want to keep a CMD window open, so build a vbs script to hide the window, file name:

After putting this vbs into the win automatic startup path, it seems that after opening the computer every day, the mobile phone screen is not automatically projected to the computer, so the Quikeer gadget is enabled, which is manually run once a day, and then it will be automatically connected as long as you return to the computer
	
## Step 5

Then you have to Make the VBS Script File

For that Open the NotePad and Type this Code
	
```
Set WshShell = CreateObject("WScript.Shell") 
WshShell.Run chr(34) & "C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup\auto.bat" & Chr(34), 0
Set WshShell = Nothing
```

Now you are done. 
	
Leave a Comment if you Encountered Any kind of a Problem


Downloads

[direct-win64]: https://github.com/Genymobile/scrcpy/releases/download/v1.23/scrcpy-win64-v1.23.zip
	
