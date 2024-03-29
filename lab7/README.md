# IS-IS



#### Цель:

Настроить IS-IS офисе Триада

#### Описание выполнения домашнего задания:

1. Настроим IS-IS в ISP Триада.
2. R23 и R25 находятся в зоне 2222.
3. R24 находится в зоне 24.
4. R26 находится в зоне 26.



#### Имеющаяся топология сети Триада:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/717e4cb3-f207-4f98-a612-d65e951bde38)



Произведем настройку роутеров, на примере роутера R25. Для начала мы активируем протокол маршрутизации командой 

R25(config)#router isis

затем зададим ему название сетевого объекта (Network Entity Title) с указанием зооны "2222" и идентификатора роутера, совпадающий, с loopback (для R25   --- 5.20.0.25):

R25(config-router)#net 49.2222.0005.0020.0.025.00  
R25(config-router)#exi  

Затем активируем IS-IS - протокол на портах маршрутизатора:  

R25(config)#int ra e0/0-2, e1/0  
R25(config-if-range)#ip router isis  

![image](https://github.com/SalminKHV/OTUS/assets/130359715/10a746d3-17cc-4424-84c9-365ee127b5cb)

так, как на маршрутизаторах R23, R24, R26 уже настроена маршрутизация, мы можем посмотреть установившиеся DIS-ы и роутеры, учавствующие в маршрутизации по протоколу IS-IS.

Также можем посмотреть состояние соседей на роутере R23:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/61ebbfcf-d7e1-4243-a3bb-8306387eb071)

проверить в какой зоне находится наш роутер мы можем командой show Run или show clns:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/37cb7118-9a38-4952-bdc7-c1f801189e1d)

Отключим отношения Level2 между R23 и R25:

R25(config-if)#int e0/0  
R25(config-if)#isis circuit-type level-1  

![image](https://github.com/SalminKHV/OTUS/assets/130359715/9c94e43d-1fe4-42f1-b05c-e4219c711631)
