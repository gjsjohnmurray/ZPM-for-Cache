## Prerequisites
Make sure you have a standard Caché instance for installation 
and you have SYSTEM access rights
## Installation 
Clone/git pull the repo into any local directory  
```
git https://github.com/isc-at/ZPM-for-Cache.git  
```
There is no docker and no automatic installation   
So some typing is required   
The installation rus in 2 phases   
- adding sone system settings   
- installing ZPM as on IRIS   

Open a terminal session like this
```
USER>set dir= <your local download directory>
USER>set prep="\src\%zrcc.xml"
USER>do $system.OBJ.Load(dir_prep,"ck")
```
You may get a similar output
```
Load started on 11/27/2022 23:02:48
Loading file C:\InterSystems\Cache\mgr\Temp\src\%zrcc.xml as xml
Imported routine: %zrcc.MAC
Compiling routine : %zrcc.mac
Load finished successfully.
```
now you run the setup with the 2nd xml in the package
```
%SYS>set xml="\src\ZPMcache.xml"
%SYS>do prepare^%zrcc(dir_xml)
 
Load started on 11/27/2022 23:07:10
Loading file C:\InterSystems\Cache\mgr\Temp\src\ZPMcache.xml as xml
. . . . . 
Compiling 10 classes, using 4 worker jobs
Compiling routine : %zrcc.mac
Load finished successfully.
 
Ready for ZPM installation
```
Now just do it
``` 
%SYS>d ^%zrcc
 
Load started on 11/27/2022 23:08:49
Loading file C:\InterSystems\Cache\mgr\Temp\2hVAs2eyWpWMyA.xml as xml
Imported class: %ZPM.Installer
Compiling class %ZPM.Installer
Compiling routine %ZPM.Installer.1
Extract package
Install ZPM
. . . . . many lines
ERROR #6301: SAX XML Parser Error: Line: 2 Offset: 39 This does not appear   
to be a Cache exported file, unable to import.
> ERROR #5090: An error has occurred while creating projection %ZPM.Installer:Reference.
Detected 1 errors during load.
 
IGNORE previous Error Messages
caused by a bad module.xml file in ZPM repo
 
All done, ready for use
 
%SYS>zpm
 
=============================================================================
|| Welcome to the Package Manager Shell (ZPM).                             ||
|| Enter q/quit to exit the shell. Enter ?/help to view available commands ||
=============================================================================
zpm:%SYS>search

```

And now you may use ZPM on Caché   
This is not tested in detail and just a prototype.
Issues and Pull Requsts ae welcome

I was waiting long to see this but now I decided
to make a 2022 birthday gift to myself. 
 
