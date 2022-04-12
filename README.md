## Домашнее задание к занятию "5.1. Введение в виртуализацию. Типы и функции гипервизоров. Обзор рынка вендоров и областей применения."
1. 
- Полная виртуализация:
	В данном случае гипервизор является сам по себе операционной системой, ему не нужна ОС, такая виртуализация может работать на чистом сервере без предустановленной ОС

- Паравиртуализация:
	Виртулизация, при которой необходима предустановленная ОС, гипервизор с помощью неё получает доступ к ресурсам сервера

- Виртуализация на основе ОС:
	Виртуализация, при которой все установленные виртуальные машины дополнительно изолированны и защищены друг от друга, но на каждой из этих виртуалок должна быть такая же версия ядра, что и на целевом сервере. Данная виртуализация не использует какой-то отдельный гипервизор, она работает напрямую с железом сервера

2.
Высоконагруженная база данных, чувствительная к отказу - Физические сервера. Немного не понял, что тут подразумевается, полная виртуализация или просто физический сервер(может это и имелось ввиду одно и то же). Но если брать просто физический сервер, то мы получаем единую точку отказа, это хостовая ОС, что поможет при дальнейшем дебаге.
Различные web-приложения - виртуализация уровня ОС. Как я понял, в IaaC используется именно этот метод. Могу это лишь обосновать тем, что для приложений такого метода существуют процессы непосредственно на самой хостовой машине, что позволяет лучше дебажить и устранять проблемы.
Windows системы для использования бухгалтерским отделом - Паравиртуализация. 
Системы, выполняющие высокопроизводительные расчеты на GPU - Физические сервера

3.

