## DHCPv4/v6 и SLAAC 



##### 1. Топология сети

![image](https://github.com/SalminKHV/OTUS/assets/130359715/a52df14c-3ea1-428b-b423-f901bb30093a)

##### 2. Таблица адресации и цели:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/b51a0740-1f5e-4457-b259-88b0aeac5e91)

###### Цели:

**Часть 1. Создание сети и настройка основных параметров устройства**  
**Часть 2. Настройка и проверка двух серверов DHCPv4 на маршрутизаторе R1**  
**Часть 3. Настройка и проверка ретрансляции DHCP на маршрутизаторе R2**  





## Решение

[Часть 1]()

[Часть 2]()

[Часть 3]()

[Часть 4]()



#### Часть 1

Произведем первоначальные настройки роутеров R1 и R2 и коммутаторов S1, S2. т.к. первоначальные настройки на устройствах идентичны, проведем настройку на примере роутера R1.       

Отключим поиск DNS командой **#no ip domain lookup**

Присвоим имена устройствам, в соответствии со схемой **#hosname R1**

Назначим пароль для доспупа в привилегированный режим:

**#enable password class**

Назначим пароль **cisco** в качестве паролей консоли и VTY и активируем вход:

**#line console 0**

перейдя к настройке консольного канала, сразу настроим **"logging synchronous"** командой    

**S1(config-line)#logging synchronous**

**#password cisco**

**#login**

**#line vty 0 4**

**#password cisco**

**#login**

Зашифруем пароли в конфигурационном файле:

**#service password-encription**

Настроим баннерное сообщение командой **#banner motd 3**

**"Unauthorized access is strictly prohibited" #**

![image](https://github.com/SalminKHV/OTUS/assets/130359715/17257e20-79ff-4999-9295-5ec3ad42a459)

Настроим часовой пояс, например UTC+11:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/de82249f-1af1-465b-9e14-9cafc39e65da)

Установим время:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/8b70cfc6-fd7b-422d-8c22-5fdf8f4558eb)



Для удобства работы установим EXEC-Timeout:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/a5d4232c-ea03-47d3-b574-a184a2a398ca)

Произведем настройку Sub-интерфейсов роутера R1:
