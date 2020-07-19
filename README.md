# Вычисление весового спектра линейного подпространства

Главный критерий, применение только средства языка Python, без подключения какой-либо библиотеки.

Формулировка

Процитируем первоначальную формулировку задачи:

a) Назовем вектором строку битов (значения 0 или 1) фиксированной длины N: то есть, всего возможно 2^N различных векторов.

b) Введем операцию сложения по модулю 2 векторов (операция xor), которая по двум векторам a и b получает вектор a + b той же длины N.

c) Пусть дано множество A = {ai | i ∈ 1..K} из 0 ≤ K ≤ 2^N векторов. Назовем его порождающим: при помощи сложения ai множества A можно получить 2^K векторов вида ∑i[1..K]=bi * ai, где bi равно либо 0, либо 1.

d) Весом вектора назовем количество единичных (ненулевых) битов в векторе: то есть, вес — это натуральное число от 0 до N.

Требуется для заданных порождающих множества векторов и числа N построить гистограмму (спектр) количества различных векторов по их весу.

Формат входных данных:
Текстовый файл из набора строк одинаковой длины по одному вектору в строке (символы 0 и 1 без разделителей). Для задачи, в качестве входных данных генерировись векторы в колличестве 2^N, тем не менее, в разделе "Дополнительно", изложен способ вывода данных их текстового файла в код в качестве тех же переменных.

Формат выходных данных:
Текстовый файл с парой значений вес/количество разделенных символом табуляции, по одной паре на строку, сортированный по числовому значению веса.

# Инструкция по применению:
Запуск в Google Colab

1. Скачивание с репозиторий !git clone https://github.com/VladicNaAmure/Weight-Spectrum-
2. Установка !pip install spectrum
3. Запуск %run /content/Weight-Spectrum-/spectrum.py
4. Импорт всех методов from spectrum import *
5. Запуск вычисления весового спектра линейного подпространства main('/content/.../filename.txt').
6. Открываем появившийся file.txt, как выходной файл.

# Оценка используемых ресурсов
Attempt | #1 | #2 | #3 | #4 | #5 | #6 | #7 | #8 | #9 | #10 | #11
--- | --- | --- | --- |--- |--- |--- |--- |--- |--- |--- |---
Seconds | 301 | 283 | 290 | 286 | 289 | 285 | 287 | 287 | 272 | 276 | 269

# Ключивые решения:
Для ускорения вычислений, все бинарные числа из входного файла переводятся в десятичную систему счисления. Далее выясняется, длина вектора больше или меньше количества строк. Если длина векторов меньше количества строк, значит мы можем освободить процесс и стандартным способом вычислить суммы биномиальных коэффициентов для n-й степени, где степень определяется количеством строк. Если длина векторов меньше количества строк, тогда принято решение найти базис, произвести операцию сложения (логическое XOR), чтобы получить суммарный вектор из 2 ^ (количество строк) подмножеств, и вычислить суммы биномиальных коэффициентов. Для подсчета веса, искалось количество совпадений с 1, каждого суммарного вектора в двоичной системе счисления. В качестве выходного файла, сопоставлены каждому возможному весу (от 0 до длины векторов) количество подмножеств, вес суммарного вектора. 
