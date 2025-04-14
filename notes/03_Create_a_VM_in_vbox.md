# 3. Struggling to Create a VM in VirtualBox

> https://www.youtube.com/watch?v=dg2ir4wGLX4  
> July 30, 2024

+ VM is virtual machine.
+ First you need a virtual machine manager, like VirtualBox. Download Oracle VirtualBox from official website.
+ Also we need an ISO file of the OS that we want VM of. Get that from official website. For Ubuntu, go to [Ubuntu Official Website](https://ubuntu.com/download)

## Instructions
+ Open VirtualBox
+ Click on `Tools`
+ Click on `New`
+ Click `Expert Mode`
+ Give a name for the VM you want. If you mention `Ubuntu` it will automatically update `Type` and `Version` fields.
+ Give the folder where you want to save your Virtual Machine files (not the files inside VM).
+ Add the ISO file path in ISO image field.
+ Click checkmark `Skip Unattended Installation`
+ Now `Unattended Installation` tab will be disabled and shown in grey.

+ Go to `hardware`
    + Give 4GB for Base Memory that is `4096 MB`, anything in green range is fine.
    + Give `4` CPUs in processors, or anything in green range.
+ Go to `Hard Disk`
    + Click on `Create a Virtual Hard Disk Now`
    + Give the path for the virtual hard disk image file to be saved
    + Specify maybe `30 GB` of size
+ Click `Finish`

> [!IMPORTANT] 
> For some distros, there is official documentation for using that OS as virtual machine, please follow their instructions.

### Installing
+ Now start the virtual machine. (You can select the VM and click `start` button or double click on VM)

> [!CAUTION] Mouse Capture
> If you click your mouse inside VM, before it completely loads, it will show a dialog about `Host Key` and `Mouse capture`, but don't panic like @youravgdev[^1]. Click cancel and wait for the `Automatic Keyboard Capture` and `Mouse Integration` to turn on, then you will be able to use your mouse and keyboard inside VM.  
> 
> In case, if the automatic capture is not turned on, then click your mouse inside VM, when the dialog opens up, click capture, but make sure that you read the whole dialog message that gives you hint about how you can get out of capture etc.
>
> To change the `host key` that will `uncapture` your keyboard and mouse, you can click on `file` near title bar, then `preferences`, then `expert`, then scroll down, `virtual machine`, then you see what you want to do.

+ Then follow the instructions shown on screen to complete installation. (steps will be different for different distros)

+ Then to setup the VM, we can run post-install script that we have written earlier. [post-install.sh](./02_Setup_Dev_Env.md#automating-using-bash-script).
    + You can run the script usng `wget`
    ```bash
    wget -qO- https://raw.githubusercontent.com/urbanspr1nter/avg-dev/refs/heads/master/tools/scripts/post-install.sh | bash
    ```
    + `wget` is a command to download files from internet from terminal.
---

**Back to HOST Machine**

> [!NOTE] Customization on HOST machine
> @youravgdev[^1] does some customization, you can do this as you like, but if you want to follow youravgdev[^1] then you can checkout [video@27:50](https://youtu.be/dg2ir4wGLX4?t=1670)

## Git and GitHub
`Git`[^2] is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.  
> [!NOTE] And it's pronounced git[^3].  

[GitHub](https://github.com) is a platform to host git repositories. Meaning it will store your repository and changes tracked, and makes it easier to collaborate with others.

Repository is just a folder/directory that you want to track changes.
+ To start tracking, you use `git init`.
+ To add a change, do `git add <Filename>`, or `git add --all` for adding all changes.
+ To commit all the stages changes, `git commit -m "<commit-message>"`
+ To add the link to upstream(the hosted/remote repository), do `git remote add origin <remote-repository-URL>`
    + `<remote-repository-URL>` should be replaced with url of the created github repo.
    + How to create github repo?
        + Create [GitHub](https://github.com/) account, if you don't have one already.
        + Create [New repository](https://github.com/new)
+ To send changes from local to remote, do `git push`
+ To get changes from remote to local, do `git pull`


#### @YourAvgDev's github
Here is the link to YourAvgDev's github profile: https://github.com/urbanspr1nter 


[^1]: https://youtube.com/@YourAvgDev
[^2]: https://git-scm.com/.
[^3]: Yeah, it's git as in `global information tracker`, not jit. [How to pronounce git](https://www.reddit.com/r/git/comments/jejppx/how_do_i_pronounce_git/)

[NEXT NOTE &Rarr;](./04_First_Web_Project.md)