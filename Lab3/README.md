## DHCPv4/v6 и SLAAC 



##### 1. Топология сети

![image](https://github.com/SalminKHV/OTUS/assets/130359715/a52df14c-3ea1-428b-b423-f901bb30093a)

##### 2. Таблица адресации и цели:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/e481a4a6-695e-4d13-9746-b694233c381e)

###### Цели:

**Часть 1. Создание сети и настройка основных параметров устройства**  
**Часть 2. Настройка и проверка двух серверов DHCPv4 на маршрутизаторе R1**  
**Часть 3. Настройка и проверка ретрансляции DHCP на маршрутизаторе R2**  





## Решение

[Часть 1](https://github.com/SalminKHV/OTUS/tree/main/Lab3#%D1%87%D0%B0%D1%81%D1%82%D1%8C-1)

[Часть 2]()

[Часть 3]()



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

​				Настроим роутер R2, назначим ip-адрес на порту Gi0/0, назначим шлюз по умолчанию и пропишем маршруты для удаленных подсетей. Проверим что связность есть. Сохраним конфиг.

![image](https://github.com/SalminKHV/OTUS/assets/130359715/ae46d4ef-b696-4860-b393-ac8c05ee1723)

​				

​				После первоначальной настройки коммутатора S1, создадим и настроим Vlan-ы:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/cc1bad2e-c4e9-4f19-8ce9-718b14b1465a)

![image](https://github.com/SalminKHV/OTUS/assets/130359715/212eb5d9-4498-4221-a8cd-94fb2e940a60)

​				Настроим режим работы портов, настроим на портах Gi0/1 и Gi0/3 вланы. Настроим транки, назначим шлюз по умолчанию, и пропишем маршрут по умолчанию на S1:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/ca1e001d-cf7a-4387-86b7-7cfd78118c4b)

![image](https://github.com/SalminKHV/OTUS/assets/130359715/139c7aa5-496d-478c-835c-53f00b81a34b)



​				Произведя первоначальную настройку коммутатора **S2**, настроим интейрфейс **Vlan1**, назначив **ip-адрес 192.168.1.98 с маской 255.255.255.240**, Пропишем шлюз по умолчанию и маршрут последней надежды. Не используемые порты отключим. И проверим связность с маршрутизатором R2:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/68b79f1c-8f49-4509-b6ee-f431b29903af)

​				Присвоим всем неиспользуемым портам Влан 999 Parking_Lot:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/2c8fbcc3-ae32-427b-8eb0-0e890232ebcb)

​				Убедимся что мы правильно создали и назначили Vlan-ы на порты и подписали их сперва на S2:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/c7c948ab-c265-4e04-b5f2-76acab7d3298)

и затем на S1:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/4e52d09d-13fe-4083-8a55-e57910d1ffae)

![image](https://github.com/SalminKHV/OTUS/assets/130359715/376d0804-23da-4a38-81fe-2891a94e5262)

**Ответим на вопрос "Почему интерфейс Gi0/1 на S2 размещен во Vlav 1?**" : потому что порт Gi0/1 на роутере  R2 настроен без саб интейфейсов и будет передавать нетегированный трафик, физическому порту роутера назначен IP-адрес, который не будет находится ни в одном из виланов, поэтому для связи с роутером R2  использется Vlan 1(по умолчанию), по которому передается трафик без тега. 



**Ответим на вопрос: "На данный момент, какой IP-адрес будет у ПК, если он будет подключен к сети с использованием DHCP?"** DHCP у нас еще пока что не сконфигурирован и не запущен, следовательно ПК не получин никакого IP-адреса от сервера, а сформирует свой собственный из подсети 169. * . * . *     c  маской 255. * . * .* 

Проверим:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/0af6c5b0-312e-42b9-a387-911a8f744b1c)





### Часть 2

Во второй части мы сконфигурируем DHCP на роутере R1 для подсетей "А" и "С".

Сконфигурируем DHCP-pool-ы на роутере R1 для подсетей А и С. Для иэтого исключим первые пять адресов из адресного пространства подсетей А и С:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/b6c9deb8-b30c-47bf-9f91-27f547fd4cdc)

Назначим имя, адресное пространство, шлюз по умолчанию и время аренды IP-адреса  DHCP- пулу А на R1:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/b0a84f32-515e-46e6-8762-f4c0055a653b)

Назначим имя, адресное пространство, шлюз по умолчанию и время аренды IP-адреса  DHCP- пулу C на R1:



![image](https://github.com/SalminKHV/OTUS/assets/130359715/0ca8f0ae-d4fc-4a60-a018-92f9464871c6)

Проверим на роутере арендованные ip-адреса:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/c54f323b-19ca-44f5-b89b-0461405b7a64)

Проверим занятые адреса в dhcp -пулах и посмотрим статистику dhcp-серверов:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/ac3d743f-1b94-4b2b-8b4c-911b4e66dd5b)



Обновим настройки PC-A и проверим доступность порта Gi0/1 роутера R1:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/13818da1-1c7d-4182-b60e-29fa64cab892)



### Часть 3

В третьей части мы настроим DHCP relay на R2, проверим полученные настройки на PC-B и доступность с PC-B ip-адресов на порту Gi0/1 роутера R1, а также посмотрим статистику DHCP-серверов  на роутере R1 и R2.

Сконфигурируем DHCP-relay:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/34185f48-71e2-4077-b02a-b23f0680990e)



Посмотрим статистику на CP-B:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/fe1f0d39-ea03-44b7-9e94-79c4ea459e57)



Проверим доступность с PC-B ip-адресов на порту Gi0/1 роутера R1:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/7e65b8b0-0086-44eb-a622-40cfd395aee4)



Посомтрим статистику DHCP-серверов на R1:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/e4a71e6c-a5d1-4830-a2d5-4f8c00594825)

и R2:



![image](https://github.com/SalminKHV/OTUS/assets/130359715/3c6414be-b118-44da-83de-425a4eae42d5)

 
