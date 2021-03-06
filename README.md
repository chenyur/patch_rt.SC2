# patch_rt.SC2
Replace your patch_rt.mpq to use Starcraft 2 default hotkeys with Broodwar

Hope this makes starting/returning to Broodwar easier from SC2!

## Quick guide
1. Download patch_rt.mpq from this page
2. Backup your existing patch_rt.mpq in Broodwar folder
3. Replace old patch_rt.mpq with the one you just downloaded

Revert to your backup if anything breaks!

## Background
The hotkey settings for Broodwar are stored in stat_txt.tbl, which itself is compressed within patch_rt.mpq

Only units that exist in SC2 will have its hotkey changed

Any conflicts will be noted in the change list

Initially intended to work with English Broodwar version 1.16.1

## How to create your own patch_rt.mpq with custom hotkeys in 2017
There are numerous guides on how to do this with WinMPQ 1.66 and Tblpad, but I've had ~~no luck with them~~ okay WinMPQ 1.66 works with listfile, but since I have Chinese and Japanese installed on my computer Tblpad is no good

1. Download PyMS from https://github.com/poiuyqwert/PyMS
  * Install Python if you don't have it installed. 
  * To check, open up cmd/terminal and type python
  * I have Python 2.7.8 on a Windows 8.1 machine
  * You might need to install PIL for your version of python http://pythonmac.org/packages/py25-fat/index.html
2. Download WinMPQ from http://sfsrealm.hopto.org/dwnload.html, don't forget to install all dependancies, I use the VB6 version
  * You also need the listfile if you can't see filenames, available on this http://www.zezula.net/en/mpq/download.html page, extract it - The WinMPQ version from this page does not work for me
3. Make a working copy of original patch_rt.mpq in the **same folder** as PyMS
  * Open patch_rt.mpq with WinMPQ, add listfile from options, choose Starcraft BW.txt
  * Find rez\stat_txt.tbl, in the locale you need (if there are multiple, Neutral is English)
  * Right click, extract and move the tbl file to the PyMS folder
4. Open up a cmd/terminal, move to the PyMS folder and use it to decompile the tbl file using commands below
  * Details can be found at http://poiuyqwert.byethost22.com/PyMSDocs/PyTBL.html
    
    ```
    # replace the path below with your path to the PyMS folder
    cd C:\Users\username\Downloads\PyMS-master
    python PyTBL.pyw -d stat_txt.tbl
    ```
5. Now you should see a stat_txt.txt file in the same folder, open it with wordpad or your favourite text editor

  > Suppose you want to make "Warp in Pylon" hotkey e instead of p  
  > find the line that reads "p<1>Warp in <3>P<1>ylon<0>"  
  > The first p represents its hotkey, but it is invisible in the game, <1> makes all text following it white, while <3> makes it yellow (to indicate that it's a hotkey)  
  > Since e isn't a part of "pylon", we can write (E) to indicate its new hotkey  
  > Thus, the line becomes "e<1>Warp in Pylon <3>(E)<0>" 

6. When you are done, save, and recompile the txt into tbl
  ```
  python PyTBL.pyw -c stat_txt.txt
  ```
7. Add the tbl file in WinMPQ to replace it and **close WinMPQ**, when prompted input rez\
8. Replace patch_rt.mpq with the one you have just created and launch Broodwar to test your change in game!

![screenshot](http://puu.sh/tKUlx/1ddf91795f.png)

## Changes

- [x] v0.1
* Original patch_rt.mpq from Broodwar 1.16.1
* Original English (Locale ID 0/neutral) stat_txt.tbl extracted from patch_rt.mpq
* Original stat_txt.txt decompiled with PyTBL

- [x] v0.2
* Background & Usage

- [x] v0.3
* A guide on how to edit the hotkeys yourself

- [x] v0.9
* List of hotkey changes

- [x] v1.0
* Patched patch_rt.mpq, stat_txt.tbl and stat_txt.txt
* Testing in game

- [x] v1.0.1
* Mutalisk hotkey M -> T

- [ ] v1.1
* Variations. e.g. Replacing (S)courge

- [ ] v2.0
* Broodwar 1.17?
