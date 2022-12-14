# Домашнее задание final

- В репозитории с домашними заданиями создайте каталог `final`. <br>
  Итоговый проект должен содержать:
  - Конфигурацию docker-compose, включающую контейнеры
    - Jenkins
    - Nexus
  - Контейнер Nexus после конфигурации должен содержать 
    - raw-репозиторий для хранения артефактов 
    - пользователя, которого можно будет использовать для загрузки или скачивания файлов из репозитория
  - Контейнер Jenkins после конфигурации должен содержать 
    - Pipeline-задачу, которая выполняет Jenkinsfile из вашего форка репозитория [word-cloud-generator](https://github.com/wickett/word-cloud-generator)
    - Установленный и настроенный плагин для запуска jenkins-агентов в docker. 
    - Учетные данные для подключения к серверу Nexus

&nbsp;
  - Ваш pipeline должен храниться в файле Jenkinsfile вашего форка репозитория [word-cloud-generator](https://github.com/wickett/word-cloud-generator) и состоять из:
    - Получения исходных кодов из репозитория 
    - Тестирования приложения (make lint, make test)
    - Сборки приложения
    - Загрузки артефактов в репозиторий Nexus
    - Интеграционного тестирования (запуск приложения в контейнере и обращение к нему по сети)
  - Сборка проекта должна выполняться в jenkins-agent, запущенном в докер-контейнере из образа [golang:1.16](https://hub.docker.com/layers/library/golang/1.16/images/sha256-8da77ed09ebe25cd79ce03092e009f3c13d684c827f61ca5236a2df26d387a55?context=explore)
  - Для запуска интеграционных тестов создайте docker-контейнер из Dockerfile, который расположен в репозитории вместе с Jenkinsfile. В качестве базового образа для Dockerfile используйте образ [alpine:latest](https://hub.docker.com/layers/alpine/library/alpine/latest/images/sha256-8d99168167baa6a6a0d7851b9684625df9c1455116a9601835c2127df2aaa2f5?context=explore). Собранное приложение word-cloud-generator должно запускаться в этотм контейнере.
