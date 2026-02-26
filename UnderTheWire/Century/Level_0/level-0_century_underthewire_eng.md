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

1. Using the details given by the challenge, in this case, the host-name and the port, to log effectively to the server of the challenge. In my case, I am going to be doing it with [PuTTY](https://www.putty.org/) as a SSH client.

<br>

---

<br>

2. Once you have entered those details to PuTTY, press "Open" in the application. That's where the login for the server is going to get open and is going to ask you for a _user-name_ and _password_ that they are giving for this level on their Slack channel ( " _century1_ " for user-name and _password_).

<br>

---

<br>

3. And that should be it. Once you enter the correct credentials and it lets you in the server, you should see yourself in the directory 

<br>

```
    
    PS C:\Users\Century1\desktop>

```

<br>

- that is how you know you entered effectively to the Level 1.

<br>

---

<br>

### Attachments.

<br>

<p align="center">
  <img src="./attachments/level-0_century_underthewire.gif"/>
</p>

> Entire procedure.

<br>

---
