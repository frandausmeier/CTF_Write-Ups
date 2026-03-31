> [Century](../README.md) | [UnderTheWire](../../README.md) | [CTF Write-Ups](../../../README.md)

# [Nivel 9](https://underthewire.tech/century)
> Century Nivel 9

> Español | [Inglés](./level-9_century_underthewire_eng.md).

> [Versión en PDF](https://drive.google.com/file/d/17G66grx1l-mwy9ENPQamvgNvTAqXy4oo/view?usp=sharing).

<br>

---

<br>

## Descripción del _challenge_.
> La contraseña para Century10 es la palabra numero 161 dentro del archivo que está en el escritorio.
>
> NOTA IMPORTANTE
>
> - La contraseña debe ser escrita siempre en minúsculas, independientemente de como aparezca en pantalla.

<br>

## Información útil dada por el _challenge_.
> Información de utilidad dada por el nivel anterior.
- _host-name_: " century.underthewire.tech ".
- _puerto_: " 22 " (2220).
- _usuario_: " century9 ".
- _contraseña_: " 696 ".

<br>

---

<br>

## Procedimiento.

<br>

1. De inicio, mirando la descripción del _challenge_, nos enteramos que la contraseña para Century10 es la palabra numero 161 dentro de un archivo que está en la carpeta _desktop_.\
Ya estando en la carpeta _desktop_ desde que nos logeamos, ejecutamos [Get-ChildItem](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=Obtiene%20los%20elementos%20y%20elementos%20secundarios%20de%20una%20o%20varias%20ubicaciones%20especificadas) para ver el archivo en cuestión con el que vamos a estar trabajando...

<br>

```powershell


    PS C:\users\century7\desktop> Get-ChildItem


    	Directory: C:\users\century9\desktop
    
    
	Mode                LastWriteTime         Length Name
    ----                -------------         ------ ----
    -a----        8/30/2018   3:34 AM           2131 Word_File.txt
    
    
```

<br>

- y ahí lo encontramos, "`` Word_File.txt ``", un archivo de texto que, en teoría, tiene en sus contenidos la contraseña.

<br>

---

<br>

2. Ahora, teniendo el archivo en cuestión a la vista, hacemos uso del cmdlet [Get-Content](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.5#:~:text=Obtiene%20el%20contenido%20del%20elemento%20en%20la%20ubicaci%C3%B3n%20especificada), para poder bien los contenidos del archivo y evaluar desde ahí como es que se prosigue en la busqueda de la contraseña.

<br>

```powershell


    PS C:\users\century7\desktop> Get-Content .\Word_File.txt
    larceny epibole ampliate trecentos psychotoxic sybarism shatterwit cartilaginification crenulation splenification free
	spac untragicalness renovater smirch historism tymbal nonobjectivist protestive octobass crownal retrorenal activation
 	ascocarp clawing unaccordingly strontianite refutatory reline unsubmersible unstuffy asynergia asha rejunction spirit
	rompe preestimates papabot postcoital forbearantly epistolize corkwood rasers logicized rearrange rectigraph signposts
 	prothrombin headkerchief upholden oversocialize semiperimeter hackbuteer ticklish brachiated atheneum naegait engrasp
 	palaeoconcha deminudity tragions curteous stratal swandown succinylcholine swooners caskanet irrespectability floccul
	ant palatefulness thalamocoele maleate tittivate eustachium etudes loppering fidos flayers murrion uninduced numbednes
	s nincompoopish compressors cassoulet protura fagopyrismus sesquibasic paxwaxes grievous remonstrator fulvid rotatoria
 	ultraconservatives postcards hairdresser wagnerianism mistreats nefarious winberry usherance conductility yearner ura
	nostaphylorrhaphy rehabilitator agrapha junglegym emanant coy gaelicist parallelogram wealdsman objurgator tapeline am
	ay psalterer eleostearate mainprise overdyeing dowly coronado localed weasellike scattergram tocological disproportion
	ation archicerebrum glazement zugtierlaster sleepwort yabber tenontodynia laevulose walkaway readept literally weinman
	nia englut caulopteris schellingian thiamid suberizes bistorta quinetum woolulose jaculiferous trestlework unoriginati
	veness kua uncontemptibleness unconcernedly taryard escapologist traumata chlorochrous exocolitis dysgnosia steadfastn
	ess keratoleukoma inordinate sacahuiste trippler intoxicatively pierid nonapplicabness patinas rabific scandaliser wag
	gel reauthenticate sufeism lairds cookee bragget ledgering perceptual chomper obscurities merino ganguela unproposed e
	pulis loppard ignoblesse carrotage heartbrokenly unfusibness degenerate lacunae cirrocumulus knightlike overwhelmingne
	ss oxyrrhyncha capitalizations dimethylamine uninucleate syndicship graspable tropophil telchines abaiser overclement 
	pursive


```

<br>

- Lo que podemos ver en el _output_ de este último comando es que el contenido del archivo "`` Word_File.txt ``" comienza con una palabra, "`` larceny ``" y todas las que preceden a esta, están separadas entre sí mediante espacios. 

<br>

---

<br>

3. En la línea de lo que vimos en el _output_ del último comando, lo que podemos hacer desde este punto nuevamente, es usar el cmdlet [Get-Content](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.5#:~:text=Obtiene%20el%20contenido%20del%20elemento%20en%20la%20ubicaci%C3%B3n%20especificada) junto a su opción "`` -Delimiter ``" para marcar a los espacios ("`` ``") como el caracter que vamos a estar usando como delimitador activo para evaluar el posible _output_ del comando que vamos a estar utilizando.\
Dicho esto, y sabiendo el archivo al cual le vamos a estar aplicando el comando y el delimitador que vamos a estar usando para orientar la busqueda, hacemos un último agregado al comando, embebiendo este entre paréntesis y agregando al final "`` [160] ``", para indicar que queremos obtener o recuperar los contenidos del archivo justo después del delimitador 160, siendo este en teoría, el espacio 160 dentro del archivo, y obteniendo como resultado la palabra numero 161 dentro del archivo.\
Así es como se vería el comando en su totalidad siendo ejecutado...

<br>

```powershell


    PS C:\users\century7\desktop> (Get-Content -Delimiter “ “ .\Word_File.txt)[160]
    pierid


```

<br>

- Como podemos ver, la palabra 161 dentro del archivo "`` Word_File.txt ``", _flag_ de este nivel y contraseña de Century10 es "`` pierid ``" (century10 : pierid).

<br>


---

<br>

### Adjunto.

<br>

<p align="center">
  <img src="./attachments/level-89_century_underthewire.gif"/>
</p>

> Procedimiento entero.

<br>

---

