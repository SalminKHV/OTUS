# Развертывание коммутируемой сети с резервными каналами







#### 1. Топология сети

![image](https://user-images.githubusercontent.com/130359715/235008936-c16ab360-6a1a-4f06-93c4-012c57ff2be9.png)

#### 2. Таблица адресации и цели:

![image](https://user-images.githubusercontent.com/130359715/235009373-7dae1d4b-5427-43cc-b0d8-1344006e0e57.png)

![image](https://user-images.githubusercontent.com/130359715/235009495-6fe79d3d-53bd-4dff-8098-3898c59f8603.png)





## Решение

[Часть 1]()

[Часть 2]()

[Часть 3]()

[Часть 4]()

#### Часть 1

Произведем первоначальные настройки коммутаторов S1, S2, S3, т.к. первоначальные настройки на устройствах идентичны, проведем настройку на примере коммутатора S1.       

Отключим поиск DNS командой **#no ip domain lookup**

Присвоим имя устройству командой **#hosname S1**

Назначим пароль для доспупа в привилегированный режим:

**#enable password class**

**#login**

Назначим пароль **cisco** в качестве паролей консоли и VTY и активируем вход:

**#line console 0**

перейдя к настройке консольного канала, сразу настроим **"logging synchronous"** командой **S1(config-line)#logging synchronous**

**#password cisco**

**#login**

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

Проверии первоначальные настройки:

проверим доступность коммутаторов S2 и S3 с ком-ра S1:

![image](https://user-images.githubusercontent.com/130359715/235069913-6be08afa-e494-467c-9812-f5f0cd3ee188.png)

проверим доступность коммутаторов S1 и S3 с ком-ра S2:

![image](https://user-images.githubusercontent.com/130359715/235070493-4bfc17ec-63b8-4cf0-868c-ffe595bcc83b.png)

проверим доступность коммутаторов S1 и S2 с ком-ра S3:

![image](https://user-images.githubusercontent.com/130359715/235072701-e17f3438-624f-40f6-aacd-5f6be7bd8978.png)



#### Часть 2

##### Шаг 1 Отключим все порты на всех коммутаторах на примере S1

![image](https://user-images.githubusercontent.com/130359715/235074203-a33ad2c6-4012-4c35-bc50-4d4731d951da.png)

##### Шаг 2 Настроим подключенные порты в кастве транков, предварительно включив encapsulation Dot1Q

![image](https://user-images.githubusercontent.com/130359715/235075614-b565edd7-fb4b-48b0-9888-44bd6ad4228f.png)

##### Шаг 3 Включим порты e0/0 и e0/2 на всех коммутаторах:

