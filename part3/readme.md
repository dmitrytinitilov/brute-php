# Глава III - Функции

Представим, что наш код начинает расти. Допустим нам приходится выводить в различных ситуациях красный квадрат, и это полностью согласуется с тех. заданием. Красный квадрат крайне востребованная часть Вашего проекта, поэтому Вы используете его в 168-ми местах в коде.

И вот однажды заказчик просит поменять цвет квадрата с красного на синий - "ведь это такая мелочь". Вам нужно менять код в 168 местах, для этого их все нужно найти. Вы используете автозамену, но меняете что-то лишнее, что-то пропускаете - в результате Вам нужно тестировать 168 мест в коде и еще больше ситуаций, в которых он используется. Стоимость проекта растет колоссально - и это всего лишь изменение цвета блока с красного на синий.

Функции позволяют избежать таких мрачных сценариев. Давайте познакомимся с ними ближе.