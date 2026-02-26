> [Century](../README.md) | [UnderTheWire](../../README.md) | [CTF Write-Ups](../../../README.md)

# [Level 0](https://underthewire.tech/century)
> Century, Level 0

> English | [Spanish](https://github.com/frandausmeier/CTF_Write-Ups/blob/main/UnderTheWire/Century/Level_0/nivel-0_century_underthewire_esp.md).

> [PDF version](https://drive.google.com/file/d/1UBVA2lnsoyYOrJKaFXTq6g4TRtGLFD10/view?usp=drive_link).

<br>

---

<br>

## Challenge description.
> The goal of this level is to log into the game. Do the following in order to achieve this goal.
> 1. Obtain the initial credentials via the #StartHere channel on our Slack (link). Once you are in the channel, scroll to the top to see the credentials.
> 2. After obtaining the credentials, connect to the server via SSH. You will need an SSH client such as Putty. The host that you will be connecting to is century.underthewire.tech, on port 22.
> 3. When prompted, use the credentials for the applicable game found in the #StartHere Slack channel.
> 4. You have successfully connected to the game server when your path changes to “PS C:\Users\Century1\desktop>”.

<br>

## Information given by the challenge.
- _hostname_: " century.underthewire.tech ".
- _port_: " 22 " (2220).
- _user_: " century1 ".
- _password_: " century1 ".

<br>

---

<br>

## Procedure.

<br>

1. We are going to start by using the main details given in the description of the challenge, in this case, the host-name and the port of the server to which we have to log in, alongside a SSH client to be able to log in from Windows with those details and the credentials we have to search in the Slack chanel that the site has. In this case, I am going to be using [PuTTY](https://www.putty.org/) as the SSH client.

<br>

---

<br>

2. After getting into the Slack channel, we arrive at the section that has the login credentials, these being "century1" as the user and as the password. So, with this in mind, after installing [PuTTY](https://www.putty.org/), we open it and enter the host-name that we have for the challenge in the "Host Name (or IP address)" part of the application. We also have to make sure that right next to the "Host Name (or IP address)" box, where we have the "Port" box, the number there indicates the SSH protocol, in this case, 22. We can also make sure SSH is the protocol selected as the communication type in "Connection type". After these specifications, we can press enter to start the connection.

<br>

---

<br>

3. At this point, with the correct host-name of the server and protocol for the connection, you should be seeing a terminal window being open. This is the one that is going to query you for the credentials to login.\

<br>

```
    
    PS C:\Users\Century1\desktop>

```

<br>

And that is what you should be seeing at last if the credentials for the level of the challenge ("century1":"century1") have been entered correctly, that's how you know you have logged in correctly.

<br>

---

<br>

### Attachments.

<br>

<p align="center">
  <img src="./attachments/level-0_century_underthewire.gif"/>
</p>

> Entire procedure.

---
