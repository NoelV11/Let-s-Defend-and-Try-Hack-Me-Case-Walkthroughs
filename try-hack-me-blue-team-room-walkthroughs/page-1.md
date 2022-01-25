# Page 1

## What is the purpose of Malware Analysis?

Malware is such a prevalent topic within Cybersecurity, and often an unfortunately recurring theme among global news today.

Not only is malware analysis a form of incidence response, but it is also useful in understanding how the behaviours of variants of malware result in their respective categorisation. This room will be a practical introduction to the techniques and tools used throughout malware analysis — albeit briefly

When analysing malware, it is important to consider the following:

* Point of Entry (PoE) I.e. Was it through spam that our e-mail filtering missed and the user opened the attachment? Let’s review our spam filters and train our users better for future prevention!
* What are the indicators that malware has even been executed on a machine? Are there any files, processes, or perhaps any attempt of “un-ordinary” communication?
* How does the malware perform? Does it attempt to infect other devices? Does it encrypt files or install anything like a backdoor / Remote Access Tool (RAT)?
* Most importantly — can we ultimately prevent and/or detect further infection?

### Question

> Q)Ah, now I kinda understand…

> A)Mark as completed

## Task 2 — Understanding Malware Campaigns

Despite the many variants of malware, attacks can generally be classified into two types: **Targeted** and **Mass Campaign**.

### Targeted Campaign

A “Targeted” attack is just that — targeted. In most cases, malware attacks that occur this way are created for a specific purpose against a specific target. A great example of this type of purpose could be the [DarkHotel](https://www.kaspersky.co.uk/resource-center/threats/darkhotel-malware-virus-threat-definition) malware, whom is designed to steal information such as authentication details from government officials.

### **Mass Campaign**

On the other hand, the “Mass Campaign” classification can be akin to many real life examples, and is the most common type of attacks. The entire purpose of this type of Malware is to infect as many devices as possible and perform whatever it may — regardless of target.

Kaspersky [report on the “Crouching Yeti (Energetic Bear)” campaign](https://www.kaspersky.co.uk/resource-center/threats/crouching-yeti-energetic-bear-malware-threat), this campaign specifically targets the following:

* Industrial/machinery
* Manufacturing
* Pharmaceutical
* Construction
* Education
* Information technology

Whilst it this variant is _technically_ _targeted_, there is a rather large scope of this variant of malware, and as such, can be considered as a “Mass Campaign” attack.

#### Questions

> Q)What is the famous example of a targeted attack-esque Malware that targeted Iran?

> A)Stuxnet

> Q)What is the name of the Ransomware that used the Eternalblue exploit in a “Mass Campaign” attack?

> A)Wannacry

### Identifying if a Malware Attack has Happened

Much like any interaction with an Operating System, there is always remnants of such activity even if there is little trace…

Unfortunately, **malware** (dependant on its variant) **is largely obtrusive** — in the sense that it leaves quite an extensive papertrail of evidence…Perfect for us analysers!

The ultimate process of a malware attack can be broken down into a few broad steps:

1. Delivery
2. Execution
3. Maintaining persistence (not always the case!)
4. Propagation (not always!)

**These steps will generate lots of data.** Namely: network traffic such as communicating with hosts, file system interaction like read/writes and modification.

Malware is essentially classified based upon the behaviours it produces to perform the steps listed above. For a famous example, Wannacry performs all four of these steps.

1\. Delivery

This could be of many methods, to name a few: USB (Stuxnet!), PDF attachments through “Phising” campaigns or vulnerability enumeration.

2\. Execution

Here’s the main part of how we classify Malware. What does it actually do? If it encrypts files — it’s Ransomware! If it records information like keystrokes or displays adware — we can classify it as Spyware.

**We only understand this stage through analysing the sample, which is why analysis is important — and is what we’ll be covering.**

3\. Maintaining Persistence

It wouldn’t make much sense for Malware authors to go through all the trouble of developing a piece of code that is capable of execution — just for it to execute and that’s it…Gone. Unless you have a very specific agenda ([Cerber](https://blog.malwarebytes.com/detections/ransom-cerber/)).

I have submitted an extensive report on this specific Malware, amongst others for a University Module on Malware Analysis…however I will wait for it to be marked before sharing.

Imagine a keylogger has been installed, but you then restart your Computer 30 seconds later. Unless you’ve entered a lot of sensitive information in 30 seconds — that’ll be of no use to the author.

4\. Persistence

This stage is largely why Malware is so **“noisy”**, Malware employs many techniques, of which we’ll be covering in-depth much later on. Essentially, this stage is just to make sure that the “execution” is worth its while.

5\. Propagation

Hey…If you can infect one device, why not infect more whilst you’re at it? Again, this is another reason why Malware can be so noticeable. Host discovery generates a lot of network traffic, we’ll come to this later.

### Malware Fingerprints

Host-Based Signatures

These are generally speaking the results of execution and any persistence performed by the Malware. For example, has a file been encrypted? Has any additional software been installed? These are two of many, many host-based signatures that are useful to know to prevent and check against further infection.

Network-Based Signatures

At an overview, this classification of signatures are the observation of any networking communication taking place during delivery, execution and propagation. For example, in Ransomware, where has the Malware contacted for Bitcoin payments?

Such as in the case of Wannacry, looking for a large amount of “Samba” Protocol communication attempts is a great indication of infection due to its use of [“Eternalblue”](https://research.checkpoint.com/2017/eternalblue-everything-know/).

#### Question

> Q)Name the first essential step of a Malware Attack?

> A)Delivery

> Q)Now name the second essential step of a Malware Attack?

> A)Execution

> Q)What type of signature is used to classify remnants of infection on a host?

> A)Host-Based Signatures

> Q)What is the name of the other classification of signature used after a Malware attack?

> A)Network-Based Signatures

## Static Vs. Dynamic Analysis

There are two categories used when analysing malware, these are:

1\. Static Analysis

2\. Dynamic Analysis

Whilst the methods and tools used for these two categories are vastly different, they are essential in compositing an understanding of how a malware behaves.

**Static Analysis.**

At its brief, “Static Analysis” is used to gain a high-level abstraction of the sample — it can be fairly simple to decide if a piece of code is “malicious” or not with this method alone (but not always, this will be discussed later…). At its core, this method is of the analysis of the sample at the state it presents itself as, without executing the code.

Employing the use of techniques such as signature analysis via checksums means quick, efficient (albeit extremely brief) and safe analysis of malware.

**Dynamic Analysis**

This step is a lot more involved, and is where the abstraction of the sample is largely built upon. “Dynamic Analysis” essentially involves executing the sample and observing what happens. This of course is not safe. If the sample turns out to be “Ransomware” — you’ve now lost your files. If it is capable of propagating via traversing a network, nice…You’ve now just infected your Local Area Network (LAN).

**Please note that these are extremely simplistic explanations of these techniques**, there is a lot more involved which we will go throughout this series.

### Questions

> Q)I understand the two broad categories employed when analysing potential malware!

> A)Mark as completed

## Discussion of Provided Tools & Their Uses

You will see that some tools will overlap between Static and Dynamic analysis:

Provided Static Analysis Tools:

C:\Users\Analysis\Desktop\\**Tools\Static\PE Tools**

* PeID
* **PE Explorer**

C:\Users\Analysis\Desktop\\**Tools\Static\Disassembly**

* IDA Freeware

The tools listed here will be used for future tasks in this room

## Obtaining MD5 Checksums of Provided Files

MD5 “Checksums” are a prominent attribute in the malware Community. Because there can be many variants of a family of Ransomware, these MD5 “Checksums” are cryptographic “fingerprints” of the files. This allows a uniformed identification throughout the community — especially with automated Sandboxes.

For example, say you have 20 files of unknown origin, you are able to identify their genus using their MD5 sum against websites such as [Virustotal](https://www.virustotal.com/gui/), if that MD5 “Checksum” has been previously analyzed — removing all the legwork for us!

### Task

> Navigate to the **“Tasks” Folder on the Desktop**, and then enter the **“Task 7” Directory**, where there will be **three** files:

> **- aws.exe**

> **- NetLog.exe**

> **- vlc.exe**

Sure, these are common names of executables, but anyone can name an executable as whatever they like! Just because it says “vlc” doesn’t mean it is indeed the VLC application! This is where identifying their MD5 Checksum is useful, as no matter the name — their MD5 reveals its true identity.

I have installed the [“HashTab”](http://implbits.com/products/hashtab/) application, which calculates a files MD5 sum — amongst others, directly within Windows Explorer as if you were inspecting its properties…

Your Task:

Identify the MD5 Checksums of the three files provided in **Task 7**

#### Questions

> Q)The MD5 Checksum of aws.exe

Right click on aws.exe,head over to the Properties section and then to ‘File Hashes’,we can find the hash

![](https://cdn-images-1.medium.com/max/1000/1\*zMKZvXqifG8HYo-9EmAi9w.png)

> A)D2778164EF643BA8F44CC202EC7EF157

> Q)The MD5 Checksum of Netlogo.exe

As folllowed in the previous question,we find:-

![](https://cdn-images-1.medium.com/max/1000/1\*d66tylIcrvocVVqL9NKTNA.png)

> A)59CB421172A89E1E16C11A428326952

> Q) The MD5 Checksum of vlc.exe

As folllowed in the previous question,we find:-

![](https://cdn-images-1.medium.com/max/1000/1\*ZE27D9kYvk55J\_Ky7f9prg.png)

> A)5416BE1B8B04B1681CB39CF0E2CAAD9F

Now lets see if the MD5 Checksums have been analysed before

Look up those MD5 “Checksums” on [Virustotal](https://www.virustotal.com/gui/home/search) to solve this task:

> Q)Does Virustotal report this MD5 Checksum / file aws.exe as malicious? (Yay/Nay)

Let’s visit ViruusTotal and click the ‘Search’ tab to enter the hashes&#x20;

![](https://cdn-images-1.medium.com/max/1000/1\*XTp5\_ZZXDuAEhfD275wKxQ.png)

We get the following results depicting that the file is not malicious in any way&#x20;

![](https://cdn-images-1.medium.com/max/1000/1\*vONO3Tm-aMV2D9kr-3qubA.png)

> A)Nay

> Q)Does Virustotal report this MD5 Checksum / file Netlogo.exe as malicious? (Yay/Nay)

Following the steps as in the previous question,we get the following result assesment for the file hash&#x20;

![](https://cdn-images-1.medium.com/max/1000/1\*D9VJEKJDO2mMkBaWcsXmbg.png)

The file hash is not malicious

> A)Nay

> Q)Does Virustotal report this MD5 Checksum / file vlc.exe as malicious? (Yay/Nay)

Following the steps as in the previous question,we get the following result assesment for the file hash&#x20;

![](https://cdn-images-1.medium.com/max/1000/1\*KlilmVLZBe5CQWeYaGiK3A.png)

The file hash is not malicious

> A)Nay

## Identifying if the Executables are obfuscated / packed

There are a few provided tools on this Windows instance that are capable of identifying the compiler / packer of a file. However, PeID has a huge database and is a great tool for this.

Moreover, just because a file doesn’t have the “**.exe**” extension, doesn’t mean it isn’t an actual executable! For instance, it can have the “.jpg” extension and still be an executable piece of code. This is a tad-bit out of scope for this room specifically, but essentially, files have identifying attributes within its hex — known as file headers.

E.g. The hex value for an executable is always “**4D 5A**”. So if a file with a “**.jpg**” file has the hex header of “**4D 5A**”, then it is obviously not a jpg file. You can read more into file headers / trailers [here](https://www.garykessler.net/library/file\_sigs.html), which are great resources for data carving in file forensics / recovery.

**Provided Tools: PeID**

### Questions

> Now using “PeID”, identify the compiler / packer of the following two files in the Directory “Tasks/Task 9” to answer the questions

> Q)What does PeID propose 1DE9176AD682FF.dll being packed with?

We can browse to the lab’s Documents folder,to find PEiD’s exeutable file&#x20;

![](https://cdn-images-1.medium.com/max/1000/1\*BlgS7FqwMlpBu5PIKD8ozw.png)

Load the 1DE9176AD682FF.dll file,from Task9 directory located in the Desktop(click on 3 dots)

After loading the file,PEiD states that the 1DE9176AD682FF.dll file is loaded with Microsoft Visual C++ 6.0 DLL

![](https://cdn-images-1.medium.com/max/1000/1\*H\_\_rgV9xmgoMLPRCu70tXQ.png)

> A)Microsoft Visual C++ 6.0 DLL

> Q)What does PeID propose AD29AA1B.bin being packed with?

Going with the same step as before,but this time select File Type as ‘All Files’ from Task 9 directory and load the AD29AA1B.bin file

![](https://cdn-images-1.medium.com/max/1000/1\*yRcvOIQhdrZOpixubLdhHw.png)

> A)Microsoft Visual C++ 6.0

## What is Obfuscation / Packing?

Theory:

Packing is one form of obfuscation that malware Authors employ to prevent the analysis of programmes. There are both legitimate and malicious reasons as to why the Author of a program will want to prevent the decompiling of their program.

For example, a legitimate reason is the protection of intellectual property! Whilst I’m one for open-source as much as the next person here — alas not every organisation has the same mindset…but let’s leave that aside.

In the same token, just because you write a program…Why should everyone have the right to “copy” your project? This is one of the justifiable reasons for obfuscation — it is yours at the end of the day!

However, malware Authors employ obfuscation techniques such as packing — whilst for the same reasons, they do so with the intent to prevent people like us reversing it to understand its behaviours and ultimately with the aims of achieving infection.

Practical:

> Your task is to identify whether or not the file **“6F431F46547DB2628”** located in the **Directory** of **“Tasks\Task 10”** is packed using the **tool** **“PeID”** akin to the task you just completed!

### Question

> Q)What packer does PeID report file “6F431F46547DB2628” to be packed with?

Similar to the previous steps,we get this while analyzing the 6F431F46547DB2628 file

![](https://cdn-images-1.medium.com/max/1000/1\*6pnmK9J\_2FsgHHKRASj2dw.png)

> A)FSG 1.0 -> dulek/xt

## Visualising the Differences Between Packed & Non-Packed Code

This is another example of why PeID is a fantastic little tool. With its huge dataset of known packers, it is arguably one of the better ones at being able to fingerprint the names of packers / obfuscators within an application.

Whilst this tool has a huge database, it doesn’t have every packer out there! Especially say if an Author has written their own — PeID will have no way of identifying the packer used. In cases like this, **it’s more about what PeID doesn’t tell us** — rather than **what it does.**

Practical:

You can try this yourself by navigating to **directory** **“Tasks/Task 11”** and dragging and dropping that file into PeID. What does it tell us?

![](https://cdn-images-1.medium.com/max/1000/1\*WUK4R-Xi01uCeSyPdzGJHQ.png)

In this instance, PeID is able to detect what packer has been used to obfuscate the code. Whilst PeID is capable of detecting the possibility of packers being used, it is not able to automatically de-obfuscate them. This is a process we will have to do manually — at a later stage.

After confirming that this file is indeed packed, let’s open it up with a tool called **IDA Freeware**. This is located in **** the **“Tools/Static/Disassembly” directory** (or you can search for it through Windows Toolbar). Notice how there is a very minimal amount of information provided to us? For example, the “Imports” tab is practically empty! Little odd…right?

When opening the file, a few dialogue boxes may appear — its just IDA Freeware processing the file, it’ll take a couple of seconds.

> Q)Cursed obfuscation!

> A)Mark as completed

## Introduction to Strings

Theory:

**“Strings**” are essentially the ASCII / Text contents of a program…this could be anything from passwords for self-extracting zips, to bitcoin addresses in ransomware samples.

Such as that in the example above, when analysing the contents of these strings, we can sometimes paint a fairly indicative picture of the behaviours of the programme — bitcoin wallets being used in ransomware.

### Sub Task:1

> Open a Command prompt on the Windows Machine and navigate to the directory **“Tools\Sysinternalssuite”**

`cd C:\Users\Analysis\Desktop\Tools\SysinternalsSuite`

**Keep this terminal open.**

We’re going to use Microsoft’s Sysinternals “Strings” program to output the retained strings within the specified file in “Task 12”. We can do this by:

`strings "C:\Users\Analysis\Desktop\Tasks\Task 12\67844C01"`&#x20;

![](https://cdn-images-1.medium.com/max/1000/1\*JIvXJ-HGomTsHCa1db40YA.png)

You will receive a whole load of text, most of it looks like nonsense…But there is some text in there that is valuable. Scroll up!

![](https://cdn-images-1.medium.com/max/1000/1\*1dgrPFucA-zhLbCh6YDY1Q.png)

#### Question

> Q)What is the URL that is outputted after using “strings”

> A)practicalmalwareanalysis.com

### Sub Task 2&#x20;

You’ll find that programs often contain large amount of strings and using the “strings” tool from sysinternals may only display 10% of these…

…That and it’s not exactly practical scrolling up through a terminal for stuff like this — we are on Windows afterall! There’s a GUI tool for that.

PE Explorer should easily be accessible from the Start Menu.Drag and drop the same file “67844C01” from the previous question into the application.

Launching PE Explorer,we are met with the following screen

![](https://cdn-images-1.medium.com/max/1000/1\*Y9IW291dZrOZMSuouQ6M0g.png)

Next navigate to the top taskbar File ->Open file ->Select 67844C01 file from Task 12 directory

We are met with the following statistic table

![](https://cdn-images-1.medium.com/max/1000/1\*wxZUt-ABsI98MlYK4UStJQ.png)

After import. Navigate to “View -> Imports”

We get the number of imports below

![](https://cdn-images-1.medium.com/max/1000/1\*l02Y8rh2\_T0Uv3sNHid5iA.png)

> Q)How many unique “Imports” are there?

> A)5

## Introduction to Imports

Theory:

The classification of IDA Freeware is arguable as the tool can be used for both static and dynamic analysis. Without going too in-depth regarding the differences, there are two classifications of tools like IDA Freeware:

* Disassemblers
* Debuggers

Disassemblers reverse the compiled code of a program from machine code to human-readable instructions (assembly). This is limited to how the program represents itself in its current state! I.e. If the contents of an executable changes during execution — “Disassemblers” will not reflect this.

Whilst Debuggers deploy the same techniques used by “Disassemblers”, “Debuggers” essentially facilitate execution of the program — where the analyser can view the changes made throughout each “step” of the program. These tools are great because a true picture of the program presents itself. However, if it is indeed malicious, you have now infected yourself.

With enough understanding, an analyser can introduce “breakpoints” (or pauses) at various stages of a program, where the program will execute up until a breakpoint. For example, sticking with the idea of Ransomware, an analyser can create a “breakpoint” within the application prior to the actual stage of encryption of files. This facilitates an analyser to view the various changes of a program during execution (such as unpacking or connecting to a remote server such as that in a botnet) up until the point of malicious infection.

### Task



> Navigate to the directory “**Tasks/Task 13**” and open “**install.exe**” with IDA Freeware, just like we did in the example above. Again, this may take a few seconds to a couple of minutes to compute dependant upon the size of the application.&#x20;

#### Question

> Q)How many references are there to the library “**msi**” in the “**Imports**” tab of IDA Freeware for “**install.exe**”

Lets launch “IDA Freeware” ,which should easily accessible from the Start Menu.Select the file to import, in this case we’ll be using “uninstall.exe”,from Task 13 folder

2\. Since we know it is an executable file, we select “Portable executable for 80386 (PE) \[pe64.dll]”&#x20;

![](https://cdn-images-1.medium.com/max/1000/1\*RhUIYgTLRDX-2ox6\_FzKYQ.png)

> Q)How many references are there to the library “msi” in the “Imports” tab of IDA Freeware for “install.exe”

> A)9

## Practical Summary

> The file specified for analysis is **“ComplexCalculator.exe”** in the **Directory** **“Tasks/Task 14”.** I’ll leave it up to you to figure out what tool(s) out of what we’ve used above is best!

> Q)What is the MD5 Checksum of the file?

![](https://cdn-images-1.medium.com/max/1000/1\*lalL7HgO-6CEW9aMCKEAog.png)

> A)f5bd8e6dc6782ed4dfa62b8215bdc429

> Q)Does Virustotal report this file as malicious? (Yay/Nay)

![](https://cdn-images-1.medium.com/max/1000/1\*IqmEZXjhFdRFN-tZguESUQ.png)

> A)Yay

\


> Q)Output the strings using Sysinternals “strings” tool.

> What is the last string outputted?

> A) d:h:

> Q)What is the output of PeID when trying to detect what packer is used by the file?

![](https://cdn-images-1.medium.com/max/1000/1\*v2dw1qYU7RL4gdElrlygEg.png)

> A)Nothing found