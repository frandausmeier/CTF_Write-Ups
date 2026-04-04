> [Century](../README.md) | [UnderTheWire](../../README.md) | [CTF Write-Ups](../../../README.md)

# [Nivel 10](https://underthewire.tech/century)
> Century, Nivel 10.

> Español | [Inglés](./nivel-10_century_underthewire_eng.md).

> [Versión en PDF](https://drive.google.com/file/d/1FNt0bsQoedl0Gast1kCvSCZH1O-pZWrq/view?usp=sharing).

<br>

---

<br>

## Descripción del _challenge_.
> La contraseña para Century11 es la decima y octava palabra (en ese orden) de la descripción del servicio de _Windows Update services_, combinada junto a el nombre del archivo que está en _desktop_.
>
> NOTA IMPORTANTE
>
> - La contraseña debe ser escrita en minúsculas sin importar como se encuentre en pantalla.
> - Si la decima y la octava palabra de la descripción del servicio es "apple" y "juice" (respectivamente) y el nombre del archivo en el escritorio es "88", la contraseña sería "applejuice88".

<br>

## Información útil dada por el _challenge_.
> Información de utilidad dada por el nivel actual o anteriores.
- _host-name_: " century.underthewire.tech ".
- _puerto_: " 22 " (2220).
- _usuario_: " century10 ".
- _contraseña_: " pierid ".

<br>

---

<br>

## Procedimiento.

<br>

1. Al dar inicio a este _challenge_, comenzamos como siempre por revisar la descripción de este, y es ahí donde nos hacen saber que para obtener la contraseña de Century 11 necesitamos combinar la decima y la octava palabra del _Windows Update service_ junto con el nombre de un archivo que debería estar guardado en _desktop_.\
Como primer paso, considerando que desde que nos logeamos estamos en _desktop_, podemos usar [Get-ChildItem](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=Obtiene%20los%20elementos%20y%20elementos%20secundarios%20de%20una%20o%20varias%20ubicaciones%20especificadas) para obtener el nombre del archivo del cual nos avisó la descripción del _challenge_...

<br>

```powershell


	PS C:\users\century10\desktop> Get-ChildItem


        Directory: C:\users\century10\desktop


    Mode                LastWriteTime         Length Name
    ----                -------------         ------ ----   
    -a----        8/30/2018   3:34 AM             43 110


```

<br>

- Y así obtenemos la primer parte de la contraseña, el nombre del archivo que está en _desktop_, "`` 110 ``".

<br>

---

<br>

2. Ahora bien, cuando se trata de las otras dos palabras que están en la descripción del _Windows Update service_, no podemos empezar usando el cmdlet [Get-Content](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.5#:~:text=Obtiene%20el%20contenido%20del%20elemento%20en%20la%20ubicaci%C3%B3n%20especificada.), dado que este está diseñado para funcionar con _file system items_, como archivos de texto o logs, y los servicios de Windows son programas ejecutable que corren en el background. Siguiendo esa logica, este cmdlet nunca va a ser de utilidad para leer los contenidos de servicios de Windows. Ahora que sabemos esto, podemos tratar con [Get-CimInstance](https://learn.microsoft.com/es-es/powershell/module/cimcmdlets/get-ciminstance?view=powershell-7.5#:~:text=Obtiene%20las%20instancias%20CIM%20de%20una%20clase%20de%20un%20servidor%20CIM), un cmdlet que nos permite obtener información de clases CIM (_Common Information Model_). Estos elementos son muy importantes cuando se trata de definir recursos manejados por el sistema, como software, hardware y componentes del sistema operativo. Este cmdlet es de mucha importacia cuando necesitamos manejar y consultar información del sistema.\
Luego de definir el cmdlet, seguimos usando su opción [-ClassName](https://learn.microsoft.com/es-es/powershell/module/cimcmdlets/get-ciminstance?view=powershell-7.5#:~:text=False-,%2DClassName) para definir el tipo de clase CIM con el cual estamos tratando. Dado que estamos hablando de un servicio de Windows, la clase del objeto que estamos buscando sería "`` Win32_Service ``" y el nombre específico del servicio que estamos buscando es "`` wuauserv ``", por lo que también procedemos a aclarar este usando la opción [-Filter](https://learn.microsoft.com/es-es/powershell/module/cimcmdlets/get-ciminstance?view=powershell-7.5#:~:text=%2DFilter,-Specifies%20a%20where.).\
Llegados a este punto, deberíamos tener el servicio bien especificado, tanto por tipo (`` -ClassName Win32_Service ``), como por nombre (`` -Filter "Name='wuauserv'" ``), por lo que podemos seguir especificando la propiedad que queremos obtener de este objeto. Para esto, usamos un a barra vertical (`` | ``) para redireccionar el objeto que encontramos en la primer mitad del comando hacia [Select-Object](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7.5#:~:text=Selecciona%20objetos%20o%20propiedades%20de%20objeto), y especificar la busqueda hacia la descripción del servicio (`` Select-Object Name, Description ``).\
Así es como el comando entero se vería ejectuado correctamente...

<br>

```powershell


	PS C:\users\century10\desktop> Get-CimInstance -ClassName Win32_Service `
    >> -Filter "Name='wuauserv'" | Select-Object Name, Description
    >>

    Name       Description
    ----       -----------
    wuauserv   Enables the detection, download, and installation of updates for Windows 
               and other programs. If this serv...


```

<br>

- Y finalmente obtenemos el nombre y la descripción del servicio. La decima palabra siendo "`` Windows ``" y la octava "`` updates ``", y como ya sabemos, el nombre del archivo en _desktop_ es "`` 110 ``", por lo tanto, la contraseña para Century11 correctamente formateada de acuero con la descripción del _challenge_ sería "`` windowsupdates110 ``" (century11 : windowsupdates110).

<br>

---

<br>

### Adjunto.

<br>

<p align="center">
  <img src="./attachments/level-10_century_underthewire_1.gif"/>
</p>

> Usos de [Get-Location](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-location?view=powershell-7.5#:~:text=Obtiene%20informaci%C3%B3n%20sobre%20la%20ubicaci%C3%B3n%20de%20trabajo%20actual%20o%20una%20pila%20de%20ubicaciones) y [Get-ChildItem](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=Obtiene%20los%20elementos%20y%20elementos%20secundarios%20de%20una%20o%20varias%20ubicaciones%20especificadas).

<br>

<br>

<br>

<p align="center">
  <img src="./attachments/level-10_century_underthewire_2.gif"/>
</p>

> Comando que tiene el uso de [Get-CimInstance](https://learn.microsoft.com/es-es/powershell/module/cimcmdlets/get-ciminstance?view=powershell-7.5#:~:text=Obtiene%20las%20instancias%20CIM%20de%20una%20clase%20de%20un%20servidor%20CIM) y [Select-Object](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7.5#:~:text=Selecciona%20objetos%20o%20propiedades%20de%20objeto).

<br>

---

