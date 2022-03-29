# AutoADB-ScrCpy
Auto ADB Setting Up Documentation for ScrCpy 


## How to Setup AutoADB for Windows

Tools Needed 
1. ScrCpy

[direct-win64]: https://github.com/Genymobile/scrcpy/releases/download/v1.23/scrcpy-win64-v1.23.zip

	- Windows: [Click to Download][direct-win64]
	
2. Auto ADB
3. RUST

<details>
	<summary> <h2> Step 1 </h2> </summary>
<p align="center">

Step 1
  
First Download Rust for your Windows

https://www.rust-lang.org/tools/install

Download According to your Computer Architecture 32 or 64bit And Install It

or else If you're willing to install this on the WSL you can Use this Code 

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
                     
</p>
</details>
                     
----

<details>
	<summary> <h2> Step 1 </h2> </summary>
<p align="center">
	
Step 2

Download the Repo
https://github.com/rom1v/autoadb

open Powershell
and 
type
`
pushd C:\Users\wdedw\Downloads\Compressed\autoadb-master

file extracted location

then 
type
cargo build --release

after that
Hope you can see a folder named Target
\target\release

there's a Application named autoadb.exe

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
## Step 5

Then you have to Make the VBS Script File

For that Open the NotePad and Type this Code
```
Set WshShell = CreateObject("WScript.Shell") 
WshShell.Run chr(34) & "C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup\auto.bat" & Chr(34), 0
Set WshShell = Nothing
```




