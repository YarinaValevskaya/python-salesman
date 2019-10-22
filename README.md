Задача коммивояжера на Python методом ветвей и границ(алгоритм Литтла).
Задача коммивояжера — одна из самых известных задач комбинаторной оптимизации, заключающаяся в поиске самого выгодного маршрута, проходящего через указанные города хотя бы по одному разу с последующим возвратом в исходный город.

В основе метода ветвей и границ лежит идея последовательного разбиения множества допустимых решений на подмножества. На каждом шаге метода элементы разбиения подвергаются проверке для выяснения, содержит данное подмножество оптимальное решение или нет. Проверка осуществляется посредством вычисления оценки снизу для целевой функции на данном подмножестве. Если оценка снизу не меньше рекорда — наилучшего из найденных решений, то подмножество может быть отброшено. Проверяемое подмножество может быть отброшено еще и в том случае, когда в нем удается найти наилучшее решение. Если значение целевой функции на найденном решении меньше рекорда, то происходит смена рекорда. По окончанию работы алгоритма рекорд является результатом его работы. Если удается отбросить все элементы разбиения, то рекорд — оптимальное решение задачи. В противном случае, из неотброшенных подмножеств выбирается наиболее перспективное (например, с наименьшим значением нижней оценки), и оно подвергается разбиению. Новые подмножества вновь подвергаются проверке и т.д.

Для решения задачи коммивояжера методом ветвей и границ необходимо выполнить следующую последовательность действий:
1 - Построение матрицы с исходными данными.
2 - Нахождение минимума по строкам.
3 - Редукция строк.
4 - Нахождение минимума по столбцам.
5 - Редукция столбцов.
6 - Вычисление оценок нулевых клеток.
7 - Редукция матрицы.
8 - Если полный путь еще не найден, переходим к пункту 2, если найден к пункту 9.
9 - Вычисление итоговой длины пути и построение маршрута.

Для тестов можно использовать следующее:
Test1
4
0 10 1 1
10 0 1 5
1 1 0 10
1 5 10 0

1->4 4->2 2->3 3->1
8

Test2
4
0 5 11 9
10 0 8 7
7 14 0 8
12 6 15 0

1->4 4->2 2->3 3->1
30

Test3
3
0 5 10
5 0 7
10 7 0

1->2 2->3 3->1
22

Test4
4
0 10 1 7
10 0 6 1
1 6 0 10
7 1 10 0

1->3 3->2 2->4 4->1
15

Test5
4
0 1 1 7
1 0 7 1
1 7 0 1
7 1 1 0

2->4 4->3 3->1 1->2
4

Test6
4
0 1 1 7
1 0 20 1
1 20 0 1
7 1 1 0

1->2 2->4 4->3 3->1
4

Test7
4
0 1 6 3
1 0 1 9
6 1 0 1
3 9 1 0

1->2 2->3 3->4 4->1
6

Test8
6
0 5 7 6 8 3
1 0 8 4 6 2
3 9 0 6 5 3
7 8 4 0 4 2
2 7 5 6 0 6
5 2 6 4 5 0

1->6 6->2 2->4 4->3 3->5 5->1
20
