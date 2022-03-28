# AutoADB-ScrCpy
ScrCpy Setting Up Documentation of AutoADB for Windows 

## How to Setup AutoADB for Windows

SCRCPY

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

## Step 4

