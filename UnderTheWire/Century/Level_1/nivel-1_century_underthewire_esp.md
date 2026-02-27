> [Century](../README.md) | [UnderTheWire](../../README.md) | [CTF Write-Ups](../../../README.md)

# [Nivel 1](https://underthewire.tech/century)
> Century Nivel 1

> Español | [Inglés](./level-1_century_underthewire_eng.md).

> [PDF version]().

<br>

---

<br>

## Descripción del _challenge_.
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

## Información dada por el _challenge_.
> Información de utilidad dada por el nivel anterior.
- _host_name_: " century.underthewire.tech ".
- _puerto_: " 22 " (2220).
- _usuario_: " century1 ".
- _contraseña_: " century1 ".

<br>

---

<br>

## Procedimiento.

<br>

1. .

<br>

```powershell

    PS C:\users\century1\desktop> $PSVersionTable 

```

<br>

---

<br>

2. .

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

---

<br>

### Adjuntos.

<br>

<p align="center">
  <img src="./attachments/level-1_century_underthewire.gif"/>
</p>

> Procedimiento entero.

<br>

---
