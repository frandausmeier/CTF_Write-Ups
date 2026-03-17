> [Century](../README.md) | [UnderTheWire](../../README.md) | [CTF Write-Ups](../../../README.md)

# [Nivel 5](https://underthewire.tech/century)
> Century Nivel 5

> Español | [Inglés](./level-5_century_underthewire_eng.md).

> [PDF version](https://drive.google.com/file/d/1DAw0DTFN3MU2w_Znb6MpChQKjWepKAAp/view?usp=drive_link).

<br>

---

<br>

## Descripción del _challenge_.
> La contraseña para Century6 es el nombre corto del dominio en el que reside este sistema MAS el nombre del archivo que está en _desktop_.
>
> **NOTA IMPORTANTE**
> - Si el nombre corto del dominio es "blob" y el archivo en el escritorio tiene el nombre "1234", la contraseña sería "blob1234".
> - La contraseña deberá ser escrita en minúscula sin importar como sus partes pueden llegar a aparecer en la pantalla.

<br>

## Información útil dada por el _challenge_.
> Información de utilidad dada por el nivel anterior.
- _host-name_: " century.underthewire.tech ".
- _puerto_: " 22 " (2220).
- _usuario_: " century4 ".
- _contraseña_: " 15768 ".

<br>

---

<br>

## Procedimiento.

<br>

1. Al fijarnos en la descripción de este _challenge_, nos damos cuenta que necesitamos 2 piezas de información para llegar a la contraseña de Century6, la primera de esas 2 siendo el nombre corto del servidor en el cual corre nuestra instancia de PowerShell. Este dato también puede ser encontrado como "`` NetBIOSName ``".\
Lo que podemos usar en este caso, es el cmdlet [Get-ADDomain](https://learn.microsoft.com/ja-jp/powershell/module/activedirectory/get-addomain?view=windowsserver2022-ps#:~:text=Gets%20an%20Active%20Directory%20domain.). Este cmdlet te permite obtener nuestro dominio específico de _Active Directory_ e información sobre este, siendo este determinado por los parametros y opciones en el comando.

<br>

```powershell

	PS C:\users\century2\desktop> Get-ADDomain

                                                                                                                
    AllowedDNSSuffixes                 : {}                                                                         
    ChildDomains                       : {}                                                                         
    ComputersContainer                 : CN=Computers,DC=underthewire,DC=tech                                       
    DeletedObjectsContainer            : CN=Deleted Objects,DC=underthewire,DC=tech                                 
    DistinguishedName                  : DC=underthewire,DC=tech                                                    
    DNSRoot                            : underthewire.tech                                                          
    DomainControllersContainer         : OU=Domain Controllers,DC=underthewire,DC=tech                              
    DomainMode                         : Windows2016Domain                                                          
    DomainSID                          : S-1-5-21-758131494-606461608-3556270690                                    
    ForeignSecurityPrincipalsContainer : CN=ForeignSecurityPrincipals,DC=underthewire,DC=tech                       
    Forest                             : underthewire.tech                                                          
    InfrastructureMaster               : utw.underthewire.tech                                                      
    LastLogonReplicationInterval       :                                                                            
    LinkedGroupPolicyObjects           : {cn={ECB4A7C0-B4E1-41B1-9E89-161CFA679999},cn=policies,cn=system,DC=undert 
                                        hewire,DC=tech, CN={31B2F340-016D-11D2-945F-00C04FB984F9},CN=Policies,CN=S 
                                        ystem,DC=underthewire,DC=tech}                                             
    LostAndFoundContainer              : CN=LostAndFound,DC=underthewire,DC=tech                                    
    ManagedBy                          :                                                                            
    Name                               : underthewire                                                               
    NetBIOSName                        : underthewire                                                               
    ObjectClass                        : domainDNS                                                                  
    ObjectGUID                         : bdccf3ad-b495-4d86-a94c-60f0d832e6f0                                       
    ParentDomain                       :                                                                            
    PDCEmulator                        : utw.underthewire.tech                                                      
    PublicKeyRequiredPasswordRolling   : True                                                                       
    QuotasContainer                    : CN=NTDS Quotas,DC=underthewire,DC=tech                                     
    ReadOnlyReplicaDirectoryServers    : {}                                                                         
    ReplicaDirectoryServers            : {utw.underthewire.tech}                                                    
    RIDMaster                          : utw.underthewire.tech                                                      
    SubordinateReferences              : {DC=ForestDnsZones,DC=underthewire,DC=tech,                                
                                        DC=DomainDnsZones,DC=underthewire,DC=tech,                                 
                                        CN=Configuration,DC=underthewire,DC=tech}                                  
    SystemsContainer                   : CN=System,DC=underthewire,DC=tech                                          
    UsersContainer                     : CN=Users,DC=underthewire,DC=tech

```

<br>

- Así es como, en el _output_ de [Get-ADDomain](https://learn.microsoft.com/ja-jp/powershell/module/activedirectory/get-addomain?view=windowsserver2022-ps#:~:text=Gets%20an%20Active%20Directory%20domain.), obtenemos el nombre corto del dominio, siendo este "`` underthewire ``", ubicado en la fila que indica el "`` NetBIOSName ``".

<br>

---

<br>

2. Ya habiendo obtenido la primera parte de la contraseña, buscamos la segunda. Esta, según la descripción del _challenge_, debería ser el nombre de un archivo ubicado en _desktop_. Ejecutamos [Get-ChildItem](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.5#:~:text=Gets%20the%20items%20and%20child%20items%20in%20one%20or%20more%20specified%20locations.) para probar que el archivo este en la ubicación dada...

<br>

```powershell

    Directory: C:\users\century5\desktop
                                                                           
Mode                LastWriteTime         Length Name                                                           
----                -------------         ------ ----                                                           
-a----        8/30/2018   3:29 AM             54 3347

```

<br>

- y ahí es donde encontramos el archivo en _desktop_, siendo su nombre "`` 3347 ``", y dando lugar a la contraseña "`` underthewire3347 ``" (century6 : underthewire3347).

<br>

---

<br>

### Adjuntos.

<br>

<p align="center">
  <img src="./attachments/level-5_century_underthewire.gif"/>
</p>

> Procedimiento entero.

<br>

---

