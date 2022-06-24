<div align="center">
  <a href="https://github.com/3xiced/vkbot/">
    <img src="https://sun9-2.userapi.com/impf/rk2ygDyEHBqBLbBUPpWGRKfP4n-envluGtF3Vg/T5XaeQtts3E.jpg?size=1024x1024&quality=95&sign=f48c68a1368be545efd1e88ad36d4ca1&type=album" height="512">
  </a>
</div>

# Compose-services of Rayado

Этот репозиторий отвечает за запуск всех микросервисов.

Для запуска всех ботов и сервисов нужно:

 - Склонировать репозиторий
```
git clone https://github.com/Rayado-Development/compose-services.git
```

 - Если у вас через ssh ключ, то клонируем этой командой
```
git clone git@github.com:Rayado-Development/compose-services.git
```

- Переходим в папку с проектом
```
cd compose-services/
```

- Далее нужно поднять базу данных и pgadmin отдельной командой 
```
docker-compose up --build --no-deps pgadmin postgres
```

- Переходим к pgadmin для создания таблиц в базе данных
```
localhost:5050
```

- Создаем базу данных schedules

- Создаем таблицы в ней
```
CREATE TABLE IF NOT EXISTS shared_schedules(stream_group TEXT NOT NULL, day TEXT NOT NULL, parity TEXT NOT NULL, schedule TEXT NOT NULL);
CREATE TABLE IF NOT EXISTS headman_schedules(stream_group TEXT NOT NULL, day TEXT NOT NULL, parity TEXT NOT NULL, schedule TEXT NOT NULL);
CREATE TABLE IF NOT EXISTS personal_schedules(id INT NOT NULL, stream_group TEXT NOT NULL, day TEXT NOT NULL, parity TEXT NOT NULL, schedule TEXT NOT NULL);
CREATE TABLE IF NOT EXISTS headman_annotations(stream_group TEXT NOT NULL, day TEXT NOT NULL, parity TEXT NOT NULL, annotation TEXT NOT NULL);
CREATE TABLE IF NOT EXISTS personal_annotations(id INT NOT NULL, stream_group TEXT NOT NULL, day TEXT NOT NULL, parity TEXT NOT NULL, annotation TEXT NOT NULL);
CREATE TABLE IF NOT EXISTS headman_changes(stream_group TEXT NOT NULL, day TEXT NOT NULL, parity TEXT NOT NULL, pair_number INT NOT NULL, changes TEXT NOT NULL);
CREATE TABLE IF NOT EXISTS personal_changes(id INT NOT NULL, stream_group TEXT NOT NULL, day TEXT NOT NULL, parity TEXT NOT NULL, pair_number INT NOT NULL, changes TEXT NOT NULL);
```

- Создаем базу данных tgbot и vkbot

- Создаем таблицы в них
```
CREATE TABLE users(user_id integer NOT NULL, date timestamp NOT NULL, command text NOT NULL);
CREATE TABLE config(user_id integer NOT NULL, keyboard_buttons text NOT NULL);
```

- Теперь заносим данные в env файлы

- После командой запускаем проект
```
docker-compose up --build
```

# Разработчики

[Александр Разумов](https://t.me/ALPHA_KENNYBODY)

[Иван Чепиков](https://t.me/darttusin)
