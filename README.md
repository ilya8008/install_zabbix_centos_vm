install_zabbix_centos_vm
------------

Установка zabbix-agent

Требования
------------

Т.к. подключение через ssh осуществляется с использованием ключей,
нужно прописать параметры соединения в ~/.ssh/config

Параметры в ansible.cfg (remote_user можно указать непосредственно в playbook, из которого вызывается роль)

[defaults]
remote_user = удаленный пользователь
roles_path = ./roles


Переменные
--------------

Адрес, на котором будет слушать агент:

'listen_ip_address: 127.0.0.1'

Адрес сервера zabbix:

'zabbix_server_address: zabbix-server.localdomain'


Пример playbook
----------------

```
- name: Install zabbix agent CentOS
  hosts: zabbix
  become: true
  vars:
    zabbix_server_address: zabbix-server.localdomain
    listen_ip_address: "{{ansible_eth0.ipv4.address}}"
  roles:
    - install_zabbix_centos_vm
```

