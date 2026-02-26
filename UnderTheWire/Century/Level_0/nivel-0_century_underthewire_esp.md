> [Century](../README.md) | [UnderTheWire](../../README.md) | [Informes y Reportes a CTFs](../../../README.md)

# [Nivel 0](https://underthewire.tech/century)
> Century, Nivel 0

> Español | [Inglés](https://github.com/frandausmeier/CTF_Write-Ups/blob/main/UnderTheWire/Century/Level_0/level-0_century_underthewire_eng.md).

> [Versión en PDF](https://drive.google.com/file/d/1pDUubStXZd9GDU3C0uBup0lDhfysbLS_/view?usp=drive_link).

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

## Procedimiento.

<br>

1. Usamos los detalles dados por el _challenge_, en este caso, el _host_ y el puerto, para logearnos correctamente al servidor. En este caso, vamos a usar esos datos usando [PuTTY](https://putty.software/) para ingresar con esos datos.

<br>

---

<br>

2. Una vez ingresamos los detalles a PuTTY, apretamos "Open" en la aplicación. Luego de esto, una vez abierto el terminal, ingresamos el _nombre-de-usuario_ y la _contraseña_ para poder logearnos (" century1 " tanto como usuario como contraseña). Estas se encuentran en el canal de Slack de UnderTheWire.

<br>

---

<br>

3. Y eso debería ser todo. Una vez entres al nivel 1 del _challenge_ con las credenciales correctas, al lado del _prompt_, deberías poder ver tu ubicación...

<br>

```

	PS C:\Users\Century1\desktop>

```

<br>

y así es como sabemos que nos logeamos efectivamente al nivel 1.

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

