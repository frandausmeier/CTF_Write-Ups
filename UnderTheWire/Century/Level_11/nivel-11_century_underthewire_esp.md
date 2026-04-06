> [Century](../README.md) | [UnderTheWire](../../README.md) | [CTF Write-Ups](../../../README.md)

# [Nivel 11](https://underthewire.tech/century)
> Century, Nivel 11.

> Español | [Inglés](./level-11_century_underthewire_eng.md).

> [Versión en PDF](https://drive.google.com/file/d/1FEG6xktH-XLUFwzc0CGHp8mtUhieQ-ms/view?usp=sharing).

<br>

---

<br>

## Descripción del _challenge_.
> La contraseña de Century12 es el nombre de un archivo oculto que está en uno de los subdirectorios de century11 (contacts, dektop, documents, downloads, favorites, music o videos).
>
> NOTAS IMPORTANTE
>
> - Excluir "desktop.ini".
> - La contraseña debe ser escrita en minúsculas sin importar como se encuentre en pantalla.

<br>

## Información dada por el _challenge_.
> Información útil dada por el _challenge_ actual o anteriores.
- _hostname_: " century.underthewire.tech ".
- _puerto_: " 22 " (2220).
- _usuario_: " century11 ".
- _contraseña_: " windowsupdates110 ".

<br>

---

<br>

## Procedimiento.

<br>

1. Para dar inicio al _challenge_, sabemos (de seguir la descripción del _challenge_) que tenemos que encontrar un archivo oculto en uno de los subdirectorios de  la carpeta de usuario century11 (" [...] archivo oculto que está en uno de los subdirectorios de century11 (contacts, dektop, documents, downloads, favorites, music o videos) "), sin considerar el archivo "desktop.ini" en la busqueda.\
Empezamos usando nuevamente [Get-ChildItem](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=Obtiene%20los%20elementos%20y%20elementos%20secundarios%20de%20una%20o%20varias%20ubicaciones%20especificadas), dado que en este caso buscamos un archivo y su nombre, en lugar de su contenido. Posterior a definir el primer cmdlet del comando, seguimos por especificar la ubicación en la cual vamos a llevar a cabo la búsqueda, "`` .. ``" desde _desktop_ ("`` C:\users\century11\desktop ``") obviamente. A partir de este punto, vamos a seguir buscando otras opciones y argumentos u otros cmdlets que puedan ayudarnos a seguir haciendo la búsqueda mas precisa.\
Vamos a iniciar con [-Recurse](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=False-,%2DRecurse), opción que determina que la búsqueda debe llevarse a cabo en la ubicación especificada y en todos los potenciales subdirectorios que esta ubicación pueda tener. También vamos a implementar [-File](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=%2DFile) para establecer que estamos buscando por en archivo y no una carpeta, y lo vamos a combinar con [-Hidden](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=%2DHidden) para orientar la ejecución del comando hacia archivos ocultos. La opción final disponible al cmdlet [Get-ChildItem](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=Obtiene%20los%20elementos%20y%20elementos%20secundarios%20de%20una%20o%20varias%20ubicaciones%20especificadas) que vamos a usar es [-Exclude](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=False-,%2DExclude), con la cual vamos a excluir de la búsqueda al archivo "desktop.ini, como el _challenge_ nos indica.\
Luego de todo esto, ya deberíamos tener al comando bien orientado hacia el archivo en cuestión. Lo que vamos a terminar agregando como última adición a este, va a ser el parametro "`` -ErrorAction ``" seguido por el valor "`` SilentlyContinue ``". Esto nos permite que el _output_ del comando no muestre errores no fatales (que no imposibiliten la ejecución del comando), dado que probablemente vamos a tener un buen par de estos, correspondientes a subdirectorios de century11 para los cuales no tenemos permisos de acceso. Por lo tanto, evitamos llenar la pantalla de mensajes de error todo lo posible para obtener un _output_ lo mas claro posible.\
Así es como el comando en su enteridad debería verse...

<br>

```


    PS C:\users\century11\desktop> Get-ChildItem .. -Recurse -File -Hidden ` 
    >> -Exclude "desktop.ini" -ErrorAction SilentlyContinue
    >>



        Directory: C\users\century11\AppData\Local\Microsoft\Windows

	Mode                LastWriteTime         Length Name
	----                -------------         ------ ----
	-a-h--        8/30/2018   3:11 AM           8192 UsrClass.dat 
	
    -a-hs-        8/30/2018   3:11 AM           8192 UsrClass.dat.LOG1                                             
	
    -a-hs-        8/30/2018   3:11 AM           8192 UsrClass.dat.LOG2                                             
	
    -a-hs-        8/30/2018   3:11 AM          65536 UsrClass.dat{d82669b3-abff-
    11e8-90ee-e14c26db97e8}.TM.blf     
	
    -a-hs-        8/30/2018   3:11 AM         524288 UsrClass.dat{d82669b3-abff-
    11e8-90ee-e14c26db97e8}.TMContainer00000000000000000001.regtrans-ms
    
	-a-hs-        8/30/2018   3:11 AM         524288 UsrClass.dat{d82669b3-abff-
    11e8-90ee-e14c26db97e8}.TMContainer00000000000000000002.regtrans-ms



    	Directory: C:\users\century11\Downloads

	Mode                LastWriteTime         Length Name         
	----                -------------         ------ ----         
	--rh--        8/30/2018   3:34 AM             30 secret_sauce



    	Directory: C:\users\century11

	Mode                LastWriteTime         Length Name
	----                -------------         ------ ----                                          
	-a-h--        3/30/2026   8:55 PM         262144 NTUSER.DAT
    
	-a-hs-        8/30/2018   3:11 AM          98304 ntuser.dat.LOG1                                                
	
    -a-hs-        8/30/2018   3:11 AM         126976 ntuser.dat.LOG2                                                
	
    -a-hs-        7/12/2020  10:55 PM          65536 NTUSER.DAT{0f893ee4-78e5-11e6-
    90dd-eefb07825ed9}.TM.blf        
	
    -a-hs-        6/14/2020   4:36 AM         524288 NTUSER.DAT{0f893ee4-78e5-11e6-
    90dd-eefb07825ed9}.TMContainer00000000000000000001.regtrans-ms 

	-a-hs-        7/12/2020  10:55 PM         524288 NTUSER.DAT{0f893ee4-78e5-11e6-
    90dd-eefb07825ed9}.TMContainer00000000000000000002.regtrans-ms 

	---hs-        8/30/2018   3:11 AM             20 ntuser.ini


```

<br>

- Como podemos observar, en el _output_ del comando que acabamos de ejecutar, obtenemos múltiples archivos ocultos bajo century11. Dicho esto, hay 1 solo de estos archivos que está ubicado en uno de los subdirectorios detallados en la description del _challenge_, siendo este "`` secret_sauce ``", dentro del directorio _downloads_ ( century12 : secret_sauce ).

<br>

---

<br>

### Adjuntos.

<br>

<p align="center">
  <img src="./attachments/level-11_century_underthewire.gif"/>
</p>

> Procedimiento entero.

<br>

---

