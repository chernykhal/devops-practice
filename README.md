## Домашнее задание к занятию "5.2. Применение принципов IaaC в работе с виртуальными машинами"
1. https://hub.docker.com/r/aledcherry/netology-devops-practice
2. 
 - Высоконагруженное монолитное java веб-приложение:

   Контейнеры точно нет, так как в одном контейнере должно быть одно приложение. В данном случае больше подойдет физический сервер либо виртуальная машина
   
 - Nodejs веб-приложение:
 
   Для данной задачи вполне подойдет контейнер. Нода является серверным языком, хорошо вписывается в микросервисы.
   
 - Мобильное приложение c версиями для Android и iOS:
 
   Мобильные приложения так или иначе скичиваются на устройства пользователя. Если приложение запрашивает какие-либо данные в рантайме, то необходимо серверное решение, которое будет предоставлять эти данные. В зависимости от выбранного архитектурного решения будет меняться и выбор инструмента. Например, если серверное приложение будет построенно на микроархитектуре, то в таком случае будет оптимальным выбор docker. Если это монолит, то  лучше подойдет физическое железо или виртуалка. Если приложение, которое предоставляет данные является обычной бд, то подойдет любой вариант. Сложный вопрос :)
   
  - Шина данных на базе Apache Kafka:

    Контейнеры могут стать оптимальным решением. В данном случае будет дороже сделать виртуалку или выделить целый сервер под этот сервис.
    
  - Elasticsearch кластер для реализации логирования продуктивного веб-приложения - три ноды elasticsearch, два logstash и две ноды kibana:
    
    В данном случае контейнеры подойдут лучше всего, к тому же уже есть официальные образы контейнеров этих продуктов.

  - Мониторинг-стек на базе Prometheus и Grafana:

    Для монтиоринг-стека подойдут контейнеры. В продукт будут вноситься изменения, добавляться новые метрики. Мы сможем версионировать контейнеры, применять IaaC

  - MongoDB, как основное хранилище данных для java-приложения:

    Есть все тот же официальный контейнер для MongoDB, на его базе можно развернуть хранилище данных.

  - Gitlab сервер для реализации CI/CD процессов и приватный (закрытый) Docker Registry.
    
    Необходим физический сервер или виртуализация, данные довольно больше, их не стоит складывать в контейнер.

3. 
 - Запускаю контейнер из образа centos
```
alexander@alexander:~/Documents/Docker$ sudo docker run -d -v /data:/data centos sleep infinity
508bc63715ba39994f8c788b030e88cf2e071e7cfa9022a6ca544d63b02ade77
```
 - Запускаю контейнер из образа debian
```
alexander@alexander:~/Documents/Docker$ sudo docker run -d -v /data:/data debian sleep infinity
6bf431e77493147c93e9e5cb289e23aa9a8cf06d7bc12957e9b3d856adcd8778
```
- Запущены оба контейнера
```
alexander@alexander:~/Documents/Docker$ sudo docker ps
CONTAINER ID   IMAGE     COMMAND            CREATED          STATUS          PORTS     NAMES
6bf431e77493   debian    "sleep infinity"   56 seconds ago   Up 54 seconds             wonderful_bose
508bc63715ba   centos    "sleep infinity"   3 minutes ago    Up 3 minutes              hopeful_murdock
```
 - Создаю файл в волюме из первого контейнера
```
alexander@alexander:~/Documents/Docker$ sudo docker exec -it 508bc63715ba bash
[root@508bc63715ba /]#echo 'Created from centos container' >> /data/centos.txt
[root@508bc63715ba /]# cat /data/centos.txt
Created from centos container
```
 - Создаю файл через хост машину
```
alexander@alexander:~/Documents/Docker$ echo 'Created from host' >> ./data/host.txt
alexander@alexander:~/Documents/Docker$ cat ./data/host.txt 
Created from host
```
 - В результате выполнения всех шагов, на втором контейнере отображается файл, созданный на первом контейнере, а файла с хоста нету.
```
root@6bf431e77493:/data# ls -la
total 12
drwxr-xr-x 2 root root 4096 Jun  2 17:35 .
drwxr-xr-x 1 root root 4096 Jun  2 17:26 ..
-rw-r--r-- 1 root root   30 Jun  2 17:35 centos.txt
```
