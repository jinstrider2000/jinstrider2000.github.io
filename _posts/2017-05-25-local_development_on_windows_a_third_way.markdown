---
layout: post
title:  Local Development on Windows (A Third Way)
date:   2017-05-25 18:48:22 -0400
---


***Disclaimer:*** *Before I get started, I want to acknowledge Michael Ries' great blog posts about setting up a local development environment on Windows (found [here](http://michaelries.info/)).  They are a great resource, and well worth reading.  However, since I tackled this same task and came up with a different solution, I just wanted to share what I did with the Learn.co community, if only for the sake of providing more options.*

## Open source development...on Windows?
Open Source development on Windows computers has always been a **chore**.  Many of the common tools (Bash, Ruby, Rails, Python, Git, etc) either don't work natively on the platform, or are missing key features if they do (just try using some of your favorite gems on Ruby for Windows).  However, in recent years, Windows has been aggressively courting the open source community, and to encourage development on their platform they have created, in collaboration with Canonical (the makers of Ubuntu), [Bash on Ubuntu on Windows](https://msdn.microsoft.com/en-us/commandline/wsl/about).

Basically, as far as I understand it, Windows and Canonical have created a *Linux Subsystem* that can be activated on Windows 10 computers. This subsystem contains the same file hierarchy and *all* the system binaries found on a Ubuntu Linux computer, including the Linux kernel.  You interact with these binaries through a modified Ubuntu Bash shell outfitted with a low-level emulator; this translates the Linux user/kernel operations into their Windows equivalents, then translates the results back into a Linux digestable format that the binaries can understand. So, unlike *VirtualBox*, which runs a full, virtual Linux machine on Windows, *Bash on Ubuntu on Windows* runs a stripped down version of Ubuntu with *only* the command line tools.

This solution is *really fast* when compared to a virtual machine, and as far as comparsions to other native environments (i.e. a Mac or Linux machine), as someone who is currently using both a Windows and Mac local dev environment, I can't tell the difference in performance.  Moreover, you might imagine that your projects would have to live exclusively in the linux subsystem because the Windows file system (C:\\) is normally traversed with \ slashes, which would cause an error on Bash, but thankfully the subsystem has a gateway into your Windows file structure (via "/mnt", located at the subsystem's root).  This means you can create your projects anywhere on your Windows computer and still use Bash on it. Lastly, since the Windows 10 Creators Update, the underlying emulation of Linux has been excellent, whereas before I wouldn't have suggested going this route for creating a local environment because the emulation was spotty.  Mind you, Windows still considers this *beta* technology, so if you use this for Learn.co labs/projects and run into issues, keep using the IDE.  So far, I've been using it on the Rails section, and it works perfectly, but your mileage may vary.

## Getting Started
First, make sure you download the [Windows 10 Creators Update](https://support.microsoft.com/en-us/instantanswers/d4efb316-79f0-1aa1-9ef3-dcada78f3fa0/get-the-windows-10-creators-update) if you haven't already.

### Installation
1. In your Cortana Search Bar (lower left of the taskbar), type "For developer settings", and click it.
2. Click on the "Developer Mode" radio button.
3. In the Search Bar, type "Turn Windows features on or off", and click it.
4. Scroll down for "Windows Subsystem for Linux (beta)", select it, then click ok.
5. In the Search Bar, type "Windows Powershell", right click it and choose "Run as administrator".
6. In Powershell, type: `Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`
7. Restart the computer when it prompts you.
8. Now, in the Search Bar, type "Command Prompt", and click it.
9. In Command Prompt, type `bash`
10. Accept the Terms of Use, then the Bash Shell will download to your computer and a shortcut will be created on your desktop.
11. Create a UNIX user profile, and that's it.

## Setting up your Learn environment
This shouldn't be too hard, because since this is just a Ubuntu subsystem running on Windows all the instructions that apply to setting up a Ubuntu local environment for Learn.co should apply. And they do, with some exceptions, which I'll note.  First, you have to view the instructions [here](https://learn.co/manual_setup)...but before you click, since the instructions displayed depend on the type of computer you're on, you need to trick the Learn.co server into thinking you're on a Linux computer.  You do this by changing your browser's *user-agent* field, which is easily done with the [User-Agent-Switcher](https://chrome.google.com/webstore/detail/user-agent-switcher-for-g/ffhkkpnppgnfaobgihpdblnhmmbodake) extension for Chrome.  Now, instructions in hand, just open the bash shell, and follow the instructions, with these modifications:

1. The Learn instructions say to make sure the bash shell is setup as a *login shell*, this is so  the *.bash_profile* (located in your ~ dir) will run at start up.  *Bash on Ubuntu on Windows* defaults to an *interactive shell*, which means the *.bashrc* (also in ~) will run instead.  This isn't a big issue, as the primary script you want (loading rvm every time you open a terminal) is automatically added to *.bashrc* when you download rvm.  Either way, all the extra things the Learn.co *.bash_profile* offers (including the cute heart prompt) can be copied into *.bashrc* with nano (command line text editor) if you want them. Learn.co's *.bash_profile* is discussed at **Step 11**, and can be viewed [here](https://raw.githubusercontent.com/flatiron-school/dotfiles/master/linux_bash_profile)
2. Now, before anything, install git with `sudo apt-get install git-all`, it may have already been installed from the start, but do it just to be sure.
3. ***Note:*** The first bullet point in **Step 3** has you bundle installing `default-jre` (Java Runtime Environment) along with some other things. This is fine, but I suggest you [also install JRE or JDK for Windows](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) (either is fine).  I'm not certain, but I imagine the JRE is necessary for Java based, in-browser content, and since you'll be testing your web apps through a Chrome browser *launched on Windows*, installing JRE in the subsystem may not make a difference.  So be safe and install both, you lose nothing. Also on **Step 3**, the fourth bullet point has you install i386 architecture for Team Viewer on Linux, **skip this** and download [TeamViewer for Windows](https://www.teamviewer.com/en/download/windows/).
4. Now, follow Learn.co's steps as follows: **Step 1,2,3,4,5,7,8,9,10,11,13**

I'm currently using [VS Code](https://code.visualstudio.com/download) for my projects, which allows for the *Bash on Ubuntu on WIndows* shell to be integrated into the IDE.  The instructions for that are [here.](https://code.visualstudio.com/docs/editor/integrated-terminal) I hope this post is helpful to anyone considering learning and developing locally on Windows. Good luck, and keep coding!
