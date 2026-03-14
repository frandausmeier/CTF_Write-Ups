> [Century](../README.md) | [UnderTheWire](../../README.md) | [CTF Write-Ups](../../../README.md)

# [Level 4](https://underthewire.tech/century)
> Century Level 4

> English | [Spanish](./nivel-4_century_underthewire_esp.md).

> [PDF version](https://drive.google.com/file/d/1Gjimn6U64S2z96wIMLRwA8xiXRfZJ0Mq/view?usp=sharing).

<br>

---

<br>

## Challenge description.
> The password for Century4 is the number of files on the desktop.

<br>

## Information given by the challenge.
> Useful information given by the previous level.
- _hostname_: " century.underthewire.tech ".
- _port_: " 22 " (2220).
- _user_: " century4 ".
- _password_: " 123 ".

<br>

---

<br>

## Procedure.

<br>

1. After the last level, we know that we can use the cmdlet [Get-ChildItem](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5)
 to print the contents of a given directory or location in the file tree. In addition to this cmdlet, by following the description of the challenge, we know that the password for the next level is the name of a file that is under a directory that has spaces in it´s name, that is under the desktop folder.\
As we said, we use [Get-ChildItem](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5), and we add it the `` "* *" `` addition, to indicate that we are looking for files or directories with spaces in their name under that directory. We also add the [-Recurse](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=Gets%20the%20items%20in%20the%20specified%20locations%20and%20in%20all%20child%20items%20of%20the%20locations.) option. Knowing that we are looking for a folder that has the file in question inside, we use [-Recurse](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=Gets%20the%20items%20in%20the%20specified%20locations%20and%20in%20all%20child%20items%20of%20the%20locations.) to guarantee that we include all child items of the locations we initially obtain in the print. Fully going over all of this, we execute the command...

<br>

```powershell

	PS C:\users\century2\desktop> Get-ChildItem "* *" -Recurse


        Directory: C:\users\century4\desktop\Can You Open Me


    Mode                LastWriteTime         Length Name                                                                
    ----                -------------         ------ ----                                                                
    -a----        4/27/2025   7:57 PM             24 15768

```

<br>

- And that's how we obtain the file and its name on the output. Following this, under desktop, there's is a folder called "`` Can You Open Me ``" (that obviously has spaces in its name) that, in it's contents, has a file named "`` 15768 ``". And there we have the credentials for Century's level 5 (century5 : 15768).

<br>

---

<br>

### Attachments.

<br>

<p align="center">
  <img src="./attachments/level-4_century_underthewire.gif"/>
</p>

> Entire procedure.

<br>

---

