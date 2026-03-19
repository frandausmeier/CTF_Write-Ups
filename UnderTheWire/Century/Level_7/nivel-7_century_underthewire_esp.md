> [Century](../README.md) | [UnderTheWire](../../README.md) | [CTF Write-Ups](../../../README.md)

# [Nivel 7](https://underthewire.tech/century)
> Century Nivel 7

> Español | [Inglés](./level-7_century_underthewire_eng.md).

> [Versión en PDF](https://drive.google.com/file/d/1L31pgrcqPH-ZIN26Qa5LIxdCd-AmFmsM/view?usp=sharing).

<br>

---

<br>

## Descripción del _challenge_.
> La contraseña para Century8 es un archivo readme en algún lugar dentro de los directorios de contactos, escritorio, documentos, descargas, favoritos, musica o videos dentro del perfil de usuario correspondiente.
>
> NOTA IMPORTANTE
> - La contraseña tiene que ser ingresada completamente en minúsculas sin importar como se la encuentre.

<br>

## Información útil dada por el _challenge_.
> Información de utilidad dada por el nivel anterior.
- _host-name_: " century.underthewire.tech ".
- _puerto_: " 22 " (2220).
- _usuario_: " century7 ".
- _contraseña_: " 197 ".

<br>

---

<br>

## Procedimiento.

<br>

1. Dando comienzo a este nuevo nivel, mirando a la descripción del _challenge_, sabemos que la contraseña para Century8 debería estar en un archivo _readme_ dentro de alguno de los subdirectorios que estan bajo el usuario century8 (como contactos, escritorio, documentos, descargas, etc).\
Para iniciar la busqueda del archivo, podemos volver a usar [Get-ChildItem](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=Gets%20the%20items%20and%20child%20items%20in%20one%20or%20more%20specified%20locations.) indicando el lugar de inicio de la busqueda como la carpeta century detallando "`` .. ``" (obviamente desde _desktop_), dado que el archivo en cuestión debería estar dentro de uno de sus subdirectorios. También podemos agregar `` "*readme*" ``, como el posible nombre del archivo que vamos a estar buscando, y por último, "`` -Recurse ``" para indicar que la busqueda se lleve a cabo en todos los subdirectorios dentro de century8. Este comando, de estar correctamente redactado, nos debería dar el archivo en cuestión y su ubicación...

<br>

```powershell


	PS C:\users\century7\desktop> Get-ChildItem .. -Recurse "*readme*"


    Directory: C:\users\century7\Downloads


Mode                LastWriteTime         Length Name                                                          
----                -------------         ------ ----                                                          
-a----        8/30/2018   3:29 AM              7 Readme.txt


```

<br>

- Y así obtenemos el archivo en cuestión y su ubicación.

<br>

---


<br>

2. Para poder imprimir en pantalla los contenidos de este, podemos pasar el _output_ con un _pipe_ de redirección hacia el cmdlet [Get-Content](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.5#:~:text=Gets%20the%20content%20of%20the%20item%20at%20the%20specified%20location.), el equivalente directo que PowerShell tiene al comando [cat](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.5#:~:text=Windows%3A-,cat,-The%20Get%2DContent). Así que intentamos obtener el contenido del archivo de esa manera...

<br>

```powershell


	PS C:\users\century7\desktop> Get-ChildItem .. -Recurse "*readme*" | Get-Content
    7points


```

<br>

- y como podemos ver en el _output_ del ultimo comando, ahí obtenemos la contraseña para Century8, "`` 7points ``" (century8 : 7points).

<br>

---

<br>

### Attachments.

<br>

<p align="center">
  <img src="./attachments/level-7_century_underthewire.gif"/>
</p>

> Procedimiento entero.

<br>

---

