# crDroid Merge Tool

## Description
An automated tool that makes merging ASB tag and LineageOS forks easier.

How does it work?
A script goes through defined set of git repositories and tries to merge upstream branch. Earlier, I have observed missing merges and found out manual merging to be a pain in the ass, thus decided to create this script.

## Usage
At the first run script will try to detect android sources root, it will succeed as long as you clone this repository inside the root (even in subfolders).
Otherwise, you will be asked to manually type in sources location (TAB completion is supported). Entered path will be saved and used for future uses.

Main menu allows you to use three functionalities:
1. **Sync new ASB tag from Google (optionally repopick LineageOS ASB topic)**  
	It will checkout repo manifest to latest origin and modify it to sync typed-in revision. Then sync. Optionally you can choose to repopick LineageOS ASB topic.
2. **Merge new ASB tag**  
	It will then ask you what revision you want to merge, then after a confirmation automatic merge will happen and eventually show every repo that changed. Merge conflicts will be displayed, if any.
3. **Merge LineageOS forks**  
	Same as 2. but without asking for revision. This option tracks branch lineage-18.1.
4. **Push modified repos**  
	The script saves all modified repos in merge_succeeded/failed. It confirms whether all conflicts were solved. After your consent all modified repos will be pushed to crDroid repository.

## Usecases

* **Sync with LineageOS trees** - performed to keep up with LineageOS changes
	* Merge lineage forks (**3**)
	* *(optional)* Test build
	* Push modified repos (**4**)
* **Test new ASB tag** - only for testing purposes of new ASB tag
	* Sync ASB tag from google and repopick LineageOS gerrit topic (**1**)
	* Merge new ASB tag (**2**)
	* Build
* **Bump crDroid to new ASB tag** - after LineageOS ASB tag merge
	* Sync new ASB tag from google (**1**)
	* Merge new ASB tag (**2**)
	* Merge LineageOS forks (**3**)
	* Build & test boot
	* Push modified repos (**4**)

## Copyright
Created by:
* Andrzej Perczak (xNombre)
