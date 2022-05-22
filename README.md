## Домашнее задание к занятию "5.2. Применение принципов IaaC в работе с виртуальными машинами"
1. 
 - Автоматизация процесса тестирования, деплоя ПО снижает трудозатраты компании, позволяет как можно скорее выявить ошибки, а также быстро подготовить продукт для релиза.
 - Основопологающим принципом является идемпотентность
 - 
2. 
 - Ansible использует существующую SHH инфраструктуру, другие инструменты требуют дополнительных действий для установки соединения.
 - Push метод является более надежным, так как при pull-методе, мы не знаем, когда была изменена конфигурация, нам необходимо каждый раз запрашивать изменения. В push-методе, как только были внесены изменения на целевой конфигурации, изменения будут отправлены сразу и на другие сервера.

3. 
```
alexander@alexander:~/Downloads$ vagrant -v
Vagrant 2.2.6
```
```
alexander@alexander:~/Downloads$ ansible --version
ansible 2.9.6
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/home/alexander/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  executable location = /usr/bin/ansible
  python version = 3.8.10 (default, Nov 26 2021, 20:14:08) [GCC 9.3.0]
```
```
При запуске команды virtualbox --version запускается само приложение виртуалбокса
```
