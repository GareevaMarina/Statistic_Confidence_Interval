Даны данные компании (расположение Лондон), которая занимается арендой велосипедов
Необходимо выявить аномалии в аренде велосипедов и разобраться в причинах

### График аренды велосипедов по дням выдает следующую картину:  
Встречаются как очень резкие скачки числа аренд, так и падения  
Максимальное число аренд за день составляет более 70 000  
Зимой число аренд меньше, чем летом  

![Screenshot_42](https://user-images.githubusercontent.com/104904113/201969684-b268e4e7-b82a-4750-a6b2-db2b436587cc.jpg)

### Проверим, что же могло произойти в дни скачков аренд. Для этого:
Сначала посчитаем скользящее среднее, чтобы сгладить ряд   
Далее – разницу между наблюдаемыми и сглаженными значениями   
Определим верхние и нижние границы 99% доверительного интервала  
Выясним в какие дни данные выходят за границы доверительного интервала

### Итог:
1. 2015-07-09 - дата, когда число аренд наибольшее, среди дней по количеству аренд выше верхней границы. Поиск по сети выдает, что в этот день в Лондоне была забастовка метро.
2. 2016-09-02 - дата, когда число аренд наименьшее среди дней по количеству аренд ниже нижней границы доверительного интервала. Значение 0 - подозрительное. По поиску в сети не было найдено каких-либо аномалий в погоде, проведение каких-либо мероприятий или экстренных ситуаций. Делаем вывод, что это ошибка данных.

### Описание данных
timestamp – дата и время (точность до часа)  
cnt – количество аренд велосипедов за этот час  
t1 – температура, в С  
t2 – температура "ощущается как", в С  
hum – влажность (%)  
wind_speed – скорость ветра, км/ч  

weather_code – погодные условия:  
1 – ясно (SKC)  
2 – преимущественно ясно / встречаются отдельные облака (SCT)  
3 – облачно / значительные облака (BKN)  
4 – пасмурно (OVC)  
7 – небольшой дождь Rain/ light Rain shower/ Light rain  
10 – дождь с грозой  
26 – снегопад  
94 – ледяной туман (да, такое бывает!)  
isholiday – является ли день праздником (1 – праздник, 0 – нет)  
isweekend – является ли день выходным (1 – выходной, 0 – нет)  
season – метеорологический сезон (0 – весна, 1 – лето, 2 – осень, 3 – зима)  
