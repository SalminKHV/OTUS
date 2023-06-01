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

![image](https://github.com/SalminKHV/OTUS/assets/130359715/d91d8f1c-74d8-41b2-9a00-4b24faefc082)

![image](https://github.com/SalminKHV/OTUS/assets/130359715/3ca61f3c-ab28-4120-a9b8-7a61ad180060)

![image](https://github.com/SalminKHV/OTUS/assets/130359715/9d742451-6ae5-4047-8220-34c3e0df7b55)

​				Мы назначили активировали порт Gi0/1, создали Sub-интерфейсы и подписали их, включили инкапсуляцию и назначили ip-адреса интерфейсам, согласно [таблице адресации.]()

​				Настроим интерфейс Gi0/0 ро роутере R1:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/08e0b0ad-a656-4f4b-8b00-7652745e6959)

​				Установим шлюз по умолчанию для роутера R1 и пропишем маршрут для удаленной сети:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/ba2ef1ec-e961-4f61-87a5-cd43392af382)

​				Настроим роутер R2, назначим ip-адрес на порту Gi0/0Ю нашзачим шлюз по умолчанию и пропишем маршруты для удаленных подсетей. Проверим что связность есть. Сохраним конфиг.

![image](https://github.com/SalminKHV/OTUS/assets/130359715/ae46d4ef-b696-4860-b393-ac8c05ee1723)

​				

​				После первоначальной настройки коммутатора S1, создадим и настроим Vlan-ы:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/212eb5d9-4498-4221-a8cd-94fb2e940a60)

​				Настроим Порты Gi0/1 и Gi0/3. Настроим транки, назначим шлюз по умолчанию, и пропишем маршрут по умолчанию на S1:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/ca1e001d-cf7a-4387-86b7-7cfd78118c4b)

![image](https://github.com/SalminKHV/OTUS/assets/130359715/139c7aa5-496d-478c-835c-53f00b81a34b)





