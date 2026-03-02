> [Century](../README.md) | [UnderTheWire](../../README.md) | [CTF Write-Ups](../../../README.md)

# [Nivel 3](https://underthewire.tech/century)
> Century Nivel 3

> Español | [Inglés](./level-3_century_underthewire_eng.md).

> [PDF version](https://drive.google.com/file/d/1V-hMxgTwnwV1ufjSpI_BoaUisaDtwssy/view?usp=sharing).

<br>

---

<br>

## Descripción del _challenge_.
> La contraseña de Century4 es el numero de archivos en el escritorio.

<br>

## Información dada por el _challenge_.
> Información de utilidad dada por el nivel anterior.
- _host-name_: " century.underthewire.tech ".
- _puerto_: " 22 " (2220).
- _usuario_: " century3 ".
- _contraseña_: " invoke-webrequest443 ".

<br>

---

<br>

## Procedimiento.

<br>

1. Siempre me gusta comenzar revisando mi posición en la estructura de archivos, incluso cuando PowerShell siempre te la da una vez logearte en el servidor, además de darte la dirección en la estructura del _command prompt_.\
Para este propósito, podemos usar [Get-Location](https://www.pdq.com/powershell/get-location/) o podemos usar también [gl](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-location?view=powershell-7.5#notes:~:text=PowerShell%20incluye%20los%20siguientes%20alias%20para%20Get%2DLocation%3A) o [pwd](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-location?view=powershell-7.5#notes:~:text=PowerShell%20incluye%20los%20siguientes%20alias%20para%20Get%2DLocation%3A), los dos alias funcionales del cmdlet [Get-Location](https://www.pdq.com/powershell/get-location/) que funcionan exactamente igual que el cmdlet original.

<br>

- En el primer caso, usando [Get-Location](https://www.pdq.com/powershell/get-location/)...

```powershell

    PS C:\users\century2\desktop> Get-Location
    
    Path
    ----
    C:\users\century3\desktop

```

<br>

- usando la segunda opción, [gl](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-location?view=powershell-7.5#notes:~:text=PowerShell%20incluye%20los%20siguientes%20alias%20para%20Get%2DLocation%3A)...

```powershell

    PS C:\users\century2\desktop> gl
    
    Path
    ----
    C:\users\century3\desktop

```

<br>

- o la tercera opción, solo usando [pwd](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-location?view=powershell-7.5#notes:~:text=PowerShell%20incluye%20los%20siguientes%20alias%20para%20Get%2DLocation%3A)...

```powershell

    PS C:\users\century2\desktop> pwd
    
    Path
    ----
    C:\users\century3\desktop

```

<br>

---

<br>

2. Ahora que estamos seguros de nuestra localización en el sistema, y sabiendo que la contraseña para el siguiente nivel es el numero de carpetas en _desktop_, empezamos a buscar una alternativa en PowerShell a [ls](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=PowerShell%20incluye%20los%20siguientes%20alias%20para%20Get%2DChildItem) al comando de linux _shell_ y cmd.\
Si nos fijamos en la documentación de Microsoft, nos terminamos cuenta de que precisamente, el comando [ls](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=PowerShell%20incluye%20los%20siguientes%20alias%20para%20Get%2DChildItem) funciona en PowerShell como un cmdlet, pero lo hace solamente como un alias del cmdlet [Get-ChildItem](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5). Este último también tiene como alias a [gci](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=PowerShell%20incluye%20los%20siguientes%20alias%20para%20Get%2DChildItem) y a [dir](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=PowerShell%20incluye%20los%20siguientes%20alias%20para%20Get%2DChildItem) junto al ya mencionado [ls](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=PowerShell%20incluye%20los%20siguientes%20alias%20para%20Get%2DChildItem).
Ahora bien, este cmdlet o cualquiera de sus aliases no son suficientes por si solos para obtener un conteo de los contenidos de la carpeta, dado que su función es por default usandolo sin argumentos es dar como _output_ una impresa enlistada de los contenidos del directorio. Ese es el momento en el cual empezamos a mirar las distintas opciones y argumentos que el cmdlet tiene y también otros cmdlets que puedan ayudar a obtener dicho conteo.\
Cuando se trata de la búsqueda entre los contenidos de la carpeta, para poder hacer esta mas específica, de acuerdo a lo dicho en la descripción del _challenge_, vamos a estar detallando la localización en la que queremos que el comando sea aplicado, siendo esa ruta "``` ..\desktop\ ```". A eso, también le vamos a estar agregando el argumento ``` -File ```, para filtrar los contenidos un poco, indicando mediante el argumento que en el contenido de la carpeta, queremos excluir de los resultados todos los elementos que no sean archivos normales, como directorios, directorios ocultos o archivos de sistema.\
Con todo esto en consideración, lo que vamos a estar obteniendo como _output_ hasta este momento es una lista detallada de todos los archivos normales en esa ubicación, por eso vamos a continuar usando un _pipe_, para poder redireccionar este _output_ que el comando va a generar hasta este momento al cmdlet [Measure-Object](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-7.5#notes). Este cmdlet va a tomar la lista detallada de archivos de esa ubicación que tenemos generada hasta ese momento (todo lo que está antes del _pipe_) para aplicarle un conteo numerico, ya que este cmdlet es usado para realizar calculos sobre los valores de propiedad de cualquier objeto que uno le pase. 

<br>

- Así sería la ejecución del comando enteramente formado usando [GetChild-Item](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5)...

```powershell

	PS C:\users\century2\desktop> Get-ChildItem ../Desktop/ `
    >> -File | Measure-Object
    >>
    
    Count     : 123
    Average   :
    Sum       :
    Maximum   :
    Minimum   :
    Property  :

```
<br>

- usando [gci](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=PowerShell%20incluye%20los%20siguientes%20alias%20para%20Get%2DChildItem)...

```powershell

	PS C:\users\century2\desktop> gci ..\Desktop\ `
    >> -File | Measure-Object
    >>
    
    Count     : 123
    Average   :
    Sum       :
    Maximum   :
    Minimum   :
    Property  :

```

<br>

- o con [ls](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=PowerShell%20incluye%20los%20siguientes%20alias%20para%20Get%2DChildItem)...

```powershell

	PS C:\users\century2\desktop> ls ..\Desktop\ `
    >> -File | Measure-Object
	>>
    
	Count     : 123
    Average   :
    Sum       :
    Maximum   :
    Minimum   :
    Property  :

```

<br>

- Finalmente, como podemos ver en el _output_ de todos estos comandos, acá es donde obtenemos el numero de archivos en el directorio _desktop_, siendo este "123".\
Esta es mi contraseña para el nivel 4 de Century.

<br>

---

<br>

### Adjuntos.

<br>

<p align="center">
  <img src="./attachments/level-3_century_underthewire.gif"/>
</p>

> Procedimiento entero.

<br>

---

