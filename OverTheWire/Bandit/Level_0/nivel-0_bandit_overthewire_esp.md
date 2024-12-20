
# [Nivel 0](https://overthewire.org/wargames/bandit/bandit0.html) | [Bandit](https://github.com/frandausmeier/CTF_Write-Ups/tree/main/OverTheWire/Bandit) | [OverTheWire](https://github.com/frandausmeier/CTF_Write-Ups/blob/main/OverTheWire/README.es.md)

> Español | [Inglés](https://github.com/frandausmeier/CTF_Write-Ups/blob/main/OverTheWire/Bandit/Level_0/level-0_bandit_overthewire_eng.md) 

> [versión en PDF](https://github.com/frandausmeier/CTF_Write-Ups/blob/main/OverTheWire/Bandit/Level_0/nivel-0_bandit_overthewire_esp.pdf)

-----

<br>

- ## Descripción del _challenge_.
	> El objetivo de este nivel es el conseguir logear al juego usando SSH. El _host_ al cual necesitás conectarte es bandit.labs.overthewire.org, en su puerto 2220 (22). Las credenciales para poder conseguir ingresar al nivel 1 serían "bandit0" tanto en el caso de usuario como en el de la contreña. Una vez correctamente logeado, ir al archivo principal del Nivel 1 para poder obtener las instrucciones sobre como pasar ese nivel.

<br>

- ## Información dada por el _challenge_.
	- _hostname_: " bandit.labs.overthewire.org ".
	- _puerto_: " 22 " (2220).
	- _usuario_: " bandit0 ".
	- _contraseña_: " bandit0 ".

<br>

-----

<br>

- ## Procedimiento.

<br>

1. Usar los datos dados por la descripción del _challenge_ para poder completar el comando SSH con el cual vamos a poder logearnos al correspondiente server para el _challenge_, siguiendo la estructura del comando SSH:

<br>

```
	bandit0@bandit:~$ ssh user@host_name -p 2220
```

<br>

* donde la opción "**-p**", nos permite especificar el puerto para la conección del login, y el numero "**2220**", que indica el puerto de default (22) en la implementación del procolo de red SSH:

<br>

``` 
	bandit0@bandit:~$ ssh bandit0@bandit.labs.overthewire.org -p 2220 
```

<br>

2. Luego de ejecutar el comando correctamente, se te debería pedir la contraseña por parte del server del _wargame_ para poder logearte e ingresar al primer nivel, siendo la contraseña para el ingreso "**bandit0**", y eso debería ser todo. 

<br>

-----

<br>

- ## Demostración.

<br>

<p align="center">
  <img src="./attachments/level-0_bandit_overthewire.gif" />
</p>

<br>

-----
