### Небольшая инструкция-шпаргалка по технологиям изучаемых на Яндекс.Практикум
<div align="center">
  <img src="https://media.giphy.com/media/dWesBcTLavkZuG35MI/giphy.gif" width="500" height="250"/>
</div>

<details>
<summary><b>Инструкция по работе с базами данных. Запросы.</b></summary>
<details>
<summary><b>Создане таблицы. Заполнение. Вывод данных.</b></summary>
      
Создаем таблицу artists с двумя полями(с типом данных):
```
CREATE TABLE artists(name TEXT, year_of_birth INTEGER);
```
</details>
  
</details>

<details>
<summary> <b>Инструкция по добавлению статики на web-сервер Яндекс.Облако.</b></summary>
Открываем терминал и копируем папку со статикой на сервер:
  
```
scp -r /локальный_путь_до_папки_на_ПК/static логин@IP_сервера:/home/логин/папка_с_проектом/папка_хранения_статики
```
  
> Пример: scp -r /Files/yandex.praktikum/static grwo1@84.221.111.206:/home/grwo1/hw05_final/yatube
  
Настраиваем права доступа к папке static на сервере:
1) добавляем учетную запись в группу:
  
```
www-data sudo usermod -a -G ЛОГИН www-data
```
  
2) устанавливаем права:
  
```
sudo chown -R :www-data /полный_путь_до_папки_статики
```
  
</details>

### :fire: Мой статус :
[![GitHub Streak](http://github-readme-streak-stats.herokuapp.com?user=grwo1&theme=dark&background=000000)](https://git.io/streak-stats)
