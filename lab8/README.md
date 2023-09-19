# EIGRP



#### Цель:

Настроить EIGRP в С.-Петербург, использовав named EIGRP

#### Описание/Пошаговая инструкция выполнения домашнего задания:

1. В офисе С.-Петербург настроим EIGRP-named.
2. R32 получает только маршрут по умолчанию.
3. R16-17 анонсируют только суммарные префиксы.



![image](https://github.com/SalminKHV/OTUS/assets/130359715/098e9646-af30-4c2b-80b2-9057c10f3ef5)



Первым делом настроим на устройствыах именнованный EIGRP на примере R32:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/422ac6ca-36a1-4b6b-b74f-5380a760d246)



На R32 прописали сети, которые хотим передавать по протоколу EIGRP, и роутер ID.

Далее на роутере R16 настроим суммаризованный маршрут в сторону R32 в виде маршрута по умолчанию,  а также настроим суммаризованный маршрут в сторону R18, настроим сети, которые хотим маршрутизировать по протоколу EIGRP и настроим router-id. Также на R17настроим суммаризованный маршрут с второну R18 и конечно настроим сети, которые хотим маршрутизировать по протоколу EIGRP и настроим router-id. 

![image](https://github.com/SalminKHV/OTUS/assets/130359715/2d3a0d8b-302a-4a85-9582-ecde94c7bbc5)

Конфиг R18:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/aaa74e0f-1057-4bd6-a906-fc34f94ad30b)

Конфиг R17:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/7d329dff-038f-442a-8011-41f93d9ad089)

Настроим коммутаторы sw9 и sw10:

SW9:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/02a698ad-bb70-49c7-b320-64496612b35a)

SW10:

![image-20230919213219188](https://github.com/SalminKHV/OTUS/assets/130359715/73c2c304-42db-4318-a1ad-6bd6a89197c0)

Проверим таблицы маршрутизации на роутерах и коммутаторах, мы должены увидеть на роутере R18 только суммаризованный маршрут в сеть 204.2.0.0/16 через роутеры R17 и R16, а также роутер R32 будет получать от R16 только маршрут по умолчанию:

R18:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/97a2b03a-efca-4702-8c1c-8ecde48141d9)

R32:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/b3996cca-4853-41dc-8f2e-15eb687288eb)

R16:



![image-20230919214700702](https://github.com/SalminKHV/OTUS/assets/130359715/e506177f-2314-4da4-a053-06a51db09d2a)

R17: 

![image-20230919214945017](https://github.com/SalminKHV/OTUS/assets/130359715/61476dbd-0ea1-42f1-9506-f9b885e470d7)



SW9:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/e1c41c2f-a8a5-45e2-97fa-c8eb23feefff)

Пропишем на интерфейсах коммутаторов SW9 и SW10, к которым подключены VPC включим настройку passiv-interface в целях безопасности.

![image](https://github.com/SalminKHV/OTUS/assets/130359715/045920a8-745c-4044-b527-b35ecf3017ed)

Проверим доступность роутеров с компьютеров: 

![image](https://github.com/SalminKHV/OTUS/assets/130359715/df3f7ceb-d71a-4630-b034-659c8ec6eae3)
