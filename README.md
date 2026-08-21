# Lesson36_dns

### Задание  

Создать домашнюю сетевую лабораторию. Изучить основы DNS, научиться работать с технологией Split-DNS в Linux-based системах

1. взять стенд https://github.com/erlong15/vagrant-bind 
добавить еще один сервер client2
завести в зоне dns.lab имена:
web1 - смотрит на клиент1
web2  смотрит на клиент2  
завести еще одну зону newdns.lab
завести в ней запись
www - смотрит на обоих клиентов

3. настроить split-dns
клиент1 - видит обе зоны, но в зоне dns.lab только web1
клиент2 видит только dns.lab




***
### Решение
у нас два dns сервера \
alp-ns1 192.168.50.216 \
alp-ns2 192.168.50.215 

есть два клиента \
alp-nginx-web 192.68.50.219 \
alp-log 192.168.217 \

плейбук для устновки bind9 и утилит 
```

---
- name: Установка bind и утилит
  hosts: ns_servers
  become: yes
  tasks:
    - name: Установить bind9
      apt:
        name: bind9
        state: present
        update_cache: yes

    - name: Установить bind9-utils
      apt:
        name: bind9-utils
        state: present

    - name: Установить dnsutils
      apt:
        name: dnsutils
        state: present

    - name: Установить chrony для синхронизации времени
      apt:
        name: chrony
        state: present
      
```











