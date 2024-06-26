---
title: "Funbridge Deal Autocollection"
date: 2023-01-05
Author: "Arnold Yang"
categories: ["Miscellaneous"]
summary: "This is a tutorial on how to use the funbridge autocollection bot to autocollect daily deals on Windows and Ubuntu Linux."
weight: -5
ShowCodeCopyButtons: True
ShowPostNavLinks: True
---

[Funbridge](https://www.funbridge.com/) is a great website to practice and play bridge on. However, the free version of it gives you a limited amount of deals to play and limits many things you can do. In this tutorial, we will go over how you can automatically collect daily free deals.

## Materials
First, you will need git, python, and selenium.
### Ubuntu
```
sudo apt install python3
sudo apt install git
sudo apt install python3-pip
pip install selenium
```

### Windows
To install python on Windows you can visit the Microsoft store, or set it up through the python website.
You can download git from [https://git-scm.com/download/win](https://git-scm.com/download/win).
You may also need to figure out how to install pip for windows seperately.
To install selenium, you can just open Powershell and run:
`pip install selenium`

## Geting the Script

After installing, git you can clone the script from this repo: [https://github.com/Poarthan/funbridge-autocollect-deals](https://github.com/Poarthan/funbridge-autocollect-deals)
```
git clone https://github.com/Poarthan/funbridge-autocollect-deals
```

## Editing the script
The last thing you need to do before running it is to edit the script to put your username and password in the spots at the bottom where it says: `your_username_or_email` and `your_password`. The script was designed for multiple funbridge accounts, therefore, it has an extra redundancy built in.

Then you should be able to run the script with:
```
python collection.py
```

To run the script for multiple accounts copy the last few lines and paste them above `exit()` and change the username and password to the login details for the second account:
```
result=collect_deals("your_username_or_email", "your_password")
if not result:
    time.sleep(5)
    collect_deals("your_username_or_email", "your_password")
time.sleep(5)
```

The script will run each account twice so that if the account is already signed in, the script will sign it out. Funbridge will automatically sign you back in when you use Funbridge later, so don't worry about extra work.

## Running the script daily
### Linux Cron Jobs
On Linux, you can just run `crontab -e` to edit a cronjob

Then add the line below to the bottom of the file, if you don't know where your python path is run `whereis python` and if you don't know where the collection python script is, go to the directory that it is and run `pwd`:
```
0 3-5 * * * /path-to-python/python /path-to-script/collection.py
```
This will run your script 3 times at 3 AM, 4 AM, and 5 AM, this is because every time the collection happens it will have to be a little over 24 hours since the last one, and currently there is no good way to do that other than adding to the script which may happen later, but for now it will just run the script 3 times every day, so it may miss out a day every week. You can edit this configuration to run more often so that it guarantees daily deal collection.

### Windows Task Scheduler
From my experience it is best to use a .bat file to run this script so
```
C:\path-to-python\python.exe C:\path-to-funbridge-autocollect-deals\funbridge-autocollect-deals\collection.py
```

Then open the task scheduler, and set triggers to run daily at a time you want every day like 3 AM, in advanced settings put repeat task every 5 minutes for 30 minutes, and enable stop all running tasks at the end of duration. Set actions to run the batch file, so just type the path of the batch file, should look something like this `C:\path-batch-file\some-name.bat`. These settings will allow it to run daily, and repeat a few times to have the problem of having to collect deals a little after 24 hours be less impactful. about every 13 or 14 days will this miss out on a day.

![Task Scheduler Daily Trigger](/uploads/task-scheduler-trigger.jpg)

You can suggest any changes you would like to see, or any feature that you want added here: [https://github.com/Poarthan/funbridge-autocollect-deals/issues](https://github.com/Poarthan/funbridge-autocollect-deals/issues)
