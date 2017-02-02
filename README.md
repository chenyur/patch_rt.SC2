# patch_rt.SC2
Replace your patch_rt.mpq to use Starcraft 2 default hotkeys with Broodwar

Hope this makes starting/returning to Broodwar easier from SC2!

## Usage
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

## How to create your own patch_rt.mpq with custom hotkeys
TODO

## Roadmap

- [x] v0.1
* Original patch_rt.mpq from Broodwar 1.16.1
* Original English (Locale ID 0/neutral) stat_txt.tbl extracted from patch_rt.mpq
* Original stat_txt.txt decompiled with PyTBL

- [x] v0.2
* Background & Usage

- [x] v0.3
* A guide on how to edit the hotkeys yourself, in 2017

- [ ] v0.9
* List of hotkey changes

- [ ] v1.0
* Patched patch_rt.mpq, stat_txt.tbl and stat_txt.txt
* Testing in game

- [ ] v1.1
* Variations. e.g. Replacing (S)courge

- [ ] v2.0
* Broodwar 1.17?
