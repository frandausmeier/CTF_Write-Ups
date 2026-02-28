> [Century](../README.md) | [UnderTheWire](../../README.md) | [CTF Write-Ups](../../../README.md)

# [Nivel 2](https://underthewire.tech/century)
> Century Nivel 2

> Español | [Inglés](./level-2_century_underthewire_eng.md).

> [PDF version](https://drive.google.com/file/d/1jDEVC4fChdFqjlGaRhmkbEcJorWNxM1D/view?usp=sharing).

<br>

---

<br>

## Descripción del _challenge_.
> La contraseña para Century3 es el nombre del cmdlet que viene por defecto que nos permite ejecutar acciones del tipo wget MAS el nombre del archivo en el escritorio.
>
> - NOTA IMPORTANTE:
> - Si el nombre del cmdlet es "get-web" y el nombre del archivo en la carpeta _desktop_ es "1234", la contraseña sería "get-web1234".
> - La contraseña va a ser escrita en minúsculas en todos los casos sin importar como aparece en la pantalla.

<br>

## Información dada por el _challenge_.
> Información de utilidad dada por el nivel anterior.
- _host-name_: " century.underthewire.tech ".
- _puerto_: " 22 " (2220).
- _usuario_: " century2 ".
- _contraseña_: " 10.0.14393.8688 ".

<br>

---

<br>

## Procedimiento.

<br>

1. Luego de un par de búsquedas, llegamos a la conclusión de que la cosa mas cercana a una alternativa de [wget](https://man7.org/linux/man-pages/man1/wget.1.html) en PowerShell es el cmdlet [Invoke-WebRequest](https://www.pdq.com/powershell/invoke-webrequest/).\
Además de referir directamente a el en el terminal, uno también puede referirse a el usando el alias "iwr" para usarlo. Podemos chequear por la presencia de ambos en el sistema usando el cmdlet [Get-Command](https://www.pdq.com/powershell/get-command/).

<br>

```powershell

    PS C:\users\century2\desktop> Get-Command Invoke-WebRequest

	CommandType     Name                                               	Version    Source
	-----------     ----                                               -------    ------
	Cmdlet          Invoke-WebRequest                                  3.1.0.0    Microsoft.PowerShell.Utility


	PS C:\users\century2\desktop> Get-Command iwr

	CommandType     Name                                               Version    Source
	-----------     ----                                               -------    ------
	Alias           iwr -> Invoke-WebRequest

```

<br>

- Así como tambien podemos obtener una descripción completa de la variable usando tanto el nombre completo como el alias usando [Get-Help](https://www.pdq.com/powershell/get-help/).

<br>

```powershell

	PS C:\users\century2\desktop> Get-Help iwr

	NAME
    	Invoke-WebRequest

	SYNOPSIS
    	Gets content from a web page on the Internet.


	SYNTAX
    	Invoke-WebRequest [-Uri] <Uri> [-Body <Object>] [-Certificate <X509Certificate>] [-CertificateThumbprint <String>]
    	[-ContentType <String>] [-Credential <PSCredential>] [-DisableKeepAlive] [-Headers <IDictionary>] [-InFile <String>]
    	[-MaximumRedirection <Int32>] [-Method {Default | Get | Head | Post | Put | Delete | Trace | Options | Merge | Patch}]
    	[-OutFile <String>] [-PassThru] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials]
    	[-SessionVariable <String>] [-TimeoutSec <Int32>] [-TransferEncoding {chunked | compress | deflate | gzip | identity}]
    	[-UseBasicParsing] [-UseDefaultCredentials] [-UserAgent <String>] [-WebSession <WebRequestSession>]
    	[<CommonParameters>]


	DESCRIPTION
    	The Invoke-WebRequest cmdlet sends HTTP, HTTPS, FTP, and FILE requests to a web page or web service. It parses the
    response and returns collections of forms, links, images, and other significant HTML elements.

    	This cmdlet was introduced in Windows PowerShell 3.0.


	RELATED LINKS
    	Online Version: http://go.microsoft.com/fwlink/?LinkId=821826
    	Invoke-RestMethod
    	ConvertFrom-Json
    	ConvertTo-Json

	REMARKS
    	To see the examples, type: "get-help Invoke-WebRequest -examples".
    	For more information, type: "get-help Invoke-WebRequest -detailed".
    	For technical information, type: "get-help Invoke-WebRequest -full".
    	For online help, type: "get-help Invoke-WebRequest -online"

```

<br>

---

<br>

2. Al saber esto, y teniendo nuestro ubicación ya por defecto de la instancia en la carpeta "desktop", usamos [ls](https://man7.org/linux/man-pages/man1/ls.1.html) para tratar de ver el nombre del archivo al cual la descripción del _challenge_ nos está guiando.

<br>

```powershell

	PS C:\users\century2\desktop> ls


    	Directory: C:\users\century2\desktop


	Mode                LastWriteTime         Length Name
	----                -------------         ------ ----
	-a----        8/30/2018   3:29 AM            693 443

```

<br>

- Y es la ejecución de este ultimo comando, la que nos da en su _output_ el nombre del archivo, siendo este "443".

<br>

---

<br>

3. Al tener todos los datos necesarios para llegar a la contraseña en cuestión, seguimos el formato que nos dieron en la descripción del _challenge_. Dados el nombre completo del cmdlet de PowerShell equivalente a [wget](https://man7.org/linux/man-pages/man1/wget.1.html) en función y el nombre del único archivo en la carpeta _desktop_, llegamos a la conclusió de que la contraseña de Century3 debería ser " invoke-webrequest443 ". Cerramos cesión en Century2 y probamos logearnos a Century3 con ese usuario y la contraseña ya mencionada...

<br>

```powershell

	PS C:\Users\fdm> ssh century3@century.underthewire.tech
	century3@century.underthewire.tech's password: 
	

	Windows PowerShell
	Copyright (C) 2016 Microsoft Corporation. All rights reserved.
	
	Under the Wire... PowerShell Training for the People!
	PS C:\users\century3\desktop>

```

<br>

- Y ese debería ser el _output_ final que nos indica que ya ingresamos correctamente a Century3.

<br>

---

<br>

### Adjuntos.

<br>

<p align="center">
  <img src="./attachments/level-2_century_underthewire.gif"/>
</p>

> Procedimiento entero.

<br>

--
