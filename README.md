### Небольшая инструкция-шпаргалка по технологиям изучаемых на Яндекс.Практикум(Бэкенд на Django)
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
Делаем запись в таблицу:
```
INSERT INTO artists VALUES('Eminem', 1972);
```
Вернуть все поля и все записи таблицы artists:
```
SELECT * FROM artists;
```
Вернуть заданные поля и отсортированные записи таблицы artists:
```
SELECT name FROM artists WHERE year_of_birth = 1972;
```
> Запрос вернет: Eminem
</details>
<details>
<summary><b>Получение данных: SELECT, FROM, WHERE, DISTINCT.</b></summary>

#### Фильтрация по столбцам
Рассмотрим БД со следующими полями:
name | genre | year_of_birth
:----- | :----: | :-----:
Eminem  | Hip-hop | 1972
Linkin Park  | Alternative  | 1996
Metallica  | Metal  | 1981
- Оператор SELECT - указывают названия полей, значения которых должны вернуться в ответе;
- FROM — названия таблиц, в которых надо искать данные.
```
SELECT name,
       year_of_birth
FROM artists; 
```
При таком запросе вернется:
name | year_of_birth
:----- | :-----:
Eminem | 1972
Linkin Park | 1996
Metallica | 1981
#### Фильтрация по строкам
- WHERE - фильтрует записи в базе данных
```
SELECT *
FROM artists
WHERE year_of_birth > 1990;
```
При таком запросе вернется:
name | genre | year_of_birth
:----- | :----: | :-----:
Linkin Park  | Alternative  | 1996
#### Оператор сравнения для WHERE:
- = - проверка равенства
- <> - проверка неравенства
- \> - больше
- < - меньше
- \>= - больше или равно
- <= - меньше или равно
- BETWEEN начало_диапазона AND конец_диапазона - проверка в диапазоне значений. Например:
```
SELECT name       
FROM artists
WHERE year_of_birth BETWEEN 1980 AND 1990;
```
При таком запросе вернется:
name 
:-----
Metallica
- IN - вхождение в список
```
SELECT *       
FROM artists
WHERE genre IN ('Alternative', 'Metal');
```
name | genre | year_of_birth
:----- | :----: | :-----:
Linkin Park  | Alternative  | 1996
Metallica  | Metal  | 1981
- LIKE - использование маски для вывода данных.

Символ | Значение
:-----: | :----
\% | любое количество символов(в том числе и 0)
\_ | один символ(цифра, буква, пробел, пунктуационный или любой другой)
```
SELECT *       
FROM artists
WHERE genre LIKE 'Hip%';
```
При таком запросе вернется:
name | genre | year_of_birth
:----- | :----: | :-----:
Eminem  | Hip-hop | 1972

Больше операторов можно посмотреть [ТУТ](https://www.techonthenet.com/sqlite/comparison_operators.php)

Оператор WHERE позволяет использовать множество условий одновременно. Для объединения сразу нескольких условий используются операторы AND, OR или NOT.
```
SELECT *       
FROM artists
WHERE genre LIKE 'Hip%' OR year_of_birth = 1981;
```
При таком запросе вернется:
name | genre | year_of_birth
:----- | :----: | :-----:
Eminem  | Hip-hop | 1972
Metallica  | Metal  | 1981
- DISTINCT - вывод уникальных значений

Рассмотрим БД со следующими полями:
name | genre | year_of_birth
:----- | :----: | :-----:
Eminem | Hip-hop | 1972
Linkin Park | Alternative  | 1996
Metallica | Metal  | 1981
IceCube | Hip-hop | 1969
DrDre | Hip-hop | 1965
```
SELECT DISTINCT genre
FROM artists;
```
При таком запросе вернется:
genre 
:----:
Hip-hop
Alternative
Metal
</details>
  
<details>
<summary> <b>Агрегирующие функции COUNT, MIN, MAX, AVG, SUM.</b></summary>

В общем виде запрос с агрегирующией функцией выглядит так:
```
SELECT АГРЕГИРУЮЩАЯ_ФУНКЦИЯ(поле)    
FROM Таблица;
```
Рассмотрим БД со следующими полями:
name | genre | year_of_birth | albums
:----- | :----: | :-----: | :-----:
Eminem | Hip-hop | 1972 | 11
Linkin Park | Alternative  | 1996 | 7
Metallica | Metal  | 1981 | 11
IceCube | Hip-hop | 1969 | 10
DrDre | Hip-hop | 1965 | 3
- COUNT  - подсчет количесва записей в БД. Через COUNT можно подсчитать число записей в любой выборке, например, с условием  WHERE.
```
SELECT COUNT(*)
FROM artists; 
```
При таком запросе вернется: 5

- MIN и MAX - поиск минимального или максимального значения в БД.
```
SELECT MIN(albums)
FROM artists;
```
При таком запросе вернется: 3

- AVG и SUM - средние значение или сумма по столбцу. Может быть ограничена с помощью WHERE.
```
SELECT AVG(albums)
FROM artist
WHERE year_of_birth > 1980;
```
При таком запросе вернется: 9
</details>
<details>
<summary> <b>Группировка GROUP BY и фильтрация HAVING.</b></summary>
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

<details>
<summary> <b>Инструкция по git push по логину и паролю.</b></summary>

Настроить ввод логина и пароля при push:

```
git config remote.origin.url https://github.com/ЛОГИН_GITHUB/ВЕТКА_ПРОЕКТА.git
```
Создаем на GitHub персональный token.

1. переходим в Settings профиля на GitHub.

2. слева выбираем Developer settings.

3. Жмем Personal access tokens.

4. Жмем Generate new token.

5. Задаем имя и время.

6. Выбираем repo.

7. Жмем Generate token.

8. Копируем и вставляем вместо пароля при push.
  
<div align="center">
  <img src="https://mycyberuniverse.com/images/webp/articles/Arthur/how-fix-fatal-authentication-failed-for-https-github-com/1.webp" width="500" height="250"/>
</div>
  
Push проекта:
```
git push -u -f origin master
```

</details>

<details>
<summary> <b>Инструкция по миграциям на web сервере(docker-compose)</b></summary>
  
Логинемся на сервер:
```
ssh <имя>@<ip_адрес>
```
Смотрим образы и выбираем ID образа с названием вашей ветки:
```
sudo docker ps
```
Выбираем образ:
```
 sudo docker exec -it <ID-образа> bash
```
Делаем миграции, создаем пользователя и подключаем статику:
```
python manage.py migrate
python manage.py createsuperuser
python manage.py collectstatic --no-input
```
</details>

### :fire: Мой статус :
[![GitHub Streak](http://github-readme-streak-stats.herokuapp.com?user=grwo1&theme=dark&background=000000)](https://git.io/streak-stats)
