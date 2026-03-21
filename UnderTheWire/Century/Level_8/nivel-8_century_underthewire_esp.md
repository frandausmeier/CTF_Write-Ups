> [Century](../README.md) | [UnderTheWire](../../README.md) | [CTF Write-Ups](../../../README.md)

# [Nivel 8](https://underthewire.tech/century)
> Century Nivel 8

> Español | [Inglés](./level-8_century_underthewire_eng.md).

> [Versión en PDF](https://drive.google.com/file/d/1wAoI8W7sSuJELI5PRG2WgS0jR3v4KqUw/view?usp=sharing).

<br>

---

<br>

## Descripción del _challenge_.
> La contraseña de Century9 es el numero de entradas unicas del archivo en el escritorio.

<br>

## Información útil dada por el _challenge_.
> Información de utilidad dada por el nivel anterior.
- _host-name_: " century.underthewire.tech ".
- _puerto_: " 22 " (2220).
- _usuario_: " century8 ".
- _contraseña_: " 7points ".

<br>

---

<br>

## Procedimiento.

<br>

1. Comenzamos este nuevo nivel sabiendo que la contraseña para Century9 es el numero de entradas únicas de datos en un archivo que está guardado en el escritorio. Hacemos un uso rapido de [Get-ChildItem](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=Gets%20the%20items%20and%20child%20items%20in%20one%20or%20more%20specified%20locations.) para corroborar por la presencia del archivo y ver su nombre.

<br>

```powershell


	PS C:\users\century7\desktop> Get-ChildItem
    
    	Directory: C:\users\century8\desktop

	Mode                LastWriteTime         Length Name
	----                -------------         ------ ----             
    
	-a----        8/30/2018   3:33 AM          15858 unique.txt


```

<br>

- Ahí es donde lo ubicamos, "`` unique.txt ``".

<br>

---

<br>

2. Para obtener una impresión inicial de los contenidos del archivo, podemos usar [Get-Content](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.5#:~:text=Gets%20the%20content%20of%20the%20item%20at%20the%20specified%20location.) nuevamente, como en el nivel anterior. El problema con esto, es que solamente con el uso por defecto de ese cmdlet, solo esteríamos obteniendo un _print_ de todas las líneas del documento, ni siquiera estaríamos obteniendo las líneas únicas. Con el propósito de ir afinando la búsqueda, para acercarnos a obtener una cuenta numérica del numero de estas líneas, vamos a tener que agregar un par de cmdlets adicionales para poder llegar a ese punto, empezando por [Get-Unique](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-unique?view=powershell-7.5#:~:text=Returns%20unique%20items%20from%20a%20sorted%20list.).\
[Get-Unique](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-unique?view=powershell-7.5#:~:text=Returns%20unique%20items%20from%20a%20sorted%20list.) es el cmdlet equivalente de PowerShell a [uniq](https://man7.org/linux/man-pages/man1/uniq.1.html#:~:text=uniq%20%2D%20report%20or%20omit%20repeated%20lines), comando que filtra y retorna _items_, o lineas unicas dentro de una lista.  

<br>

```powershell


	PS C:\users\century7\desktop> Get-Content .\unique.txt  | Get-Unique
	recreatively
	proboscidean
	commenceable
	simptico
	zoon
	glacises
	rationaliser
	unlustful
	catnapping
	arboreta
    
    [...]


```

<br>

- Através de esto, deberíamos estar obteniendo una impresión de las lineas de ese archivo que representan entradas de datos unícas al documento en sí.

<br>

---

<br>

3. Finalmente, habiendo filtrado y teniendo únicamente las líneas unicas del documento, podemos pasarlas mediante un _pipe_ de redirección por el cmdlet [Measure-Object](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-7.5#notes), para poder obtener el conteo numerico de esas lineas que ya tenemos filtradas.

<br>

```powershell


	PS C:\users\century8\desktop> Get-Content .\unique.txt `
    >> | Get-Unique | Measure-Object
    >>
    
	Count    : 696
	Average  :                           
	Sum      :                               
	Maximum  :                               
	Minimum  :                               
	Property :


```

<br>

- y así es como obtenemos la _flag_ de este nivel y la contraseña del siguiente. El numero y contraseña en cuestión siendo "`` 696 ``" (century9 : 696).

<br>

---

<br>

### Adjunto.

<br>

<p align="center">
  <img src="./attachments/level-8_century_underthewire.gif"/>
</p>

> Procedimiento entero.

<br>

---

