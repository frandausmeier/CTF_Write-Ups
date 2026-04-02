> [General Skills challenges](../README.md) | [PicoCTF](../../README.md) | [CTF Write-Ups](../../../README.md)

# Super SSH
> General skills challenge, PicoCTF.

> English | [Spanish](./super-ssh_general-skills_picoctf_eng.md).

> [PDF version](https://drive.google.com/file/d/1cUURtdpwEeaEuG_skqBfNQhYp6RFhhwI/view?usp=sharing).

<br>

---

<br>

## Challenge description.
> Using a Secure Shell (SSH) is going to be pretty important.
>
> Additional details will be available after launching your challenge instance.
>

<br>

## Information given by the challenge.
- _hostname_: " titan.picoctf.net ".
- _user_: " ctf-player ".
- _port_: " 61084 ".
- _password_: " f3b61b38 ".

<br>

---

<br>

## Procedure.

<br>

1. Beginning with taking a look at the description of the challenge, we know that we have every single detail (talking about the host, the port, the user and the password) that we need to be able to login successfully to this challenge.\
We can go about this in two different ways, using the conventional structure of the command using the option " [-p](https://man7.org/linux/man-pages/man1/ssh.1.html#:~:text=%2Dp%20port,-Port) " to specify the port number in which we want the conexion to be done...

<br>

```


	PS C:\Users\PC03Mostrador> ssh ctf-player@titan.picoctf.net -p 61084
	The authenticity of host '[titan.picoctf.net]:61084
    ([3.139.174.234]:61084)' can't be established.
	ED25519 key fingerprint is 	SHA256:4S9EbTSSRZm32I+cdM5TyzthpQryv5kudRP9PIKT7XQ.
	This key is not known by any other names.
	Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
	Warning: Permanently added '[titan.picoctf.net]:61084' (ED25519) to the list of known hosts.
	ctf-player@titan.picoctf.net's password:
	Welcome ctf-player, here's your flag: picoCTF{s3cur3_c0nn3ct10n_3e293eea}
	Connection to titan.picoctf.net closed.


```
> ssh [user]@[host] -p [port-number]

<br>

- or detail the user and host separated from each other in the command, adding to the already mentioned command the " [-l](https://man7.org/linux/man-pages/man1/ssh.1.html#:~:text=%2Dl%20login%5Fname,-Specifies) " option, to be able to specify the user.

<br>

```


	PS C:\Users\PC03Mostrador> ssh titan.picoctf.net -l ctf-player -p 61084
	ctf-player@titan.picoctf.net's password:
	Welcome ctf-player, here's your flag: picoCTF{s3cur3_c0nn3ct10n_3e293eea}
	Connection to titan.picoctf.net closed.


```
> ssh [host] -l [user] -p [port-number]

<br>

- Following either one of those two options should be enough to be able to succesfully login to the challenge and obtain its flag (" picoCTF{s3cur3_c0nn3ct10n_3e293eea} ").

<br>

---

<br>

### Attachments.

<br>

<p align="center">
  <img src="./attachments/super-ssh_general-skills_picoctf.gif"/>
</p>

> Entire procedure.

<br>

---

