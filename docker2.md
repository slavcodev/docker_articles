Docker myths and receipts. Semi-automatic leg-homing gun
========

Начало: https://github.com/grikdotnet/docker_articles/blob/master/docker1.md

**Как не надо использовать Docker.**

Чтобы понимать эту статью надо знать базовые команды Dockerfile для создания изображений и принципы объектно-ориентированного дизайна. 

Открываю документацию любого официального образа сервисного ПО - например, [Nginx](https://hub.docker.com/_/nginx/) и нахожу раздел "How to use this image".
Нам предлагают создать свой образ на базе официального, скопировав в него наши файлы, настроить мапинг порта в мир, и подмонтировать свою папку с конфигами.
Это же нам предлагают сделать в образах [PHP](https://hub.docker.com/_/php/), [Pyhon](https://github.com/docker-library/docs/blob/master/python/README.md) и так далее.
```
FROM ...
COPY . /usr/src/myapp
WORKDIR /usr/src/myapp
```

Да, нам предлагают унаследовать Model от View в одном звездном классе. В случае с Python и Ruby это даже не предлагают, авторы  захардкодили это в триггерах на построение изображений-наследников, "which should be all you need" - как 640 килобайт.

К счастью, решение известно так же давно как проблема. Банда четырех, создатель Java Джеймс Гослинг и Фаулер последние 20 лет твердят: используйте композицию вместо наследования.
Поэтому я положу контейнеры рядом, создам адаптер, data transfer object, и свяжу их через конфиг.

Продолжение: https://github.com/grikdotnet/docker_articles/blob/master/docker3.md