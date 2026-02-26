> [Century](../README.md) | [UnderTheWire](../../README.md) | [Informes y Reportes a CTFs](../../../README.md)

# [Nivel 0](https://underthewire.tech/century)
> Century, Nivel 0

> Español | [Inglés](https://github.com/frandausmeier/CTF_Write-Ups/blob/main/UnderTheWire/Century/Level_0/level-0_century_underthewire_eng.md).

> [Versión en PDF](https://drive.google.com/file/d/1O_wDygpBFFe3OPuwgj-6QYUWDdhlRbBR/view?usp=sharing).

<br>

---

<br>

## Descripción del _challenge_.
> El objetivo de este nivel es logearte en el nivel. Hacer lo siguiente para lograrlo.
> 1. Obtener las credenciales en el canal #StartHere en nuestro Slack. Una vez dentro del canal, subir dentro de el hasta encontrar las credenciales.
> 2. Luego de obtener las credenciales, conectarse al servidor mediante SSH, para lo cual vas a necesitar un cliente de SSH como [PuTTY](https://putty.software/). El _host_ al cual nos vamos a estar conectando es century.underthewire.tech, en el puerto 22.
> 3. Paso siguiente, cuando se te pregunte, vas a tener que ingresar las credenciales encontradas en el canal de Slack #StartHere.
> 4. Uno sabe que se logeó correctamente cuando el servidor te muestre el _path_ “PS C:\Users\Century1\desktop>”.

<br>

## Información dada por el _challenge_.
- _hostname_: " century.underthewire.tech ".
- _puerto_: " 22 " (2220).
- _usuario_: " century1 ".
- _contraseña_: " century1 ".

<br>

---

<br>

## Procedure.

<br>

1. Vamos a comenzar usando los detalles que nos dieron en la descripción del _challenge_, en este caso, el _host-name_ y el puerto del servidor al cual nos tenemos que conectar, junto a una aplicación que sirva de cliente SSH para poder conectarnos al servidor desde Windows. En este caso, voy a estar usando [PuTTY](https://www.putty.org/) para poder conectarnos.

<br>

---

<br>

2. Luego de meternos en el canal de Slack, buscamos las credenciales de _login_, las cuales terminan siendo "century1" como usuario y como contraseña. Ya con todos los detalles necesarios para poder ingresar al nivel del _challenge_ y luego de instalar [PuTTY](https://www.putty.org/), abrimos la aplicación e ingresamos el "_host_name_" que tenemos por el _challenge_ en el apartado "Host Name (or IP address)". Como ultima medida, tenemos que asegurarnos que justo a la derecha de "Host Name (or IP address)", donde tenemos "Port". Acá tenemos que asegurarnos de que el numero ingresado indique que el procotolo de conexión va a ser SSH. El numero tiene que ser "22". También podemos asegurarnos de seleccionar SSH como el procotolo de conexión en el apartado "Connection type". Luego de haber ingresado todos los detalles y haber dado esas especificaciones, podemos comenzar la conexión.

<br>

---

<br>

3. Llegados a este punto, habiendo ingresado correctamente el _host-name_ y teniendo el protocolo correcto de conexión, deberiamos estar viendo un ventana de terminal abrirse luego de apretar _enter_. Esta es la ventana que indica que la conexión con el servidor comenzó, esta es la que te debería pedir las credenciales de logeo.

<br>

```
    
    Windows PowerShell
    Copyright (C) 2016 Microsoft Corporation. All rights reserved.
    
    Under the Wire... PowerShell Training for the People!
    PS C:/users/century1/desktop>

```

<br>

- Y este _output_ en el terminal es lo último que deberíamos estar viendo de haber ingresado las credenciales ("century1":"century1") correctas, habiendo ingresado al primer nivel del _challenge_.

<br>

---

<br>

### Adjunto.

<br>

<p align="center">
  <img src="./attachments/level-0_century_underthewire.gif"/>
</p>

> Procedimiento entero.

<br>

---

