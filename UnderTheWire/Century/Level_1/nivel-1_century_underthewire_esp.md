> [Century](../README.md) | [UnderTheWire](../../README.md) | [CTF Write-Ups](../../../README.md)

# [Nivel 1](https://underthewire.tech/century)
> Century Nivel 1

> Español | [Inglés](./level-1_century_underthewire_eng.md).

> [PDF version](https://drive.google.com/file/d/13NlgF-uUQt-jk5yyDaaiNiFTbwVGK1sX/view?usp=sharing).

<br>

---

<br>

## Descripción del _challenge_.
> La contraseña para Century2 es la _build version_ de la instancia específica de PowerShell instalada en tu sistema.
>
> - NOTA:
> - El formato es el siguiente: **xx.x.xxxxx.xxxx**\
> – Incluyendo todos los puntos\
> – Asegurarse de estar buscando la _build version_ y no la versión específica de PowerShell.
>
> IMPORTANTE:
> Una vez que creas haber completado el _challenge_ Century1, empezá una nueva conexión al servidor y logeate con el nombre de usuario "Century2" y la _build version_ a obtener en este nivel como la contraseña. De hacerlo exitosamente, cerrá la conexión de Century1 y empezá a resolver el _challenge_ Century2. Esta metodología se repite una y otra vez en los siguientes niveles hasta terminar el _wargame_.


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

1. Una vez tu logees correctamente al Nivel 1 de Century, tenemos la tarea de encontrar la _flag_ del nivel, la _build version_ de nuestra instancia específica de PowerShell, que a su vez, según la descripción del _challenge_, también sería la contraseña para logearnos al siguiente nivel.\
Luego de hacer un par de busquedas por un comando o comandos que nos permitan obtener esta información, terminamos por lo general llegando a la conclusión de que, la opción mas usadas y recomendada para este caso sería ``` $PSVersionTable ```, una variable automatica (de lectura unicamente) que guarda cierta información sobre PowerShell y nuestro sistema, como la versión de PowerShell (PSEdition), la edición de PowerShell (PSVersion), otras versiones de PowerShell compatibles con la nuestra (PSCompatibleVersions) y entre toda esa información, podemos encontrar la _build version_ de nuestra instancia específica de PowerShell (BuildVersion). Sabiendo esto, ejecutamos la variable para obtener la información.

<br>

```powershell

    PS C:\users\century1\desktop> $PSVersionTable 

```

<br>

---

<br>

2. Luego de haber ejecutado correctamente la variable, deberíamos poder ver un _output_ a ese comando parecido a este... 

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

- Y ahí es donde obtenemos la _flag_ de este nivel y la contraseña para el siguiente, en el valor de ``` BuildVersion ```. Así que, siguiendo la descripción del _challenge_ y la información que ya tenemos, deberíamos poder logearnos a Century2 usando "Century2" como usuario y "10.0.14393.8688" como contraseña, junto con los ya mencionados datos y detalles concernientes al _host_name_ y protocolo de comunicaciones para la conexión con el servidor que ya hablamos en el nivel anterior.

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
