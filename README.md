<div align="center">
  <img src="https://media.giphy.com/media/dWesBcTLavkZuG35MI/giphy.gif" width="500" height="250"/>
</div>

### 1. Инструкция по добавлению статики на web-сервер Яндекс.Облако.
Копируем папку со статикой на сервер:
```
scp -r /локальный_путь_до_папки_на_ПК/static логин_сервера@IP_сервера:/home/логин/папка_с_проектом/папка_хранения_статики
```
Настраиваем права доступа к папке static на сервере:
1) добавляем учетную запись в группу:
```
www-data sudo usermod -a -G ТУТ-ИМЯ-ПОЛЬЗОВАТЕЛЯ www-data
```
2) устанавливаем права:
```
sudo chown -R :www-data /полный_путь_до_папки_статики
```

### :fire: Мой статус :
[![GitHub Streak](http://github-readme-streak-stats.herokuapp.com?user=grwo1&theme=dark&background=000000)](https://git.io/streak-stats)
