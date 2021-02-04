# Setting Up Unix Computing Environment on Windows 10 with WSL

WSL, or _Windows Subsystem for Linux_, is a subsystem that allows users to run a
Unix computing environment within Windows 10. This is the recommended method for
having a local Unix computing environment for your Windows 10 machine.

There are two versions, WSL 1 and, a newer, WSL 2.

For the Unix@Home workshop, it suffices for attendees to install WSL 1.

## Requirements

Before you proceed with the instructions below, you need to make sure that:

- You have 64-bit versions of Windows 10, version 1607 or higher
  ([Here is how you check](https://support.microsoft.com/en-sg/help/13443/windows-which-version-am-i-running));

- You have administrator access to your Windows 10; And

- You have an SoC Unix account. You can
  [create an SoC Unix account here](https://mysoc.nus.edu.sg/~newacct). For SoC
  students, this username is something that sticks with you for the rest of your
  SoC life -- so choose wisely.

## Installing WSL 1

### Step 1: Enabling WSL on Windows 10 through PowerShell

Before you install WSL 1, you need to first enable the "Windows Subsystem for
Linux" feature by running the following command in PowerShell.

```PowerShell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

You can achieve this step by:

- Hit ++win++ to open the Start menu, type `PowerShell`, then right-click on
  Windows PowerShell, and click "Run as administrator"
- Copy the command above by selecting it and then hitting ++ctrl+c++
- Go to your PowerShell window and paste the command above by hitting
  ++ctrl+v++. Press enter if needed to run the command.

### Step 2: Restart your computer

### Step 3: Install Ubuntu

After restarting your computer, go to the
<a href="https://aka.ms/wslstore">Microsoft Store</a> and get
<a href="https://www.microsoft.com/store/productId/9N9TNGVNDL3Q">Ubuntu</a>
18.04 LTS.[^1]

[^1]:
    The latest Ubuntu 20.04 LTS is
    [reported](https://discourse.ubuntu.com/t/ubuntu-20-04-and-wsl-1/15291)
    reported to be unstable on WSL 1.

Follow the on-screen instructions to install.

When you are asked to create a user account and password, we suggest that you
choose a Unix username that is that same as your SoC Unix username.

## Launching WSL

To launch WSL, you can hit ++win+r++ and type in `Ubuntu` followed by ++enter++.
This should bring up the Unix command-line interface for you to interact with
the Unix computing environment.

## Getting ready to install tools

Ubuntu comes with `apt` as the package manager, which is a convenient way to
list, search, install, update, and uninstall software and libraries in WSL.

After you have set up WSL, run the following:

```Bash
sudo apt update
```

What it does:

- `apt` is a command to install, upgrade, search, and uninstall software and
  other packages in Ubuntu.
- `apt update` asks `apt` to obtain the latest list of available packages from
  the Internet.
- `sudo` performs `apt update` with a super-user's level permission. This
  command may ask you to enter your password. (Note: super-user means
  administrator in Unix).
