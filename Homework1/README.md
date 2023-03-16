# HSE_HomeWorkAssembler1
🏫 Домашнее задание №1 по курсу "Архитектуры вычислительных систем", БПИ216 Багаев Марат

# Задание на 4 балла
Для начала я написал решение задачи на языке C. Код находится в файле [code.c](code.c). Далее я перевел его в ассемблер([code.s](code.s)) и оставил там необходимые комментарии(по работе с переменными в ассемблере). С помощью команды ```gcc -masm=intel -fno-asynchronous-unwind-tables -fno-jump-tables -fno-stack-protector -fno-exceptions code.c -S -o code_nice.s``` я получил ассемблерный код без макросов([code_nice.s](code_nice.s)). После я скомпилировал обе программы в исполняемые файлы: [скомпилированный C](code_c.exe), [скомпилированный ассемблер](code_nice_s.exe). С помощью питона я написал код, который тестирует обе программы([script.py](script.py)). Тестирование ошибок не выявило.

# Задание на 5 баллов
Я добавил в ассемблерный код функцию, которая по длине и адресу массива выводит все его элементы([code_with_func.s](code_with_func.s)). Прокомментировал передачу параметров в функцию. Локальные переменные я использовал и раньше. 

# Задание на 6 баллов
Замена переменных со стека на регистры:
- i = -4[rbp] = r15d
- удалил argc и argv так как они не используются
- n1 = -12[rbp] = r14d
- n2 = -8[rbp] = r13d
Тестирование ошибок не выявило. С помощью питона я замерил скорость всех программ и получил такой результат:

1. Среднее время выполнения [code_nice.s](code_nice.s):                            0.00248091983795166
2. Среднее время выполнения [code_without_variables.s](code_without_variables.s):  0.0022792267799377442
3. Среднее время выполнения [code.c](code.c):                                      0.0022612977027893066
4. Среднее время выполнения [code_with_func.s](code_with_func.s):                  0.0023132476806640625

По идее код без переменных должен работать быстрее всех. Возможно такие цифры получаются из-за того, что я замеряю скорость с помощью питона(считаю время работы os.system("./программа.exe < tests/test.in > tests/test.out")), а он может работать нестабильно. 

# Задание на 7 баллов
Я отделил функцию write_array в отдельный файл. С помощью команды ```gcc -c *.s``` преобразовал их в файлы ".o". Далее с помощью команды ```gcc -o code_from_2_dot_0.exe *.o``` я собрал их в один испольняемый файл. Результат представлен в папке [2_dot_o](2_dot_o)