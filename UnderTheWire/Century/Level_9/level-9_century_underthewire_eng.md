> [Century](../README.md) | [UnderTheWire](../../README.md) | [CTF Write-Ups](../../../README.md)

# [Level 9](https://underthewire.tech/century)
> Century Level 9

> English | [Spanish](./nivel-9_century_underthewire_esp.md).

> [PDF version](https://drive.google.com/file/d/1HCjgvMsvFxTeZNtw7UMhN9IT3JbaH6dm/view?usp=drive_link).

<br>

---

<br>

## Challenge description.
> The password for Century10 is the 161st word within the file on the desktop.
>
> IMPORTANT NOTE
>
> - The password will be lowercase no matter how it appears on the screen.

<br>

## Information given by the challenge.
> Useful information given by the previous level.
- _hostname_: " century.underthewire.tech ".
- _port_: " 22 " (2220).
- _user_: " century9 ".
- _password_: " 696 ".

<br>

---

<br>

## Procedure.

<br>

1. Initially, we take a look at the description of the challenge and get to know that the password for Century10 is the 161st word in a file that is stored in the desktop folder.\
Already being in desktop from the login, we use [Get-ChildItem](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=Obtiene%20los%20elementos%20y%20elementos%20secundarios%20de%20una%20o%20varias%20ubicaciones%20especificadas) to see the file in question...

<br>

```powershell


	PS C:\users\century7\desktop> Get-ChildItem


    	Directory: C:\users\century9\desktop
    
    
	Mode                LastWriteTime         Length Name                 ----                -------------         ------ ----
    -a----        8/30/2018   3:34 AM           2131 Word_File.txt
    
    
```

<br>

- and that's where we find it, "`` Word_File.txt ``", a text file that, in its contents, should be the one that has the password.

<br>

---

<br>

2. Now, having the file in question at sight, we make use of the cmdlet [Get-Content](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.5#:~:text=Obtiene%20el%20contenido%20del%20elemento%20en%20la%20ubicaci%C3%B3n%20especificada) to get a peek at the contents of the file, to see how we can approach getting the word at issue.

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

- What we can see in the output of the last command is that the document starts with a word, "`` larceny ``", and every single one of this is followed by a space that serves to separate each word from each other.

<br>

---

<br>

3. Following what we learned in the output of the last command, what we can do, is use once again [Get-Content](https://learn.microsoft.com/es-es/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.5#:~:text=Obtiene%20el%20contenido%20del%20elemento%20en%20la%20ubicaci%C3%B3n%20especificada) alongside its "`` -Delimiter ``" option to determine spaces ("`` ``") as the character we are going to be using as the delimiter to evaluate the possible output of the command.\
Now, knowing the file to which we apply the command and the delimiter we are going to be using, we take a final step to get the word in question, we wrap the previously mentioned commmand between parenthesis and add it a "`` [160] ``" at the end, to indicate that we want to retrieve the first contents of the file after the delimiter 160, or after the space number 160 of the file, what we think it's the 161st word of the file.\
This is how the entire command looks...

<br>

```powershell


	PS C:\users\century7\desktop> (Get-Content -Delimiter “ “ .\Word_File.txt)[160]
    pierid


```

<br>

- As we see in the output of the command, the 161st word of the "`` Word_File.txt ``" file, flag of this level and password for Century10, is the word "`` pierid ``" (century10 : pierid).

<br>

---

<br>

### Attachments.

<br>

<p align="center">
  <img src="./attachments/level-9_century_underthewire.gif"/>
</p>

> Entire procedure.

<br>

---

