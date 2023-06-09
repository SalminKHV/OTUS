### VLAN и маршрутизация между VLAN

​		**Описание задания:**

​					[1. Необходимо собрать схему сети как на скриншоте ](#необходимо-собрать-схему-сети-как-на-скриншоте)

​					[2. Описание основного задания:](https://github.com/SalminKHV/OTUS/tree/main/Lab1/#%D0%BE%D0%BF%D0%B8%D1%81%D0%B0%D0%BD%D0%B8%D0%B5-%D0%BE%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D0%BE%D0%B3%D0%BE-%D0%B7%D0%B0%D0%B4%D0%B0%D0%BD%D0%B8%D1%8F ) 

​					[3. Сконфигурировать оборудование в соответствии с таблицами:](https://github.com/SalminKHV/OTUS/tree/main/Lab1/#%D1%81%D0%BA%D0%BE%D0%BD%D1%84%D0%B8%D0%B3%D1%83%D1%80%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D1%82%D1%8C-%D0%BE%D0%B1%D0%BE%D1%80%D1%83%D0%B4%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D0%B2-%D1%81%D0%BE%D0%BE%D1%82%D0%B2%D0%B5%D1%82%D1%81%D1%82%D0%B2%D0%B8%D0%B8-%D1%81-%D1%82%D0%B0%D0%B1%D0%BB%D0%B8%D1%86%D0%B0%D0%BC%D0%B8)

​					[Решение](https://github.com/SalminKHV/OTUS/tree/main/Lab1/#%D1%80%D0%B5%D1%88%D0%B5%D0%BD%D0%B8%D0%B5)

1. ###### Необходимо собрать схему сети как на скриншоте ![Собранная топология](https://user-images.githubusercontent.com/130359715/232216648-4dc9562b-a5d2-47ba-984a-eaa31e09b246.jpg)

2. ###### Описание основного задания: 

   ```
   Часть 1. Создание сети и настройка основных параметров устройства
   В части 1 вы настроите топологию сети и настроите основные параметры хостов и коммутаторов ПК.
   Шаг 1: Подключите сеть, как показано в топологии.
   Присоедините устройства, как показано на схеме топологии, и при необходимости подключите кабели.
   Шаг 2: Настройте основные параметры маршрутизатора.
   Открыть окно конфигурации
   а. Подключитесь к маршрутизатору через консоль и включите привилегированный режим EXEC.
   b. Войдите в режим конфигурации.
   c. Назначьте маршрутизатору имя устройства.
   d. Отключите поиск DNS, чтобы маршрутизатор не пытался преобразовать неправильно введенные команды, как если бы они были именами хостов.
   е. Назначьте class в качестве пароля, для входа в привилегированноый режим.
   f. Назначьте cisco в качестве пароля консоли и разрешите вход.
   g. Назначьте cisco в качестве пароля для VTY и разрешите вход в систему.
   h. Зашифруйте открытые пароли.
   i. Создайте баннер, предупреждающий любого, кто получает доступ к устройству, о том, что несанкционированный доступ запрещен.
   j. Сохраните текущую конфигурацию в файл начальной конфигурации.
   k. Настройте часы на роутере.
   Примечание. Используйте вопросительный знак (?), чтобы указывать правильную последовательность параметров, необходимых для выполнения этой команды.
   Закройте окно конфигурации
   Шаг 3: Настройте основные параметры для каждого коммутатора.
   Откройте окно конфигурации
   а. а. Подключитесь к коммутатору через консоль и включите привилегированный режим EXEC.
   b. Войдите в режим конфигурации.
   c. Назначьте коммутаторам имя устройства.
   d. Отключите поиск DNS, чтобы коммутатор не пытался преобразовать неправильно введенные команды, как если бы они были именами хостов.
   е. Назначьте class в качестве пароля, для входа в привилегированноый режим.
   f. Назначьте cisco в качестве пароля консоли и разрешите вход.
   g. Назначьте cisco в качестве пароля для VTY и разрешите вход в систему.
   h. Зашифруйте открытые пароли.
   i. Создайте баннер, предупреждающий любого, кто получает доступ к устройству, о том, что несанкционированный доступ запрещен.
   j. Сохраните текущую конфигурацию в файл начальной конфигурации.
   k. Настройте часы на коммутаторе.
   Примечание. Используйте вопросительный знак (?), чтобы указать правильную последовательность параметров, необходимых для выполнения этой команды.
   k. Скопируйте текущую конфигурацию в конфигурацию запуска.
   Закройте окно конфигурации
   Шаг 4: Настройте хосты ПК.
   Информацию об адресе хоста ПК см. в Таблице адресации.
   ```

3. ###### Сконфигурировать оборудование в соответствии с таблицами:![image](https://user-images.githubusercontent.com/130359715/233513879-dd757261-35c2-4cb9-a93a-7c6ef89df3f4.png)





## Решение:

​	1. [Произведем первоначальную настройку: ](https://github.com/SalminKHV/OTUS/tree/main/Lab1/#1-%D0%BF%D1%80%D0%BE%D0%B8%D0%B7%D0%B2%D0%B5%D0%B4%D0%B5%D0%BC-%D0%BF%D0%B5%D1%80%D0%B2%D0%BE%D0%BD%D0%B0%D1%87%D0%B0%D0%BB%D1%8C%D0%BD%D1%83%D1%8E-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D1%83 )

​		[Команды первоначальной настройки устройств: ](https://github.com/SalminKHV/OTUS/tree/main/Lab1/#%D0%BA%D0%BE%D0%BC%D0%B0%D0%BD%D0%B4%D1%8B-%D0%BF%D0%B5%D1%80%D0%B2%D0%BE%D0%BD%D0%B0%D1%87%D0%B0%D0%BB%D1%8C%D0%BD%D0%BE%D0%B9-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B8-%D1%83%D1%81%D1%82%D1%80%D0%BE%D0%B9%D1%81%D1%82%D0%B2 )

 2. [Настройка роутера R1:](https://github.com/SalminKHV/OTUS/tree/main/Lab1/#2-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-%D1%80%D0%BE%D1%83%D1%82%D0%B5%D1%80%D0%B0-r1)

 3. [Настройка коммутатора S1:](https://github.com/SalminKHV/OTUS/tree/main/Lab1/#3-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-%D0%BA%D0%BE%D0%BC%D0%BC%D1%83%D1%82%D0%B0%D1%82%D0%BE%D1%80%D0%B0-s1)

 4. [Настройка коммутатора S2:](https://github.com/SalminKHV/OTUS/tree/main/Lab1/#4-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-%D0%BA%D0%BE%D0%BC%D0%BC%D1%83%D1%82%D0%B0%D1%82%D0%BE%D1%80%D0%B0-s2)

 5. [Настройки компьютеров](https://github.com/SalminKHV/OTUS/tree/main/Lab1#5-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B8-%D0%BA%D0%BE%D0%BC%D0%BF%D1%8C%D1%8E%D1%82%D0%B5%D1%80%D0%BE%D0%B2)

 6. [Проверка работоспособности наших настроек:](https://github.com/SalminKHV/OTUS/tree/main/Lab1#6-%D0%BF%D1%80%D0%BE%D0%B2%D0%B5%D1%80%D0%BA%D0%B0-%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%BE%D1%81%D0%BF%D0%BE%D1%81%D0%BE%D0%B1%D0%BD%D0%BE%D1%81%D1%82%D0%B8-%D0%BD%D0%B0%D1%88%D0%B8%D1%85-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B5%D0%BA)

    ### 1. Произведем первоначальную настройку

    На наших активных устройствах R1, S1, S2, настроим доступ и авторизацию по консоли и по VTY, установим пароли, время и приветственный баннер, а также отключим поиск DNS и установим имя устройства. Произведем настройку на примере маршрутизатора R1(на других устройствах настройки аналогичные):

    

    ##### Команды первоначальной настройки устройств:

    Router>en  
    Router#conf t  
    Enter configuration commands, one per line.  End with CNTL/Z.  
    Router(config)#hostname R1  
    R1(config)#no ip domain lookup  
    R1(config)#line console 0  
    R1(config-line)#pass cisco  
    R1(config-line)#login  
    R1(config-line)#ex  
    R1(config)#line vty 0 4  
    R1(config-line)#pass cisco  
    R1(config-line)#login  
    R1(config-line)#exi  
    R1(config)#enable pass class  
    R1(config)#service password-encryption  
    R1(config)#banner motd #  
    Enter TEXT message.  End with the character '#'.  
    Unauthoririd access is strictly prohibited#  
    R1(config)#  
    R1(config)#clock timezone UTC 11  
    R1(config)#  
    *Apr 23 22:43:24.648: %SYS-6-CLOCKUPDATE: System clock has been updated from   

    22:43:24 UTC Sun Apr 23 2023 to 09:43:24 UTC Mon Apr 24 2023, configured from console by console.      

    ### 2. Настройка роутера R1:

​		Необходимо настроить Sub-интерфейсы на порту е0/1 роутера для подсетей 192.168.3.х и 192.168.4.х. Назначим IP - адреса этим интерфейсам 192.168.3.1 и 192.168.4.1 соответственно, а также настроим sub - интерфейс для нативного vlan-а, без IP-адреса. Включим инкапсуляцию dot1Q. Сохраним настроенную (работающую) конфигурацию в файл стартовой конфигурации устройства.

R1(config)#int e0/1.3  
R1(config-subif)#ip add   
R1(config-subif)#ip address 192.168.3.1 255.255.255.0  
R1(config-subif)#encapsulation dot1Q 3  
R1(config-subif)#int e0/1.4   
R1(config-subif)#ip add 192.168.4.1 255.255.255.0  
R1(config-subif)#encapsulation dot1Q 4  
R1(config-subif)#int e0/1.8  
R1(config-subif)#encapsulation dot1Q 8 native  
R1#copy running-config startup-config  
Destination filename [startup-config]?  
Building configuration...  
[OK]   

### 3. Настройка коммутатора S1:

На коммутаторе S1 необходимо создать vlan-ы 3, 4, 7 и 8, утсновить на инттерфейсе vlan3 ip- адресс 192.168.3.11, порты e0/0 и e0/1 перевести в режим trunk с странсляцией vlan-ов 3, 4 и нативного vlan-а 8, подпишем vlan-ы.  Не используемые порты коммутатора переведем в режим доступа и отнесем к vlan-ну 7. Порт e0/2 переведем в режим доступа gj vlan 3, к нему подключим VPC-A. Также необходимо прописать шлюз по умолчанию и пропишем маршрут "последней надежды"(не безопасно, можно было бы прописать маршрут к сети 192.168.4.0 с маской 255.255.255.0 и шлюзом 192.168.3.1) без этого маршрута наш коммутатор не будет знать куда слать пакеты для обращения к сети 192.168.4.0.

Switch(config)#hostname s1  
s1(config)#hostname S1  
S1(config)#vlan 3  
S1(config-vlan)#name Management  
S1(config-vlan)#vlan 4  
S1(config-vlan)#name Operations  
S1(config-vlan)#vlan 7  
S1(config-vlan)#name ParkingLot  
S1(config-vlan)#vlan 8  
S1(config-vlan)#name Native  
S1(config-vlan)#exi  
S1(config)#int e0/0  
S1(config-if)#sw m t  
S1(config-if)#sw t native vlan 8  
S1(config-if)#sw t allowed vlan 3,4  
S1(config-if)#int e0/1  
S1(config-if)#sw m t  
S1(config-if)#int e0/1  
S1(config-if)#sw m t  
S1(config-if)#sw t encapsulation d  
S1(config-if)#sw t na v 8  
S1(config-if)#sw t all v 3,4  
S1(config-if)#sw m a  
S1(config-if)#sw a vl 3  
S1(config)#int vlan 3  
S1(config-if)#ip add 192.168.3.11 255.255.255.0  
S1(config-if)#exi  
S1(config)#ip default-gateway 192.168.3.1  
S1(config)#ip route 0.0.0.0 0.0.0.0 192.168.3.1  
S1(config)#int e0/3  
S1(config-if)#sw m a  
S1(config-if)#sw a vl 7  

### 4. Настройка коммутатора S2:

На коммутаторе S2 необходимо создать vlan-ы 3, 4, 7 и 8, утсновить на инттерфейсе vlan3 ip- адресс 192.168.3.12, порт e0/1 перевести в режим trunk с странсляцией vlan-ов 3, 4 и нативного vlan-а 8, подпишем vlan-ы.  Не используемые порты коммутатора переведем в режим доступа и отнесем к vlan-ну 7. Порт e0/2 переведем в режим доступа по vlan 4, к нему подключим VPC-B. Также необходимо прописать шлюз по умолчанию и пропишем маршрут "последней надежды".

Router(config)#hostname S2  
S2(config)#vlan 3  
S1(config-vlan)#name Management  
S2(config-vlan)#vlan 4  
S2(config-vlan)#name Operations  
S2(config-vlan)#vlan 7  
S2(config-vlan)#name ParkingLot  
S2(config-vlan)#vlan 8  
S2(config-vlan)#name Native  
S2(config-vlan)#exi  
S2(config)#int e0/1  
S2(config-if)#sw m t  
S2(config-if)#sw t native vlan 8  
S2(config-if)#sw t allowed vlan 3,4  
S2(config-if)#sw t e d   
S2(config-if)#int e0/2  
S2(config-if)#sw m a  
S2(config-if)#sw a vl 4  
S2(config)#int vlan 3  
S2(config-if)#ip add 192.168.3.12 255.255.255.0  
S2(config-if)#exi  
S2(config)#ip default-gateway 192.168.3.1  
S2(config)#ip route 0.0.0.0 0.0.0.0 192.168.3.1  
S2(config)#int e0/3  
S2(config-if)#sw m a  
S2(config-if)#sw a vl 7  
S2(config-if)#int e0/0  
S2(config-if)#sw m a  
S2(config-if)#sw a vl 7  

### 5. Настройки компьютеров:

Произведем настройки VPC-A и VPC-B, настроив их IP- адреса, в соответствии с [таблицей адресации](https://github.com/SalminKHV/OTUS/tree/main/Lab1#%D1%81%D0%BA%D0%BE%D0%BD%D1%84%D0%B8%D0%B3%D1%83%D1%80%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D1%82%D1%8C-%D0%BE%D0%B1%D0%BE%D1%80%D1%83%D0%B4%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D0%B2-%D1%81%D0%BE%D0%BE%D1%82%D0%B2%D0%B5%D1%82%D1%81%D1%82%D0%B2%D0%B8%D0%B8-%D1%81-%D1%82%D0%B0%D0%B1%D0%BB%D0%B8%D1%86%D0%B0%D0%BC%D0%B8)

VPC-A 

![VPC-A](https://user-images.githubusercontent.com/130359715/234719730-09380ea5-759f-4f7e-acc7-bbbab009ffce.PNG)

VPC-B

![image](https://user-images.githubusercontent.com/130359715/234719348-5079eec9-07ae-46ea-82e4-8a5974be60c8.png)



### 6. Проверка работоспособности наших настроек:

Проведем тестирование доступности всех наших устройств с VPC-A и VPC-B. Проверка доступности устройств с VPC-A:

![image](https://user-images.githubusercontent.com/130359715/234721389-52c1848a-605e-4e8c-9f9c-e22e369560ca.png)

Проверка доступности устройств с VPC-B:

![image](https://user-images.githubusercontent.com/130359715/234721704-09cb2457-04eb-4147-ae6f-179239bdb794.png)