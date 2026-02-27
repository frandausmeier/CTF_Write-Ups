> [Century](../README.md) | [UnderTheWire](../../README.md) | [CTF Write-Ups](../../../README.md)

# [Level 1](https://underthewire.tech/century)
> Century Level 1

> English | [Spanish](./nivel-1_century_underthewire_esp.md).

> [PDF version](https://drive.google.com/file/d/16FpIrtXWdYzoHQR_3O1tZHyRkAC-2-fS/view?usp=sharing).

<br>

---

<br>

## Challenge description.
> The password for Century2 is the build version of the instance of PowerShell installed on this system.
>
> - NOTE:
> - The format is as follows: **xx.x.xxxxx.xxxx**\
> – Include all periods\
> – Be sure to look for build version and NOT PowerShell version
>
> IMPORTANT:
> Once you feel you have completed the Century1 challenge, start a new connection to the server, and log in with the username of Century2 and this password will be the answer from Century1. If successful, close out the Century1 connection and begin to solve the Century2 challenge. This concept is repeated over and over until you reach the end of the game.

<br>

## Information given by the challenge.
> Useful information given by the previous level.
- _hostname_: " century.underthewire.tech ".
- _port_: " 22 " (2220).
- _user_: " century1 ".
- _password_: " century1 ".

<br>

---

<br>

## Procedure.

<br>

1. Once we have successfully logged in to Century's Level 1, we are tasked with founding the flag of the level and the password for Century's Level 2, the build of our current version of PowerShell.\
Knowing this, and after a while making a couple of searches, looking for a command or commands that allows to get this information, we usually arrive at the conclusion that, the most used and recommended option for this case would be ``` $PSVersionTable ```, a reading only automatic variable that stores some information about PowerShell and our system, including the PowerShell version (PSVersion), the edition of PowerShell (PSEdition), other PowerShell compatible versions with ours (PSCompatibleVersions) and amongst all of that information, we can find the PowerShell build version (BuildVersion). So, with this in mind, we execute that variable to get the information. 

<br>

```powershell

    PS C:\users\century1\desktop> $PSVersionTable 

```

<br>

---

<br>

2. After correctly executing the variable, we should some output that resembles something like this...

<br>

```powershell

    Name                                     Value
    ----                                     ----
	PSVersion                                5.1.14393.8688
    PSEdition                                Desktop
    PSCompatibleVersions                     {1.0, 1.0, 3.0, 4.0...}
    BuildVersion                             10.0.14393.8688
    CLRVersion                               4.0.30319.42000
    WSManStackVersion                        3.0
    PSRemotingProtocolVersion                2.3
    SerializationVersion                     1.1.0.1

```

<br>

- And that's where we get the build version of our PowerShell version. So, following this, our password for the Level 2 is "10.0.14393.8688", we will be able to log in to Level 2 using it, of course, alongside "century2" as the user, and the already mentioned host_name and communication protocol details that we have discussed in the last level.

<br>

---

<br>

### Attachments.

<br>

<p align="center">
  <img src="./attachments/level-1_century_underthewire.gif"/>
</p>

> Entire procedure.

<br>

---
