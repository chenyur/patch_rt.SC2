# patch_rt.SC2
Replace your patch_rt.mpq to use Starcraft 2 default hotkeys with Broodwar

Hope this makes starting/returning to Broodwar easier from SC2!

## Quick guide
1. Download SC2.patch_rt.mpq
2. Rename it patch_rt.mpq
3. Backup your existing patch_rt.mpq in Broodwar folder
4. Replace old patch_rt.mpq with the one you just downloaded

Revert to your backup if anything breaks!

## Background
The hotkey settings for Broodwar are stored in stat_txt.tbl, which itself is compressed within patch_rt.mpq

Only units that exist in SC2 will have its hotkey changed

Any conflicts will be noted in the change list

Initially intended to work with English Broodwar version 1.16.1

## How to create your own patch_rt.mpq with custom hotkeys in 2017
There are numerous guides on how to do this with WinMPQ 1.66 and Tblpad, but I've had no luck with them

1. Download PyMS from https://github.com/poiuyqwert/PyMS
  * Install Python if you don't have it installed. 
  * To check, open up cmd/terminal and type python
  * I have Python 2.7.8 on a Windows 8.1 machine
2. Download WinMPQ 3.5.1.188 http://www.zezula.net/en/mpq/download.html
  * You also need the listfile, available on the same page, extract it
3. Make a working copy of original patch_rt.mpq in the **same folder** as PyMS
  * Open patch_rt.mpq with WinMPQ, click Add Listfile, choose Starcraft BW.txt
  * On the left choose the rez folder and find stat_txt.tbl in the locale you want (Neutral is English)
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
  > Since e isn't a part of "pylon", we can write (e) to indicate its new hotkey  
  > Thus, the line becomes "e<1>Warp in Pylon <3>(E)<0>"  

6. When you are done, save, and recompile the txt into tbl
  ```
  python PyTBL.pyw -c stat_txt.txt
  ```
7. Simply drag the tbl file back into the rez folder in WinMPQ to replace it
8. Replace patch_rt.mpq with the one you have just created and launch Broodwar to test your change in game!

## Roadmap

- [x] v0.1
* Original patch_rt.mpq from Broodwar 1.16.1
* Original English (Locale ID 0/neutral) stat_txt.tbl extracted from patch_rt.mpq
* Original stat_txt.txt decompiled with PyTBL

- [x] v0.2
* Background & Usage

- [x] v0.3
* A guide on how to edit the hotkeys yourself,

- [ ] v0.9
* List of hotkey changes

- [ ] v1.0
* Patched patch_rt.mpq, stat_txt.tbl and stat_txt.txt
* Testing in game

- [ ] v1.1
* Variations. e.g. Replacing (S)courge

- [ ] v2.0
* Broodwar 1.17?
