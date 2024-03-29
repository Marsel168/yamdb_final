#  CI/CD проекта YaMDb
![workflow](https://github.com/Kolanser/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
 
### Технологии:
- Python=3.7
- Django=2.2.16
- Django Rest Framework API=3.12.4
- Gunicorn=20.0.04
- PostgreSQL
- Docker
- Docker Compose
- GitHub Actions

### CI\CD проекта :
-   автоматический запуск тестов;
-   обновление образа на Docker Hub;
-   автоматический деплой на боевой сервер при пуше в главную ветку  _main_;
- отправка на Telegram-bot сообщения об успешном деплое.

### _Отличный специализированный портал для получения актуальной информации о любых современных произведениях во всех видах искусств!_
#### Проект размещен на сервере Yandex.Cloud. Вы можете увидеть его [*здесь*](http://158.160.38.1/api/v1/).
Проект YaMDb представляет из себя API-ориентированную базу данных произведений в различных сферах искусств и абсолютно всех жанров. YaMDb предоставляет расширенный функционал для взаимодействия пользователей с произведениями а именно:

  
* Создание произведений различных жанров и категорий

* Добавление рецензий к произведениям с возможностью поставить оценку от 1 до 10

* Создание комментариев к конкретному отзыву.

 

Таким образом пользователи могут активно взаимодействовать с ресурсом, общаясь и обсуждая произведения и свои впечатления о них, читать отзывы других пользователей или создавать свои собственные, а так же комментировать и ставить оценки произведениям! Вкупе всё это создает потрясающий программный продукт для пользователя, который хочет получать подробную информацию о конкретном произведении, основанную на персональных ощущениях других пользователей!

  

[![N|Solid](https://img.freepik.com/free-photo/businesspeople-at-office-meeting_23-2148908967.jpg?w=2000&t=st=1661689328~exp=1661689928~hmac=9b24a57975b0c56f0d8762a872114722c62c117f7d0c80f979880b2060f72487)]()

  
На сайте реализована расширенная версия ролей, включающая в себя модератора, который имеет право удалять и редактировать любые отзывы и комментарии. Тем самым внося гармонию, покой и упорядоченность в бурлящих реках онлайн обсуждений!


Кроме всего прочего в проекте реализована полноценная админ зона с полным функционалом для работы со всем контентом проекта!


### Подготовка сервера

1.  Войдите на свой удаленный сервер в облаке.
    
2.  Остановите службу nginx:
   

```
 sudo systemctl stop nginx 
```

3.  Установите docker:


```
sudo apt install docker.io 
```

4.  Установите docker-compose, с этим вам поможет  [официальная документация](https://docs.docker.com/compose/install/).
    
5.  Скопируйте файлы  _docker-compose.yaml_  и  _nginx/default.conf_  из проекта на сервер в  _home/<ваш_username>/docker-compose.yaml_  и  _home/<ваш_username>/nginx/default.conf_  соответственно.
    

Эти файлы всегда копируются вручную. Обычно они настраиваются один раз и изменения в них вносятся крайне редко.

6.  Добавьте в Secrets GitHub Actions переменные окружения для работы базы данных и деплоя.


### «Закинь данные из csv в БД» — достаточно распространённая задача.

В проекте YaMDb реализован программный модуль автоматического наполнения баз данных!

Для это необходимо всего лишь поместить файлы по адресу ```/static/data``` и ввести команду:

```sh

docker compose exec web python manage.py load_data_from_csv

```

Для создания суперпользователя, используйте:

```sh

docker compose exec web python manage.py createsuperuser

```

Соберите статические файлы в единое место (--no-input - без запроса параметров у пользователя):

```sh

docker-compose exec web python manage.py collectstatic --no-input

```

Для остановки работы контейнера, удаления его и томов используйте:

```sh

docker-compose down -v

```

  

### Актуальная информация по взаимодействию с эндпоинтами

  

Для быстрого ориентирования в системе эндпоинтов API в проекте подключена документация API! Воспользоваться ей можно пройдя по адресу:

```sh

http://web/redoc/

```

В ней описаны возможные запросы к API и структура ожидаемых ответов. Для каждого запроса указаны уровни прав доступа: пользовательские роли, которым разрешён запрос, права доступа и дополнительные параметры, если это необходимо.

  
  

### Автор

  

[**Марсель Галиаскаров**](https://github.com/Marsel168)