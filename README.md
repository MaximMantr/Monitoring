#  Домашнее задание к занятию «Система мониторинга Zabbix»

---

`Мантуров Максим Андреевич`
---

#### Задание № 1 [Установка и настройка Zabbix]
- Установить PostgreSQL.
- Пользуясь конфигуратором команд с официального сайта, составить набор команд для установки последней версии Zabbix с поддержкой PostgreSQL и Apache
- `Мной был выбран NGINX, так как он у меня уже был установлин и работал`
- Выполнить все необходимые команды для установки Zabbix Server и Zabbix Web Server
---
`Команды для установки`
```
1. Установите репозиторий Zabbix
wget https://repo.zabbix.com/zabbix/6.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.4-1+ubuntu22.04_all.deb
dpkg -i zabbix-release_6.4-1+ubuntu22.04_all.deb
apt update

------------------------------------------------------
2.Установите Zabbix сервер, веб-интерфейс и агент
apt install zabbix-server-pgsql zabbix-frontend-php php8.1-pgsql zabbix-nginx-conf zabbix-sql-scripts zabbix-agent

2.1 Для apache2 будут следующие комманды 
apt install zabbix-server-pgsql zabbix-frontend-php php8.1-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent

-------------------------------------------------------
3.Создайте базу данных
sudo -u postgres createuser --pwprompt zabbix
sudo -u postgres createdb -O zabbix zabbix

На хосте Zabbix сервера импортируйте начальную схему и данные. Вам будет предложено ввести недавно созданный пароль
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix

-------------------------------------------------------
4.Настройте базу данных для Zabbix сервера
Отредактируйте файл /etc/zabbix/zabbix_server.conf

DBPassword=password //Отредактировать 

--------------------------------------------------------
5.Настройте PHP для веб-интерфейса
Отредактируйте файл /etc/zabbix/nginx.conf раскомментируйте и настройте директивы 'listen' и 'server_name'.

listen 8080;
server_name example.com;

--------------------------------------------------------
6.Запустите процессы Zabbix сервера и агента
systemctl restart zabbix-server zabbix-agent nginx php8.1-fpm
systemctl enable zabbix-server zabbix-agent nginx php8.1-fpm

6.1 Для apache2 будут следующие комманды 

systemctl restart zabbix-server zabbix-agent apache2
systemctl enable zabbix-server zabbix-agent apache2
```
`Скриншоты настроеноеных`
- Zabbix Server
- Zabbix Agent
- Zabbix Web Server
---
![1-1](https://github.com/MaximMantr/Monitoring/blob/master/img/Zabbix/Zabbix-admin/1.png)
![1-3](https://github.com/MaximMantr/Monitoring/blob/master/img/Zabbix/Zabbix-admin/3.png)
![1-2](https://github.com/MaximMantr/Monitoring/blob/master/img/Zabbix/Zabbix-admin/2.png)
![1-6](https://github.com/MaximMantr/Monitoring/blob/master/img/Zabbix/Zabbix-admin/6.png)

- `На последним скриншоте показан Web interface Zabbix где мной уже была проведина авторизация.`
- `Доступ к Web Server я настроил по порту :8085` 
![1-5](https://github.com/MaximMantr/Monitoring/blob/master/img/Zabbix/Zabbix-admin/5.png)
---
#### Задание № 2 [Установка Zabbix-agent и их настройка]
- Установить Zabbix Agent на 2 вирт.машины, одной из них может быть Zabbix Server
- Добавить Zabbix Server в список разрешенных серверов  Zabbix Agentов
- Добавить Zabbix Agentов в раздел Configuration > Hosts моего Zabbix Servera.
- Проверить, что в разделе Latest Data начали появляться данные с добавленных агентов.
---
- `Ход выполнения задания.`
Мной была создана виртуальная машина Ubuntu 24.04 LTS. И после был установклен Zabbix-agent
Команды которые были спользованы мной.

```
1.Установите репозиторий Zabbix
wget https://repo.zabbix.com/zabbix/6.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.4-1+ubuntu24.04_all.deb
dpkg -i zabbix-release_6.4-1+ubuntu24.04_all.deb
apt update

--------------------------------------------------------
2. Установите Zabbix агент
apt install zabbix-agent

--------------------------------------------------------
3. Нужно отредактировать файл /etc/zabbix/zabbix_agent.conf
# ListenPort=10050 // Где 10050 это порт Zabbix-agent
ListenIP=*.*.*.*  // Где *.*.*.* это ip адресс Zabbix-agent в моем случае это 192.168.0.103 

--------------------------------------------------------
4.Запустите процесс Zabbix агента
systemctl restart zabbix-agent
systemctl enable zabbix-agent
```
---
`Скриншоты настроеноеных`
- Zabbix-agent
- Web interface с добавленными агентами и выполнеными пунктами из задания 
---
- `Zabbix-agent на Ubuntu 24.04 LTS.`
![2-4](https://github.com/MaximMantr/Monitoring/blob/master/img/Zabbix/Zabbix-admin/4.png)
- `Zabbix-agent на моем хосте.`
![2-3](https://github.com/MaximMantr/Monitoring/blob/master/img/Zabbix/Zabbix-admin/3.png)
---
- `Добавленые Zabbix-agent`
![2-1](https://github.com/MaximMantr/Monitoring/blob/master/img/Zabbix/Zabbix-agent/1.png)
---
`Вывод log можно посмотреть командой`
```
cat /var/log/zabbix/zabbix_agentd.log
```

- `С Ubuntu 24.04 LTS.`
![1-3](https://github.com/MaximMantr/Monitoring/blob/master/img/Zabbix/Zabbix-agent/3.png)
- `С моего хоста`
![2-2](https://github.com/MaximMantr/Monitoring/blob/master/img/Zabbix/Zabbix-agent/2.png)
---
- `Раздел Latest Data где появились данные с добавленных агентов `
![2-4](https://github.com/MaximMantr/Monitoring/blob/master/img/Zabbix/Zabbix-agent/4.png)
![2-5](https://github.com/MaximMantr/Monitoring/blob/master/img/Zabbix/Zabbix-agent/5.png)
![2-6](https://github.com/MaximMantr/Monitoring/blob/master/img/Zabbix/Zabbix-agent/6.png)
---
> ### Спосибо за внимание!
