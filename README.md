## Решение задания к занятию "3.1. Работа в терминале, лекция 1"
1. По умолчанию выделено: 1024МБ ОЗУ, 2 ядра, 64гб памяти
2. Чтобы добавить память или ядер нужно прописать следующие команды в конфигурации вагранта:
```Vagrantfile
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
  end
  ```
3.  HISTSIZE(862)

    ignoreboth - шорткат для двух команд ignorespaces и ignoredups, которые не сохраняют комманды начинающиеся на пробелы и дубликаты в истории
4. {} - шаблон использующийся в циклах, функциях, условных операторах(1091)
5. touch {000001..100000}.txt
   Не удастся создать, так как слишком длинный список аргументов
   
6. Проверяет есть ли каталог /tmp
7. mkdir /tmp/new_bash/

   cp /bin/bash /tmp/new_bash/
   
   PATH=/tmp/new_bash/:$PATH
   
   vagrant@vagrant:~$ type -a bash
   
   bash is /tmp/new_bash/bash
   
   bash is /usr/bin/bash
   
   bash is /bin/bash
