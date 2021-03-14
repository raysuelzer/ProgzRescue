# ProgzRescue
Repository to help with archival and recovery of AOL Progs from the 1990s

At the moment, I am simply posting links to zip files that have been extracted from metadata files from the wayback machine.  I am hoping the community will use these links to determine which files are of interest for archiving for "AO Scene" community.  

I will open source the extractor I am using, however, it is very crude at the moment and relies upon downloading warc cdx files and placing them in hard coded directories. 


As of now there are three files in the archived-urls directory

- found-angelfire-files.txt

This contains a list of every zip file returning 200 status contained in the https://archive.org/details/archiveteam_angelfire cdx files.  Note: some of these links may still be active, but probably 80% of them are dead, but are archived in the wayback machine.  Pasting the URL in the Wayback machine should allow the file to be downloaded.  Perhaps someone can write a script that will download these files from the wayback machine programatically.

- found-fortune-city-skyscraper-files.txt

As above, these are .zip files from fortunecity.com/skyscraper/** urls. Note: I have not yet pulled data for any other directories, we need to find a list of the other directories. 

- found-geocities-silicon-valley-files.txt

Same as above, but for geocities.com/SiliconValley/**  There are clearing hundreds more "cities" that need to be searched. 


## How to do this yourself for certain domains? 

It's pretty simple, you will need use the following URL to download a list of all of the files contained in a domain / prefix on the wayback machine.  Then, you need to parse this json file to look for the "application/zip" filetype. I cannot figure out a way to filter just to certain mimetypes. 

The Archive.org URL (likely an unsupported API) is below

`http://web.archive.org/web/timemap?url=http%3A%2F%2Ffortunecity.com%2Fskyscraper&matchType=prefix&collapse=urlkey&output=json&fl=original%2Cmimetype%2C&filter=!statuscode%3A%5B45%5D..&limit=100000&_=1615693790712`

This will pull 100,000 results from `http://fortunecity.com/skyscrapper`  (note the URL encoding).
I found there is no upper bound to the limit param. But, tread lightly. 15 million seems to be okay. 

Once you have that JSON downloaded, you can parse the data however you see fit.  I recommened reading the file line by line and only keepling lines which contain 'application/zip' becuase loading the entire file into memory is not ideal. 



