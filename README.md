#  Домашнее задание к занятию «Система мониторинга Zabbix Часть 2»

---

`Мантуров Максим Андреевич`
---

#### Задание № 1 
- `Создание своего шаблона, в котором будут элементы данных, мониторящие загрузку CPU и RAM хоста.`

---
`Решение`
- Был создан шаблон  `CPU-MEM-WORK-1` и в нем созданы 2 элемента данных.
- `1` CPU IN %  `Мониторинг загрузки процессора в процентах`
- `2` MEMORY IN % `Мониторинг загрузки памяти в процентах`

> Для создания элемента данных были использованы следующие Поддерживаемые ключи элементов
> Для CPU IN %  `system.cpu.util`
> Для MEMORY IN % `vm.memory.size`
![1-7](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_1/7.png)
![1-8](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_1/8.png)
---
- `Ход выполнения задания.`
![1-1](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_1/1.png)
---
- `На скриншоте представлены пустые Элементы данных`
![1-2](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_1/2.png)
---
- `Начало создания Элемента данных`
![1-3](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_1/3.png)
![1-4](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_1/4.png)
![1-5](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_1/5.png)
---
- `Созданные Элементы данных`
![1-6](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_1/6.png)

#### Задание № 2 
- `Добавить в Zabbix два хоста и задайть им имена <фамилия и инициалы-1> и <фамилия и инициалы-2>. Например: ivanovii-1 и ivanovii-2.`
- `Прикрепить за каждым хостом шаблон Linux by Zabbix Agent`
- `Проверить что в разделе Latest Data начали появляться данные с добавленных агентов`

--- 
`Решение`

- `Добавленные и переименованные хосты`
![2-1](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_2/2.png)
---
- `Добавленные шаблоны Linux by Zabbix Agent`
![2-2](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_2/3.png)
![2-3](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_2/4.png)
---
- `Раздел Latest Data с свежими данными.`
![2-4](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_2/5.png)
![2-5](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_2/6.png)
---

#### Задание № 3 
- `Привязать созданный шаблон к двум хостам. Также привязать к обоим хостам шаблон Linux by Zabbix Agent.`
- `Проверить что в раздел Latest Data начали поступать необходимые данные из созданного шаблона`

---
`Решение`
- `HOST №1`
![3-1](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_3/1.png)
![3-2](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_3/3.png)
![3-3](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_3/4.png)
![3-4](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_3/2.png)
![3-5](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_3/5.png)
---
- `HOST №2`
![3-6](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_3/6.png)
![3-7](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_3/7.png)
![3-8](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_3/9.png)
![3-9](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_3/8.png)
![3-10](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_3/10.png)
---
#### Задание № 3 
- `Создайте свой кастомный дашборд.`

---
`Решение`
![4-1](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_4/1.png)
![4-2](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_4/2.png)
![4-3](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_4/3.png)
![4-4](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_4/4.png)
![4-5](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_4/5.png)
![4-6](https://github.com/MaximMantr/Monitoring/blob/zabbix_2/img/Zabbix_2/work_4/6.png)
> ### Спосибо за внимание!
