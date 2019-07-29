# PMC_App3_WebsiteBlocker

Python script created to block certain websites from being accessed at certain points of the day.

Currently has FB blocked between 3 and 4pm on laptop, for testing purposes.

Code created in pycharm with instruction from https://www.udemy.com/the-python-mega-course/learn/lecture/5163360#content . 

The architecture.. the script will open the hosts file within the system32 folder, add any applicable websites to the hosts file, and between the indicated hours within the script, those sites would be inaccessible. If outside those hours, the script would check to see if those sites are within the hosts file, and if so, would remove them.

So in the basic process of the steps to create:
  Architecture was provided
  Time was imported. Variables were created for the path to the hosts file (using 'r' to read the raw directory address), the redirect, and the list of websites to be blocked. Also, a while loop was input to test something being printed every 5 sec while 'true'.
  Datetime was imported. The while loop was expanded to print 'working hours' or 'not working hours' depending on the datetime.
  Next, the first part was created in detail. Basically, if the time was between x and x hours, the hosts file would be opened (r+ to read and write). The contents were put into a variable. A for loop would then run checking, if a website is in the content, it would pass, and if it wasn't, it would be written with the redirect variable.
  The second part is a bit trickier. If the hours are outside the working hours, the file would open the same, content variable the same, but the opened file would have seek(0) used to bring cursor to the top. Then for each line, the any method would be used to confirm if a website was present. If not, it will write the normal line. Anything after, truncate() would be used, indicating everything under would be removed. This basically creates a new hosts file, with the websites removed.
  Also, this uses time.sleep(5), so the while runs every 5 seconds, not every millisecond, which would suck. :)
  
Once created, the .py file had a 'w' added (website_blocker.pyw), so it would simply run when double clicked. Then the task scheduler was used, task was created to run this file at startup, and will show as a python proggy within task manager. Make sure to direct the Program/Script field to the pythonw.exe file, and the Add arguments field should be set to the actual file itself. Ensure quotations are input also.

Fun project, will need to dive deeper to find more uses for this. :)
