# JENKINS HANDS ON 

LAB2-JENKINS |
[LAB1-GIT](../LAB1-GIT/README.md) |
[LAB3-AWS](../LAB3-AWS/README.md)] |
[Home](../README.md) 


# PREREQUISITS

First you will need to download jenkins from the official website, for windows version just find it, download the installer and follow the steps. 
* Jenkins should now be available via localhost:8080
* If it gives 404 you will need to change the port number to say 8090 in the jenkins manifest.xml file 

### POWERSHELL PLUGIN

You will be installing tons of plugins for Jenkins, it is really easy - lets start with a powershell plugin 

1. Google Jenkins powershell you should get taken to a link, with another link to ...[Here](https://plugins.jenkins.io/powershell)
2. Go to Archive *top right*
3. Download the latest or earlier version it is a .hpi file 
4. Go to Jenkins and __MANAGE JENKINS__ on the left side
5. __MANAGE PLUGINS__
6. __ADVANCED__ tab
7. __upload plugin__ and chose your powershell.hpi file
8. Click upload 


## LESSON 2 JENKINS JOBS

We can now run powershell from Jenkins, that means we can schedule the jobs so we can do cool stuff like daily reporting, remote API calls etc

Lets get stuck in and start our Jenkins development project

1. Create a new folder called JENKINS-SANDPIT
2. Create a file called BTCREPORT.txt
3. Paste the code below into the file 
```
$url = "https://api.coinmarketcap.com/v1/ticker/?convert=GBP"


#this bit of code will pull data from coinmarketcap into a json file that we could parse or do reporting on.

Invoke-WebRequest -Uri $url -UseDefaultCredentials -UseBasicParsing | Select-Object -ExpandProperty content > C:\Users\adam\Documents\jenkins\output.json
```

4. Now add a git repo like we did the last time - first go to github login, and click create project and follow the steps 
5. Upload this git repo (should be in the steps when you create a new GIT project)

