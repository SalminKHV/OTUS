# Развертывание коммутируемой сети с резервными каналами







#### 1. Топология сети

![image](https://user-images.githubusercontent.com/130359715/235008936-c16ab360-6a1a-4f06-93c4-012c57ff2be9.png)

#### 2. Таблица адресации и цели:

![image](https://user-images.githubusercontent.com/130359715/235009373-7dae1d4b-5427-43cc-b0d8-1344006e0e57.png)

![image](https://user-images.githubusercontent.com/130359715/235009495-6fe79d3d-53bd-4dff-8098-3898c59f8603.png)





## Решение

[Часть 1](https://github.com/SalminKHV/OTUS/tree/main/Lab2#%D1%87%D0%B0%D1%81%D1%82%D1%8C-1)

[Часть 2](https://github.com/SalminKHV/OTUS/tree/main/Lab2#%D1%87%D0%B0%D1%81%D1%82%D1%8C-2-%D0%BE%D0%BF%D1%80%D0%B5%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5-%D0%BA%D0%BE%D1%80%D0%BD%D0%B5%D0%B2%D0%BE%D0%B3%D0%BE-%D0%BC%D0%BE%D1%81%D1%82%D0%B0)

[Часть 3](https://github.com/SalminKHV/OTUS/tree/main/Lab2#%D1%87%D0%B0%D1%81%D1%82%D1%8C-3-%D0%BD%D0%B0%D0%B1%D0%BB%D1%8E%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-%D0%B7%D0%B0-%D0%BF%D1%80%D0%BE%D1%86%D0%B5%D1%81%D1%81%D0%BE%D0%BC-%D0%B2%D1%8B%D0%B1%D0%BE%D1%80%D0%B0-%D0%BF%D1%80%D0%BE%D1%82%D0%BE%D0%BA%D0%BE%D0%BB%D0%BE%D0%BC-stp-%D0%BF%D0%BE%D1%80%D1%82%D0%B0-%D0%B8%D1%81%D1%85%D0%BE%D0%B4%D1%8F-%D0%B8%D0%B7-%D1%81%D1%82%D0%BE%D0%B8%D0%BC%D0%BE%D1%81%D1%82%D0%B8-%D0%BF%D0%BE%D1%80%D1%82%D0%BE%D0%B2)

[Часть 4](https://github.com/SalminKHV/OTUS/tree/main/Lab2#%D1%87%D0%B0%D1%81%D1%82%D1%8C-4-%D0%BD%D0%B0%D0%B1%D0%BB%D1%8E%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-%D0%B7%D0%B0-%D0%BF%D1%80%D0%BE%D1%86%D0%B5%D1%81%D1%81%D0%BE%D0%BC-%D0%B2%D1%8B%D0%B1%D0%BE%D1%80%D0%B0-%D0%BF%D1%80%D0%BE%D1%82%D0%BE%D0%BA%D0%BE%D0%BB%D0%BE%D0%BC-stp-%D0%BF%D0%BE%D1%80%D1%82%D0%B0-%D0%B8%D1%81%D1%85%D0%BE%D0%B4%D1%8F-%D0%B8%D0%B7-%D0%BF%D1%80%D0%B8%D0%BE%D1%80%D0%B8%D1%82%D0%B5%D1%82%D0%B0-%D0%BF%D0%BE%D1%80%D1%82%D0%BE%D0%B2)

#### Часть 1

Произведем первоначальные настройки коммутаторов S1, S2, S3, т.к. первоначальные настройки на устройствах идентичны, проведем настройку на примере коммутатора S1.       

Отключим поиск DNS командой **#no ip domain lookup**

Присвоим имя устройству командой **#hosname S1**

Назначим пароль для доспупа в привилегированный режим:

**#enable password class**

**#login**

Назначим пароль **cisco** в качестве паролей консоли и VTY и активируем вход:

**#line console 0**

перейдя к настройке консольного канала, сразу настроим **"logging synchronous"** командой    

**S1(config-line)#logging synchronous**

**#password cisco**

**#login**w

**#line vty 0 4**

**#password cisco**

**#ligin**

Зашифруем пароли в конфигурационном файле:

**#service password-encription**

Настроим баннерное сообщение командой **#banner motd 3**



![image](https://user-images.githubusercontent.com/130359715/235053670-39cabec0-b5f3-44f2-86bd-c6d9ccbbbc0a.png)

Настроим IP-адреса vlan1 на всех коммутаторах в соответствии с [таблицей адресации](), на S1 это 192.168.1.1 с маской 255.255.255.0

и переведем интерфейс в состояние **up** командой **no shutdown**

![image](https://user-images.githubusercontent.com/130359715/235054719-390c061f-9f4f-46fd-a38a-060a5cb952a6.png)

сохраним текущую конфигурацию в файл загрузочной конфигурации

![image](https://user-images.githubusercontent.com/130359715/235060887-39eaeabd-14f0-49b6-a26a-957099557535.png)

Проведем настройку на коммутаторах S2 и S3.

Проверим первоначальные настройки:

проверим доступность коммутаторов S2 и S3 с ком-ра S1:

![image](https://user-images.githubusercontent.com/130359715/235069913-6be08afa-e494-467c-9812-f5f0cd3ee188.png)

проверим доступность коммутаторов S1 и S3 с ком-ра S2:

![image](https://user-images.githubusercontent.com/130359715/235070493-4bfc17ec-63b8-4cf0-868c-ffe595bcc83b.png)

проверим доступность коммутаторов S1 и S2 с ком-ра S3:

![image](https://user-images.githubusercontent.com/130359715/235072701-e17f3438-624f-40f6-aacd-5f6be7bd8978.png)



#### Часть 2: Определение корневого моста

##### Шаг 1 Отключим все порты на всех коммутаторах на примере S1

![image](https://user-images.githubusercontent.com/130359715/235074203-a33ad2c6-4012-4c35-bc50-4d4731d951da.png)

##### Шаг 2 Настроим подключенные порты в кастве транков, предварительно включив encapsulation Dot1Q

![image](https://user-images.githubusercontent.com/130359715/235075614-b565edd7-fb4b-48b0-9888-44bd6ad4228f.png)

##### Шаг 3 Включим порты e0/0 и e0/2 на всех коммутаторах:

S1:

![image](https://user-images.githubusercontent.com/130359715/235278077-e1f8fbec-4ef7-456f-ab3d-95353d5131bf.png)

S2:

![image](https://user-images.githubusercontent.com/130359715/235278162-956549bb-670a-41e1-a917-b145274423f1.png)

S3:

![image](https://user-images.githubusercontent.com/130359715/235278202-41d2bbef-af85-47ee-8f1b-2f420ab13004.png)

##### Шаг 4 Отобразим данные протокола spanning-tree:

S1:

![image](https://user-images.githubusercontent.com/130359715/235278337-c811ba46-374e-4f58-9b63-27e4099cda44.png)

S2:

![image](https://user-images.githubusercontent.com/130359715/235278422-07b806f6-f2ae-4c3d-bb13-5e437a1dd6df.png)



S2(Много позже):

![image](https://user-images.githubusercontent.com/130359715/235396983-2541a293-7b24-4a25-ac8b-900f5587b0a6.png)



Надо отметить, что состояние порта E0/2 изменилось из состояния Desg BLK в Desg FWD, то есть снята блокировка порта. Отмечу что в моей лабораторной работает протокол RSTP - по умолчанию включен на коммутаторах.



S3:

​			   ![image](https://user-images.githubusercontent.com/130359715/235278593-6d48a9ac-e04f-44b3-82a1-ef72d6e3be0c.png) 





##### Ответим на вопросы, с учетом поступившей информации



![image](https://user-images.githubusercontent.com/130359715/235443580-61101116-0e62-45eb-88f3-f73cd9ad1fb0.png)



### Часть 3: Наблюдение за процессом выбора протоколом STP порта, исходя из стоимости портов

##### Шаг 1:   Определим коммутатор с заблокированным портом



s2: 

![image](https://user-images.githubusercontent.com/130359715/235396983-2541a293-7b24-4a25-ac8b-900f5587b0a6.png)



S3: 

![image](https://user-images.githubusercontent.com/130359715/235399076-cc4c9ec2-1212-4308-ba13-b66bd1ab36a7.png)



### Шаг 2:   Изменим стоимость корневого порта на S3

По умолчанию стоимость порта 100, установим 90:

S3(config)#int e0/2

S3(config-if)#spanning-tree cost 90

### Шаг 3: Просмотрим изменения протокола spanning-tree:

S3:

![image](https://user-images.githubusercontent.com/130359715/235403354-bbe1abba-9b6a-4e55-b2b1-74ebc4691109.png)

​				![image](https://user-images.githubusercontent.com/130359715/235403672-511fc804-33f4-4dab-906e-e7ede4d38523.png)	

S2:

![image](https://user-images.githubusercontent.com/130359715/235402230-d19f5af4-3305-47c9-8564-cb027c4a9e65.png)



Мы видим что протокол spanning-tree заменяет ранее заблокированный порт e0/0 на S3, сперва переводит из состояния Alternative в состояние Designated, оставляя порт заблокированным, и через секунд 30 примерно переводит порт в состояние Desg Forward(Назначенный в состоянии передачи). А порт e0/2 на коммутаторе S2 переводит из состояния Desg Forward в состояние Alternative Block (альтернативный - блокированный) т.е. блокирует порт для передачи. Порт изменил свою роль из-за того, что у всего коммутатора изменилась стоимость доставки до Root Bridge (Root Path Cost), и она стала меньше чем у коммутатора S2.



### Шаг 4:   Удалим изменения стоимости порта на S3

командами:

S3(config)#int e0/2

S3(config-if)#spanning-tree cost 100

S3:

![image](https://user-images.githubusercontent.com/130359715/235404532-4579fa88-257e-4a2e-99b9-6a94d143a20c.png)





Видим, что настройки протокола пришли в прежний вид.





## Часть 4: Наблюдение за процессом выбора протоколом STP порта, исходя из приоритета портов



Если стоимости портов равны, процесс сравнивает BID. Если BID равны, для определения корневого моста используются приоритеты портов. Значение приоритета по умолчанию — 128. STP объединяет приоритет порта с номером порта, чтобы разорвать связи. Наиболее низкие значения являются предпочтительными.

Включим поты e0/1 и e0/3 на всех коммутаторах и посмотрим результат.

S1:

![image](https://user-images.githubusercontent.com/130359715/235405841-4859ec97-098c-4745-8645-919d3cbbb4c1.png)



S2:

![image](https://user-images.githubusercontent.com/130359715/235405938-139fa9b2-9e92-4eb7-a315-e5eaf54a1164.png)



S3:

![image](https://user-images.githubusercontent.com/130359715/235405994-378676ea-635b-4023-bf30-d3df5b774c6e.png)



Итак, мы Видим, что Протокол Spanning-tree выбрал сам в качестве Корневого моста S1 по BID, затем на коммутаторе S2 установил, что 2 порта подсоединены напрямую к коммутатору S1 => порты e0/0 и e0/1  и эти порты имеют одинаковую Цену(cost = 100), одинаковый приоритет (Prio = 128), => тот порт, коммутатора S2, который смотрит на порт с наименьшим номером коммутатора Root Bridge меньше по номеру и будет Root портом, а второй переведен в состояние ALT BLC (запасной, блокированный). Порты e0/2 и e0/3  коммутатора S2 приведены в состояние Desg FWD (Назначенные порты в состояние UP) т.к. коммутатор имеет меньший Root Path Cost (а именно значение mac-адреса), по сравнению с коммутатором S3, следовательно порты коммутатора S2 имеющие одинаковою Cost, будут иметь состояние Desg FWD. На коммутаторе S3 порты e0/2 и e0/3 подключены к S1 (Корневому мосту) напрямую,  порты имеют одинаковый вес, но порт коммутатора , который смотрит на порт с наименьшим номером коммутатора Root Bridge меньше по номеру и будет Root портом, а второй переведен в состояние ALT BLC  порта е0/2 S2 смотрит на порт е0/2 S1, а  порта е0/3 S2 смотрит на порт е0/3 S1 , следовательно порт  е0/2 S2 будет Root FWD, а е0/3 в состоянии ALT BLK. Т.к. S3 имеет наибольшее значение BID в сети, и Cost портов е0/0 и е0/1 на коммутаторе S3 и Cost портов е0/2 и е0/3 на коммутаторе S2 одинаковы, следовательно порты е0/0 и е0/1 на коммутаторе S3 переведены в состояние ALT BLK.



Ответим на вопросы в конце самостоятельной работы:

![image](https://user-images.githubusercontent.com/130359715/235443693-daf8f923-c720-4800-90e5-40ccfc395660.png)













