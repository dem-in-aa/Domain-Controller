# Настройка Контроллера Домена, Windows Server 2019

### Настройка сети NAT в VirtualBox v.7

1. Создать сеть 10.0.2.0/24, отключить DHCP, IPv6:

![](img/vbox5.png)
------
2. Подключить сетевой адаптер ВМ Windows Server к сети:

![](img/vbox6.png)
------

### Настройки Контроллера Домена

1. В настройках сетевого адаптера в Windows Server 2019 отключить IPv6, в свойствах IPv4 установить статический
IP 10.0.2.3, маску 255.255.255.0, шлюз 10.0.2.1, DNS 127.0.0.1

![](img/network.png)
------
2. Сменить Имя компьютера: Этот компьютер > Свойства > Система > Изменить параметры > Изменить

3. В Диспетчере серверов добавить роли **Доменные службы Active Directory** ,  **DHCP-сервер** , **DNS-сервер**

![](img/AD1.png)
------
4. Повысить роль сервера до уровня контроллера домена:

![](img/AD2-2.png)
------
- указать имя корневого домена:

![](img/AD3.png)
------
- установить пароль для режима восстановления служб каталога:

![](img/AD4.png)
------
- параметры DNS оставить без изменения:

![](img/AD5.png)
------
- имя домена NetBIOS оставить без изменения:

![](img/AD6.png)
------
*После успешной проверки предварительных условий можно запустить настройку доменных служб Active Directory.*

![](img/AD2-1.png)
------
5. Настроить DHCP-сервер:

- Диспетчер серверов > Средства > DHCP

![](img/DHCP2.png)
------
В оснастке DHCP  проверить и/или авторизовать сервер: DHCP > Список авторизованных серверов

![](img/DHCP3.png)
------
![](img/DHCP4.png)
------
-  Проверить и/или установить привязки сервера:

![](img/DHCP5.png)
------
![](img/DHCP6.png)
------
- Создать область с диапазоном ip-адресов:

![](img/DHCP7.png)
------
![](img/DHCP8.png)
------
- Указать адрес DNS-сервера:

![](img/DHCP9.png)
------
- Проверить пул адресов:

![](img/DHCP10.png)
------
6. Настроить DNS-сервер:

Диспетчер серверов > Средства > DNS

- В каталоге **Серверы условной пересылки** создать сервер условной пересылки:

![](img/DNS1.png)
------
- В каталоге **Зоны обратного просмотра** создать зону обратного просмотра:

![](img/DNS2.png)
------
![](img/DNS3.png)
------
![](img/DNS4.png)
------
![](img/DNS5.png)
------
![](img/DNS6.png)
------
- В подкаталоге **site.example.com** каталога **Зоны прямого просмотра** создать узел(А) с ip 10.0.2.15

![](img/DNS7.png)
------
- В подкаталоге **example.com** каталога **Зоны прямого просмотра** создать узел(А) с ip 10.0.2.15

![](img/DNS8.png)
------
7. Создание пользователей и групп

Перейти в оснастку AD - пользователи и группы

* оснастку можно вызвать командой:
```
dsa.msc
```
![](img/users1.png)
------
Создать группы и пользователей, включив их в группы:

![](img/users2.png)
------
8. Включение клиента в домен

Детали сетевого подключения на клиенте Windows 10:

![](img/win10-1.png)
------
Отчет групповой политики:

![](img/win10-2.png)
------
![](img/win10-3.png)
------
 



