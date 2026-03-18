> [Century](../README.md) | [UnderTheWire](../../README.md) | [CTF Write-Ups](../../../README.md)

# [Nivel 6](https://underthewire.tech/century)
> Century Nivel 6

> English | [Spanish](./level-6_century_underthewire_eng.md).

> [PDF version](https://drive.google.com/file/d/1F9jq_GI7cLYv1MAcd2VJLmXf8vjx3Swt/view?usp=sharing).

<br>

---

<br>

## Descripción del _challenge_.
> La contraseña para Century7 es el numero de carpetas que hay en el escritorio.

<br>

## Información útil dada por el _challenge_.
> Información de utilidad dada por el nivel anterior.
- _host-name_: " century.underthewire.tech ".
- _puerto_: " 22 " (2220).
- _usuario_: " century6 ".
- _contraseña_: " underthewire3347 ".

<br>

---

<br>

## Procedimiento.

<br>

1. Desde este punto, y ya habiendonos logeado al nivel 6, siguiendo la descripción del _challenge_, sabemos que tenemos que llegar a obtener el numero de subdirectorios que hay en _desktop_, dado que aparentemente, esa es la contraseña para el nivel Century7.\
Para esto, podemos usar nuevamente [Get-ChildItem](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=Gets%20the%20items%20and%20child%20items%20in%20one%20or%20more%20specified%20locations.) casi de la misma manera en la que lo hicimos en el nivel 3 de Century. La única modificación en este caso, sería que en lugar de usar el argumento "`` -File ``", vamos a estar usando "`` -Directory ``" para poder orientar la busqueda en torno a los directorios. Dicho esto, colocamos el argumento luego de la ubicación de la busqueda, "`` . ``" (siempre desde _desktop_ obviamente).\
Finalmente, una vez mas agregamos una _pipe_ para redireccionar el _output_ que estaríamos obteniendo hasta ahora hacia el cmdlet [Measure-Object](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-7.5#:~:text=Calculates%20the%20numeric%20properties%20of%20objects%2C%20and%20the%20characters%2C%20words%2C%20and%20lines%20in%20string%20objects%2C%20such%20as%20files%20of%20text.), para poder generar el conteo númerico de propiedades de objetos que nos va a dar el numero de carpetas. Así sería como ejecutamos el comando completo... 

<br>

```powershell

	PS C:\users\century6\desktop> Get-ChildItem . -Directory | Measure-Object


	Count    : 197
	Average  :
	Sum      :
	Maximum  :
	Minimum  :
	Property :

```

<br>

- Y como podemos ver en el _output_ del comando, así es como obtenemos el numero de directorios en la carpeta _desktop_, siendo este numero "`` 197 ``" (century7 : 197).

<br>

---

<br>

### Adjunto.

<br>

<p align="center">
  <img src="./attachments/level-6_century_underthewire.gif"/>
</p>

> Procedimiento entero.

<br>

---

