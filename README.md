##HoiPolloi People viewer v.0.4  
_by Michel Clasquin <clasqm@mweb.co.za>_

Initially developed and tested on BeOS 5.03  
This version specially made for Zeta 1.0  
Released into the Public Domain, September 2005  

Since the release of Be, Inc's People file format, there have been a number of utilities produced to extend its functionality. People.iro is really just People with an icon-colouring utility. BlueCult shows a reduced amount of information, but adds a cellphone field of its own. DeeperPeople and MrPeeps vastly extend the amount of information a Person file can store. There have been others, but they seem no longer downloadable. With these five put together, a Person file can now have 50 attributes hanging off it!

I like to use them for different purposes. For example, why does MrPeeps (1.1.0 beta 3) not use the country field? We don't all live in America! DeeperPeople has both home and work country fields. BlueCult is useful for a quick lookup of an email address. And so on.

Unfortunately, incompatibilities have crept in over the years. If you entered a cell phone number in BlueCult, DeeperPeople will show it, but MrPeeps will not. If you entered your ICQ address in Surgeon, neither DP nor MP will even know it is there. HoiPolloi shows you all the information contained in these various programs, and attempts to harmonise some of the more glaring incompatibilities by copying data between competing attributes.

Both Surgeon and MrPeeps had the bright idea of storing something inside the Person file itself. But while Surgeon places text Comments in there, MrPeeps stuffs in a JPG. Editing such a file with an image in it in Surgeon, or even just opening it in Surgeon and clicking on the Notes tab, instantly makes the JPG unreadable.  You should use either one of these programs, but not both. Considering that Surgeon is abandonware whle MrPeeps is in active development and has its own notes facility, the choice seems clear.

On the brighter side, with the MrPeeps setup you can use your favourite graphic ---> icon Tracker Add-on to give your People files recognisable faces! I have included my own mug with the program. Go ahead, drag and drop me on HoiPolloi! Also included is Mr Test Person, a fictional character with ALL fields filled in, so that you can test out the program.

The other question that HoiPolloi tries to address is, what can you actually do with those People files? Yes, in People you can start an e-mail or go straight to a website with a single click. But some of us still write letters and faxes. Why can't you drop a Person onto a blank document and get the postal address all formatted up there on the letterhead? With HoiPolloi, it's still not quite that easy, but at least it's just a few clicks away. Just load your person and click on Extractor . . . While every other Person-compatible application is an alternative input method, HoiPolloi is concerned with output. Mind you, that is not entirely true of the bundled utilities (see below).

###INSTALLATION:

Unzip the distribution file into /boot/apps/or anywhere you like as long as the full pathname does not contain spaces. Note that both BeOS (R5.03) and Zeta (1.0) binaries are included. You can delete the one you don't need and rename the remaining one to just HoiPolloi, if you like. Make a symlink to the HoiPolloi binary into the BeOS or Zeta menu in the normal way.

For the utilities to work, a link called HoiPolloi needs to be in the Search Path. Open a Terminal and enter the following command from within HoiPolloi's directory

    ln -s HoiPolloi-R5 ~/config/bin/HoiPolloi

or

    ln -s HoiPolloi-Zeta ~/config/bin/HoiPolloi


All this may be automated in a later version if the demand is there!

###USAGE:

Drop a Person file anywhere on the HoiPolloi window and choose the program whose info you want to see displayed. An image will only be displayed if you have added one with Mr Peeps. These images are NOT compatible with Surgeon's Comments, so don't even try. Only those categories for which there is an entry will be displayed.

###THE BUTTONS:

The shortcut keys on each button work with either ALT or CTRL, depending on how your system is set up.

***REFRESH*** will reload the Person file after you have edited it with an external program. However, if you are coming from EXTRACTOR (see below) it will simply redisplay the data without reloading, to speed things up. A Refresh is done automatically after you use HARMONISE (see below).

***COPY*** will copy the contents, exactly as you see them, to the clipboard.

***EXPORT*** will save the contents, exactly as you see them, to a text file.

***HARMONISE*** will attempt to reconcile the different methods that the five supported apps use to store information. This uses a wizard-type interface, in which you will be asked which of two conflicting entries you want to use. HoiPolloi's HARMONISE function currently addresses the following incompatibilities:

***Cell phone:***  BlueCult and DeeperPeople store this in META:cphone, while MrPeeps stores it in META:cell. In this and the next two cases, you will be asked whether you want to use the MrPeeps value or the other one.

***ICQ:*** DeeperPeople and MrPeeps store this in META:icq, while Surgeon stores it in META:icquin.

Position. DeeperPeople uses META:wposition, while MrPeeps uses META:position. 

***Name:*** DeeperPeople uniquely splits the name into first and last names, and attempts to reconstruct the whole name from that. It also creates the Person file's filename from this information. Unfortunately, it doesn't do it the other way round! You could end up with a Person named "John Smith CHANGE-ME". To prevent DP from changing the Name field (and the filename), first and last names are automatically generated and inserted without user intervention if either of these DP fields are empty (i.e. if they were created in another program). Any CHANGE-ME in the filename is also automatically deleted. If the name is still screwed up after this, use the NameSwitcher utility (see below) to edit it.

***Notes and Comments:*** If a Surgeon Comment is detected, and the DeeperPeople/MrPeeps Notes field is empty, the surgeon note will be moved to the DP/MP field after the user OK's the change. If the DP/MP field is NOT empty, the Comment will appended to the DP/MP Note. In either case, the Surgeon Comment is wiped out and the Person can now take a MP image.

There is one issue that HARMONISE does not address. MrPeeps and DeeperPeople use the same attribute for Notes. But while MP can handle long multi-line notes gracefully, if you try open that Person in DP, the lines get concatenated (squashed together). If you try to edit the Note in DP, it will be truncated (cut off)! Nothing I can do about that, sorry. Personally, I work around that by using DP for new entries (for the country entries, but see the CountryAdder utility, below) and MP ever afterwards for the notes.

Harmonise has been debugged extensively, but it is almost impossible to foresee every possible situation. You might want to backup your People before you run it.

***EXTRACTOR*** will launch a utility that extracts the data in specific formats and allows you to copy just that format to the clipboard or save it to a file. For example, you can have the Person's home or business postal address extracted and ready to be pasted into your word processor, in which you are writing a letter to that person.  Current extractions are:
Home address (no labels)
Spouse's address (no labels)
Work address (no labels)
Assistant's address (no labels)
All Internet related data
All telephone-related data
Personal data
Notes
If you can think of more combinations of data that would be useful, let me know.There is some space left on the Extractor screen. Once you are familiar with Extractor, go ahead and explore the Associated Actions button. This is set of shortcuts in "wizard" style to some things you could do with the Copy and Export functions as well.

***QUIT*** . . . well, it quits, obviously!

***HELP*** - You can also recall the HELP screen that shows on startup at any time with either ALT-H or CTRL-H, again, depending on your system setup. Help is disabled in Extractor.

###ABOUT THE EXTRA UTILITIES

You would normally start these from the HoiPolloi menu, but you can run them from Terminal if you like. Just type "HoiPolloi help" for instructions. By default, all the utilities except the "wizards" will start up with the person you currently have loaded in HoiPolloi. If that was not the intention, just drag and drop a new person onto the utility's dropzone.

***ADDRESSER*** is a very minimal, early version of what has become HoiPolloi: it accepts dropped files and parses the home address ready for copying to clipboard. Still useful if you only use People to handle handle your People files.

***COUNTRY ADDER*** is a small app that tries to make up for the main deficiency in MrPeeps (at the time of writing - maybe DarkWyrm will repent and put them back ... ); the fact that it does not use either the Home Address Country or the Work Address Country fields. With CountryAdder you can add these easily just by dropping the Person onto its dropzone.This utility is multilingual in the sense that you don't need to enter the name of the country in English. CountryAdder can also change the country of an existing Person. Hey, this is the age of globalisation, people move around . . .

***E-MAIL 2 PEOPLE*** will scan all e-mail on your system, extract names and e-mail addresses, and then create appropriate People files in a special folder to avoid overwriting any existing People. You can then move them into the regular People directory. The special folder lives in /var/tmp and will be deleted at the next boot.

***HOME MERGER:*** You have a very detailed Person file for your best buddy. You also have one for his girlfriend, but it only has her phone number in it. She is moving in with him. With HomeMerger you can paste all his home address details into her Person file with two drag and drops and a single click on a button. If you mixed up the drag and drop and have them the wrong way round, you can switch them with a button press as well. 

***NAME SWITCHER:*** So you have all your People files listed in the format "John Smith". One day, you realise that you would really prefer "Smith, John", "Mr John Smith" or even "Mr Smith, John".  You change the filename. Then, one day you run DeeperPeople and find that the filename has been changed back! NameSwitcher gives you the choice. NS was designed for western names (firstname familyname) and will not work well with Asian (familyname firstname) style names. Also, if you have lots of friends in Sri Lanka or Samoa, whose names are seriously L O N G, then NS will work, but it won't look pretty!

***NEW PERSON WIZARD:*** Just an alternative interface to create new People files, both for business and personal use. The resulting files are optimised for Extractor and are already Harmonised. If you supply the name of an existing Person, the old file will be overwritten without warning! Apart from the inital alert, this interface is entirely keyboardable.

***WORK MERGER:*** Just like HomeMerger, except that it copies the work address.

###NOTES

The "Associated Actions" Button in Extractor needs to make some assumptions about what external software is on your system and where it is situated. These are:
Gobe Productive 2.0
StyledEdit
Firefox
Beam

The default directories used here are as found on a stock Zeta 1.0 installation

If you know your way around BASIC code and have a working YAB installation, you can open up the HoiPolloi source code in a text editor and edit the first four global variables:
texteditor$ = "/boot/zeta/apps/StyledEdit"
wordprocessor$= "\"/boot/apps/Office/Gobe Productive 2.0/Gobe Productive\""
mailapp$= "/boot/apps/Internet/Beam/Beam"
webapp$ = "/boot/apps/Internet/Firefox/Firefox"

It should be possible to change these and still have everything work. e.g to open a URL in NetPositive or Mozilla instead of Firefox. Note the escape code \" for any pathname that includes spaces.

A different approach is to create symlinks to programs that are on your systems in the directories listed above. For example, if you use NetPositive, you can create the directory /boot/apps/Internet/Firefox and then place inside it a link to NetPositive named "Firefox".

###KNOWN BUGS

HoiPolloi may crash on exit, especially if the last Person loaded contained an image. Zeta seems less finicky in this regard than BeOS. Apart from crashing on exit, though, it is fine during normal use. <famous last words ...>

