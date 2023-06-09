# Оптимизация памяти и обогащение данных
## Улучшим модель линейной регрессии
Операции с данными зачастую требуют большой объем оперативной памяти. Для сокращения потребления памяти потребуется переопределить тип данных для отдельных серий, привести ряд данных к целым значениям, удалить неиспользуемые серии данных, а так же удалить промежуточные серии данных.
## Постановка задачи
Загрузить данные по энергопотреблению всех зданий в оперативную память и добиться ее минимального расхода
Данные:
•	http://video.ittensive.com/machine-learning/ashrae/building_metadata.csv.gz
•	http://video.ittensive.com/machine-learning/ashrae/weather_train.csv.gz
•	http://video.ittensive.com/machine-learning/ashrae/train.0.csv.gz Соревнование: https://www.kaggle.com/c/ashrae-energy-prediction/
© ITtensive, 2020
___
## Решение:
1) Подключим библиотеки.
2) Выведем размеры вещественных и целых размеров данных.
Для вывода типа данных используем этого сокращенное название, например:
"f2", "f4" - float
"i1", "i2", "i4" - int
3) Потребление памяти.
4) Функция оптимизация памяти.
Без объединения оптимизации исходные данные по энергопотреблению занимают порядка 400 Мб, при построении зависимостей моделей этой объем памяти может увеличиваться на 1-2 порядка. Поэтому нам требуется максимально уменьшить объем памяти, для этого используем функцию оптимизации памяти для наших нужд. В ней проверим исходный тип данных и уменьшим его размер, если диапазон данных это позволяет
5) Приведем последовательно оптимизацию потребления памяти для всех загруженных данных:
- Оптимизация памяти: строения (Потребление памяти меньше на 0.05 Мб (минус 73.9 %))
- Отимизация: погода (Потребление памяти меньше на 6.53 Мб (минус 68.1 %))
- Оптимизация: энергопотребление (Потребление памяти меньше на 195.54 Мб (минус 53.1 %))
6) Объединение данных.
Теперь проведем объединение данных. Удалим те серии данных, которые в дальнейшем нам не понадобятся
Используем только одну метрику – энергопотребление.
7) Исследование диапазона данных.
Для дальнейшей оптимизации по памяти требуется понять какие данные могут быть приведены к целым. В частности, это скорее всего облачность, скорость ветра и количество осадков.
Выведем значений этих серий, чтобы принять окончательное решение
8) Приведение к целым типам.
Теперь можно привести к целым типам как указанные выше указанные серии данных, так и серии с годом постройки, и этажность. Создадим для этого отдельную функцию.
9) Проверка результатов оптимизации.
Было 425.6 MB после оптимизации стало 391.1 MB.

 
