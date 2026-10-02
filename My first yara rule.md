Well, I saw an interesting malware sample on MalwareBazaar. I will try to analyze it. I chose MedicWiesel name for my codename. After analyzing I will create all IOCs in my  hand. ![](dotnetdropper.png)
Here I see it is a .net file. I usually don't like .net but since this eases my job letting me employ ILSpy I will enjoy it. 


IOCs:
strings 
"0000000A"	"28"	"Rightbar-1.5-windows-x64.exe"
"000001F4"	"24"	"Rightbar-1.5-windows-x64"


It starts rightbar.exe as child process.
![](RightbarChildprocess.png)


I got it I guess. This malware can be executed with --extract-only flag and after accepts an argument which should be directory. Malicious thing happens mostly in Prepare class. inside it there is a payloadhash class call which is like this inside.
![](payloadhash.png)
This just basically takes an embed hash file. 
![](Rightbarpayloadsha256.png)
And one more pattern
`94c976faa7a18e8cd03d867ece41a5c0cf3f7d40741b795fbb5111bf40485263`

Hmm, I analyzed full code of this executable. But it just seems like a dropper. I didn't saw anything too malicious. But it doesn't mean it can't be used as malicious. This seems like to be in gray area. I will analyze the zip archive it drops first
![](dotnetmainfiles.png)
both exes seems legit not gonna lie. Let me look at the decompiled version. Yeah I checked the IOCs in community comments in virustotal. Joesandbox IOC report seemt legit. So I stopped analyzing after finishing reading code of dropper. 

#LEGITSOFTWARE 
