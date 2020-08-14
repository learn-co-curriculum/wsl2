---
title: WSL::Flatiron Local Environment
date: "2020-06-05T00:00:00.000Z"
description: Configure WSL2; Code on Windows 10
---


Howdy neighbor. Have you heard the news about WSL2? As of June 2020, WSL is available to the general public. I figured this would be a good opportunity to share my findings with you, the general public. But more specifically, Flatiron Students using WSL. 

## Table of Contents:
1. [Updating and Configuring Windows 10](#updating-and-configuring-windows-10) 
2. Enabling Windows Subsystem for Linux (WSL) && Virtual Machine Platform
3. Installing Ubuntu
4. Upgrading to WSL Packages and Ubuntu Version
5. Flatiron Local Environment Set Up
6. Install Ruby Version Manager
7. Configure Git
8. Node Version Manager
7. [Generating a SSH Key](#ssh)



## <a name="updating-and-configuring-windows-10"></a>Updating and Configuring Windows 10

1. Make sure to run: [Windows Update Assistant](https://www.microsoft.com/en-us/software-download/windows10ISO). When the update is complete, your system build should be greater than 1900. Please verify this is true before continuing.

<br>

## Enabling Windows Subsystem for Linux (WSL) && Virtual Machine Platform

Windows Subsystem Linux (WSL) is **not** automatically enabled on windows. So, to start off, we need to enable it!

1. Go to your Windows Search bar and type in `Turn Windows Features On or Off`. Click on the result that matches your query. It will be in your Control Panel.  You should see something like this:

    ![toggle windows features](https://curriculum-content.s3.amazonaws.com/setup-instructions/turn-windows-features-on-or-off.png) 

<br>

2. Scroll down until you see "Windows Subsystem for Linux" - ensure its box is checked!

    ![wsl checkbox](https://curriculum-content.s3.amazonaws.com/setup-instructions/wsl-turnon.png)

<br>

3. Scroll up a bit until you see "Virtual Machine Platform." Turn this feature on as well.

   ![virtual machine platform checkbox](https://curriculum-content.s3.amazonaws.com/setup-instructions/wsl-virtual-machine-platform.png)  

<br>


4. Click `ok`. This will prompt Windows to completely restart. Do so, grab some water, and let's continue!

<br>


## Installing Ubuntu

1. Open up Microsoft Store. Search for "Ubuntu"

2. Choose "Ubuntu" (not 16.04 LTS, 18.04 LTS, or 20.04LTS)

    ![ubuntu choice in microsoft store](https://curriculum-content.s3.amazonaws.com/setup-instructions/ubuntu-choice.png)

3. Search for, and open the newly installed Ubuntu application.

4. Choose a username -- I suggest picking a really simple username (like your first name).

    <span style="color:red;">NOTE:</span> 
    -  Ubuntu will not accept capital letters in a username
    -  Ubuntu will not accept numbers at the start of a username

5. Choose a password -- I suggest picking a really simple password.

    <span style="color:red;">NOTE:</span> 
    - When you start typing a password, it will look as though nothing is happening. Thats totally normal, it's just a security feature. 
    - Type whatever password you would like, and press enter.
    - It will prompt you to confirm your password, retype the same password and hit enter.

Once you have set up a username and password, you should return to a normal bash prompt (what does even mean!?). It should look something like this:

TODO: ENTER AN EXAMPLE OF COMMAND PROMPT HERE!!

<br>

## Upgrading to WSL Packages and Ubuntu Version (via Command Prompt)

At this point, you've already install WSL1, we just need to run a few commands to update it to WSL2. The next few commands are a little quirky, but, extremely important.

1. [Click this link](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi) -- it will download the necessary msi package. The package's name should be something along the lines of: `wsl_update_x64.msi`.

2. Double click on the package and follow the necessary prompts to install. (It should take approx 30 seconds to install.)

3. Now, in your Windows Search bar, search for an application named `Command Prompt`. click <span style="color:red;">Run as Administrator</span>.

TODO INSERT PIC OF RUN AS ADMINISTRATOR HERE

4. Run: &nbsp; &nbsp;  `wsl --set-default-version 2` <br>
Inside Command Prompt (running as administrator), copy and paste the code below:

TODO: WHAT DOES IT SAY WHEN THE LINE ABOVE INSTALLS CORRECTLY??

5. Run: &nbsp; &nbsp;  `wsl.exe --set-version Ubuntu 2` <br>
This command will change your version of Ubuntu from 1, to 2.

Annnddd That's it for WSL2 you _should_ be good to go on your WSL2 installation. Let's move on to our Learn Local Environment installation.

<br>

## <div style="text-align:center">• &nbsp;  Water Break &nbsp;  • </div> 
<div style="text-align:center"> Take a moment to stretch a little, fix your posture, hydrate a bit. </div>

<br>
<br>

## Flatiron Local Environment Set Up

Okay, so now we can start setting up our Ubuntu system for Flatiron stuff!

1. Open Ubuntu and run the following commands to make sure packages in your Ubuntu system are up to date:

    ```
    sudo apt-get update  
    ```

2. Then run the following command to install a few important packages. (copy the entire block of code)

    ```
    sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev software-properties-common libffi-dev libpq-dev libgdbm-dev libncurses5-dev automake libtool bison gnupg postgresql postgresql-contrib
    ```
### Ruby Version Manager

Next, we'll install [Ruby Version Manager](https://github.com/rvm/ubuntu_rvm), also known as RVM.

3. Run: &nbsp; &nbsp;  `sudo apt-get install software-properties-common`

4. Run: &nbsp; &nbsp;  `sudo apt-add-repository -y ppa:rael-gc/rvm`

5. Run: &nbsp; &nbsp;  `sudo apt-get update`

6. Run: &nbsp; &nbsp;  `sudo apt-get install rvm`

7. Run: &nbsp; &nbsp;  `source ~/.bashrc`

I've purposefully listed commands 3 through 7 separately. Do not run them all at the same time -- run them in succession.

Moving right along, let's set up the ruby version compatible with Flatiron labs, we want to
  download ruby 2.6.1 and set it as our default:

8. Run: &nbsp; &nbsp;  `rvm install "ruby-2.6.1`

9. Once that's complete run: &nbsp; &nbsp; `rvm use 2.6.1 --default` <br>
This will set Ruby version 2.6.1 to be our default Ruby. 


### Gem Installation

10. Run: &nbsp; &nbsp;  `gem install bundler` <br>
This will install a Ruby gem named [Bundler](https://rubygems.org/gems/bundler). (follow the hyperlink if you are curious as to what Bundler does)

11. Run: &nbsp; &nbsp;  `gem install learn-co` <br>
This will allow you to use commands like "*learn open*", "*learn test*", and "*learn submit*". For more information on the [Learn gem](https://rubygems.org/gems/learn-co), follow that hyperlink! 

    <span style="color:red;">NOTE:</span> 
    After installing the Learn gem, you will get a weird error that looks something like:

    ```
    RDoc is not a full Ruby parser and will fail when fed invalid ruby programs.

    The internal error was:
        (NoMethodError) undefined method `[]' for nil:NilClass
        ERROR:  While executing gem ... (NoMethodError)
        undefined method `[]' for nil:NilClass
    ```

    This error is okay; it is the only error I will suggest ignoring!

    Before we continue, let's configure our new installed learn-co gem. We'll do part of the configuration now, and another part later! 

    - First run: &nbsp; &nbsp;  `cd ~` <br>
    - Then run: &nbsp; &nbsp;  `touch .netrc` <br>
    - Next run: &nbsp; &nbsp;  `learn whoami` <br>
    That last command will ask you to to retrieve some information and bring it back to terminal. That information can be found on your [learn.co](https://www.learn.co/) profile page. So, head to [learn.co](https://www.learn.co/), click on your profile picture in the top right, then click on the "**Your Profile**" link. On your profile page, scroll to the bottom and copy your OAuth token. YOU ONLY NEED TO COPY EVERYTHING AFTER "OAuth token:". For example, mine looks like this:
      ```
      9cd7da7faf8d978cb613008bdb56e4fc2d6642sdfds91eb70b5d8d3b2820fd91
      ```

    - Copy your token and paste it into terminal. <br>
    If all fairs well, your terminal _should_ display some information about you!


12. Run: &nbsp; &nbsp;  `gem install pry` <br>
This will install the lovely debugging tool [Pry](https://rubygems.org/gems/pry). Seriously ask yourself, where would you be with out [Pry](https://rubygems.org/gems/pry)??

13. Run: &nbsp; &nbsp;  `gem install rails` <br>
As if [Rails](https://rubygems.org/gems/rails) needs an introduction! (but just incase, follow the hyperlink!)

14. Run: &nbsp; &nbsp;  `gem install nokogiri` <br>
[Nokogiri](https://rubygems.org/gems/nokogiri) has many uses -- You will primarily use it to scrape websites so definitely install it and check out the documentation.

That should be all for necessary gems. Let's move on to configuring our version control! 


<br>

### Configure Git

15. Run: &nbsp; &nbsp;  `git config --global color.ui true` <br>
This (and the next 2 commands) will set up git in your system. When you enter these commands, your terminal will not say anything -- don't worry, it definitely worked!

*For the next few commands, make sure to input your specific information:*

16. Run: &nbsp; &nbsp;  `git config --global user.name YOUR_GITHUB_USER_NAME` <br>
Please please please replace your YOUR_GITHUB_USER_NAME, with your actual github username. For example, mine would look something like: 
    ```
    git config --global user.name "dwyn"
    ```

    Alternatively, you could just put your first and last name, like so:

    ```
    git config --global user.name "Dwayne Harmon"
    ```

17. Run: &nbsp; &nbsp;  `git config --global user.name YOUR_GITHUB_EMAIL_ADDRESS` <br>
You are essentially repeating the same process, but with the email address tied to your github account.

<br>

### Node Version Manager
[Node Version Manager](https://www.keycdn.com/blog/node-version-manager#:~:text=What%20is%20Node%20Version%20Manager,via%20the%20command%20line%20interface.) is a tool that allows programmers to seamlessly switch between different versions of Node. I would say its a kin to Ruby Version Manager, but for Node. [Node](https://www.codecademy.com/articles/what-is-node) allows developers to write JavaScript code that runs directly in a computer process itself instead of in a browser.


20. Run: &nbsp; &nbsp;  `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.1/install.sh | bash` <br>
This will install NVM, baby!

21. Run: &nbsp; &nbsp;  `source ~/.bashrc` <br>
This refreshes your terminal!

22. Run: &nbsp; &nbsp;  `nvm install node` <br>
This will install Node.JS! 



<br>

## <div style="text-align:center">• &nbsp;  Water Break &nbsp;  • </div> 
<div style="text-align:center"> Take a moment to close your eyes, focus on your breathing, hydrate a bit. </div>


<br>





## Visual Studio Code

You can use any editor you want, but I am going to be walking through setting up
VSCode.

1. <a href="https://code.visualstudio.com/download" target="_blank">Follow this link to download VSCode</a>. Choose the Windows download, not the Linux
    download. Any required Linux downloads will be done via the Ubuntu terminal,
    and everything else should be downloaded for your Windows OS.

    <span style="color:red;">NOTE:</span> <br>
    As VSCode is installing, make sure to check all check boxes so that it installs for your entire system.

2. To configure your Ubuntu terminal to be available in VSCode:

    - open up VSCode
    - open the Command Palette via `F1` or `Ctrl`+`Shift`+`p`
    - begin typing the following: `Terminal: Select Default Shell`  until you
      see it. Select that option.

    ![command palette](https://curriculum-content.s3.amazonaws.com/setup-instructions/default-shell.png)  

    - Once you select it, a few options will pop up. You want to select WSL

    ![WSL Terminal](https://curriculum-content.s3.amazonaws.com/setup-instructions/wsl-bash-selection.png)

3. Now, you can use your Ubuntu terminal in VSCode. Select "New Terminal" in
    the "Terminal" drop-down, or type `Ctrl`+`Shift`+` in order to use it!

4. Install the [Remote - WSL extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl) for VSCode. The Remote - WSL extension extension lets you use WSL as your full-time development environment right from VS Code! 

<br>









## <a name="ssh"></a>SSH

  You can either communicate with your remote repositories via HTTPS or SSH.
  Let's use SSH so you will not have to authenticate with
  your GitHub username and password everytime you run &nbsp; *learn save* , &nbsp; *learn submit* ,  or any other commands similar to&nbsp;  *git push*.

  1. Run:&nbsp; &nbsp; `ssh-keygen` <br>
    - You will be asked where to save the new ssh file. Just press "enter" to save it in the default location. <br>
    - You will be asked for a passphrase -- <span style="color:red;">DO NOT ENTER A PASSPRHASE!</span> Simply press "enter", twice.

  You will know the process is complete once you have some randomly generated ASCII art in your terminal. Now, let's retrieve the contents of that file.

  2. Run:&nbsp; &nbsp;  `cat ~/.ssh/id_rsa.pub` <br>
  This should print out a really long string of characters starting with *ssh*. It will look *something like this*:
      ```
      ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDI0n1zGPzhpwJRCwn0KeI8BybeyZP1XJWaGnvBMJNfzvXVhRGX5TxZ6Aq2hvHtDVE0ST9O1L2PU802RN5in6mpwCWoeJx9HXKoI3KW1nAYMJH8LjR1I2nbm7cSZjg732CdElc3uwTMf0cU7S2oocH5vTYpBT20NsdfsdsdfsdQaHdfAlop6VVckZKNZbPLNiW1MO2rk7Hw1j6r6bDM1nFwV+uDzxJ7+uEBXpl6bsxVn7X8AmwZdLSYz6wTq1lXWTy46tfkkFPNFyu5akkYoTym3jnQpKdW6AOVl89dXfRira4+DF7mQt3+kcfqHVsC7nN4s5T2Ju2KrVYiKF4yo89CXd7Yu6EQx7JeRlw+kxtzgYo1enMnp4hAawgxCkWlEqWyJQkNVZ6Wq+/gcHezJr2PoUc3lTX61TUcoCXV3QkjJDmnsSiwVDUqypCEBtNZyKMX5ZjSESPaj24C3F/yOdWIQu40iUR8oOT86Xo9+waR/nIobxaqWLJ4I8vfVqXsrh0ZTU= dharmon@skynet.attlocal.net

      ```
      <span style="color:red;">Just keep in mind, yours will look *similar*... not the same!</span>

3. copy whatever <span style="color:red;">__your__</span> ssh key is, and follow this link: [Github New SSH](https://github.com/settings/ssh/new). 

4. In the top input field, enter something meaningful. Such as, computer name, purpose for the key and date are solid options.

5. Paste your ssh key in the lower box.

    After you've completed both, your page should look similar to this:

![New SSH Key in Github](./sshkeysnew.png)

6. Click "*Add SSH key*", and that's all! Your ssh key has been generated on your computer, and linked to Github! Yeth!

<br>
































## Updating Learn Config

1. Update your .learn-config

- Open the WSL terminal. You can access the terminal through VS Code now, or you
  can open a separate terminal by typing `wsl` into the Window Search Bar.
  Alternatively, you can also press the `Windows` and `R` keys (for run), and
  entering `wsl`.

- Travel to your Linux home directory by typing `cd`, you can change your
  `.learn-config` by typing:

    ```shell
    nano .learn-config
    ```

- and customizing where you want the `learn open` command to save labs, and
  setting your editor to VSCode. Here's what it should look like:

    ```
    ---
    :learn_directory: "/mnt/c/users/YOUR-WINDOWS-USERNAME/development/flatiron/labs"
    :editor: code
    ```

- You save a file you have modified in `nano` by following the directions at the
  bottom of the screen: click `Ctrl`+`X` and then `y` and then `Enter` to save
  your changes.

- If you feel uncomfortable with these commands, check out the basic Linux
  commands link below in the resources.





























## Important Knowledge: Basic Use

Your terminal is actually accessing an Ubuntu Virtual Machine which is running
inside of your Windows OS. If you ever `cd` in your terminal, you will be
sent to the 'user home' of your Linux VM. That is also the default location you
will be in when you open your Ubuntu app. You actually want to do all of your
business inside of your normal Windows file space, not your Linux VM file space.
So, you will need to know how to navigate in your terminal from your Ubuntu file
system to your Windows file system. This is pretty simple if you understand how
the system is set up, so let's go over that quickly.

To allow you to access the functionality of a Linux machine, Windows stores the
Ubuntu OS and file system inside of its own file system. You should NEVER access
your Ubuntu files via your Windows machine. What you SHOULD do is save
everything you are working on in your normal Windows filespace, and access that
via your Ubuntu terminal. So, how do you do that? Well, from the Ubuntu's point
of view, it is just a normal Linux machine, but Microsoft has made a pathway
between the Linux VM and your Windows OS via the `/mnt` directory in your
Ubuntu's root.

Here is a quick visual of what the first few levels of any Linux filesystem look
like:  

![linux file system](https://curriculum-content.s3.amazonaws.com/setup-instructions/linux_fs.png)

As you can see, the `mnt` directory is made for other filesystems, so that is
where Microsoft connected your Linux to your Windows machine:

![linux file system](https://curriculum-content.s3.amazonaws.com/setup-instructions/linux_fs_path.png)

So, you can get there from your starting point by typing:

```shell
cd /mnt/c/users/your_windows_username
```

or

```shell
cd ../../mnt/c/users/your_windows_username
```

Remember, put all of your stuff in your windows directories! That way, you have
access to it via your Linux Terminal or your Windows OS, and your VSCode editor
can open to the correct location when you use

```shell
code .
```

(if you are in your Linux file system, VSCode will open, but not to the right spot).

## Adding A Flatiron Customization To Your Terminal

Start out by making a backup for your `.bashrc`

```shell
mv .bashrc .bashrc.bak
```

We will want a tool for converting Windows ending to Unix endings for our new
`.bashrc`

```shell
sudo apt-get install dos2unix
```

download the new `.bashrc`

```shell
curl -R "https://raw.githubusercontent.com/Enoch2k2/flatiron-wsl-bashrc/master/.bashrc" >> $HOME/.bashrc
```

We'll use our converter to convert our bashrc to use the right unix endings:

```shell
dos2unix .bashrc
```

## Set up a directory for all of your labs

You'll notice that we set up our `.learn-config` file earlier with a path
destination of `/mnt/c/users/<your_windows_username>/dev/flatiron/labs`. The
`.bashrc` file we just downloaded gives us a really nice way to access that
folder quickly by just typing in `labs` when we pull up our WSL terminal (or
anytime you want to access that folder - it doesn't matter what directory you
are currently in when you type it). In order for this to work, we need to make
sure that these directories exist. To do this, begin by navigating to your
`windows home` directory:

```shell
cd /mnt/c/users/your_windows_username
```

Now, let's make the appropriate files. Run these one at a time, and do it
without copying and pasting. Remember the basic bash commands: `cd` changes
directories to whatever folder you type in and `mkdir` creates a new directory
which will be a subdirectory of the current directory location of your terminal.

```shell
mkdir dev
cd dev
mkdir flatiron
cd flatiron
mkdir labs
```

Now you have the directories you need, and you should have seen yourself
navigating down your new file tree as you made each new directory and then
`cd`'d into it.

Now, `learn open` should work seamlessly by adding your most current lab to the
`labs` directory we just made.

Also, you should be able to run the command

```shell
labs
```

at any time in your terminal and you will be taken to your `labs`  directory.
Give it a try!

> **Note:** If the `labs` command is not working, try running `learn directory`.
> You will be prompted to re-enter the location where you would like your labs
> to be stored. Do not use the provided default. Instead, the path should be:
>
> ```shell
> /mnt/c/users/<your_windows_username>/dev/flatiron/labs
> ```

<br>
<br>
<br>
<hr>

## FAQ

If you get the error: `Windows Subsystem for Linux has no installed
distributions. Distributions can be installed by visiting the Windows Store:
https://aka.ms/wslstore Press any key to continue...`

1. Search for 'Services' in your Windows search bar, open it up  

![find services ](https://curriculum-content.s3.amazonaws.com/setup-instructions/find_services.png)

2. Scroll down to the `L` section, and find `LxssManager`. If it is running,
right click and `Restart` it. If it is not running, right click it and
`Start` it.  

![Lxss Manager](https://curriculum-content.s3.amazonaws.com/setup-instructions/lxss_manager.png)

[You can check out the github issue here](https://github.com/Microsoft/WSL/issues/2576)

---

## Resources

[Microsoft Documentation: Windows Subsystem for Linux]( https://docs.microsoft.com/en-us/windows/wsl/install-win10)  
[Setting up a SSH Key with GitHub](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)  
[Basic Linux Commands](https://maker.pro/linux/tutorial/basic-linux-commands-for-beginners)

[VS Code]: https://code.visualstudio.com/download
[WSL Installation Guide]: https://docs.microsoft.com/en-us/windows/wsl/install-win10
[Hack font]: https://sourcefoundry.org/hack/