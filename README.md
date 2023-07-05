#    Prometheus. Zabbix.

Задание:

```text
Настроить дашборд с 4-мя графиками

    память;
    процессор;
    диск;
    сеть.
    Настроить на одной из систем:
    zabbix (использовать screen (комплексный экран);
    prometheus - grafana.
```

Выполнение:

```bash
    git clone https://github.com/zabbix/zabbix-docker.git
    cd zabbix-docker
    git checkout 5.0
    docker-compose -f docker-compose_v3_centos_mysql_latest.yaml --profile all up
    docker-compose -f docker-compose_v3_alpine_mysql_latest.yaml up -d
    docker ps #узнаем ID контейнера с запущенным zabbix-agent. В моем случае 7e4e73b689af
    docker inspect 7e4e73b689af #узнаем ip-адрес запущенного контейнера с агентом
```
Далее заходим по адресу 127.0.0.1, логин пароль: Admin zabbix, идем в Configuration-Hosts-Zabbix server и в поле Agent IP address пишем ip-адрес запущенного контейнера с агентом.
Затем настраиваем необходимые графики на dashboard.
![zabbix]([http://url/to/img.png](https://github.com/Dekkert/dz14_prometheus_zabbix/blob/master/zabbix.png)https://github.com/Dekkert/dz14_prometheus_zabbix/blob/master/zabbix.png)
