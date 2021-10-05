# Описание своего языка описаний конечных автоматов

##Язык имеет следующий вид:
	
	*Первая строка, задающая алфавит, начинается с ключевого слова **Alph**, далее идет символ '=', отделенный пробелами, а после него через пробел записаны в '"' символы алфавита, чтоб разрешить наличие '"' и '\' в символах будем экранировать их, то есть перед этими символами писать дополнительный '\' (перед дополнительным ничего ставить не нужно). Пример первой строки: 'Alph = "0" "1" "\""'.
	*Вторая строка имеет вид: 'States = amount', где 'State' ключевое слово, а 'amount' какое-то число. И задает количество всех состояний автомата.
	*Третья строка имеет вид : 'StartState = q', где 'StartState' ключевое слово, а 'q' какое-то число, меньшее 'amount', означающее номер стартовой вершины. Эта строка, как можно догадаться, задает стартовую вершину.
	*В четвертой строке задаются номера терминальных вершин. Она начинается с ключевого слова 'AcceptStates', далее идет отделенное пробелами '=', а далее через пробел номера терминальных состояний. Таким образом эта строка имеет вид: 'AcceptStates = x1 x2 ... xn', где все 'xk' различные неотрицательные целые числа и меньше, чем 'amount'.
	*В последней, пятой строке записаны переходы в нашем графе. Она начинается с ключевого слова 'Transits', далее '=', отделенное пробелами, а затем идет некоторое количество переходов, разделенных пробелами. Структура записи переода в этой строке следующая: в скобках '()' записаны через запятую номер состояния, из которого переходим и номер состояния в которое переходим, после них стоит запятая и через пробел записаны условия, при которых выполняется переход. Условиями являются символы алфавита, то есть последовательности 'char' в '""' записанные по правилам, описанным в первом пункте.
	
##Парсер

	*Запуск производится при помощи команд: 'g++ my\_parser.cpp -o my\_parser' и './my\_parser input.txt'.
	*Синтаксический анализатор распарсит входной файл 'input.txt', создаст внутри структуру 'struct Automata', в которой хранится автомат, а затем выведет в красивом виде этот автомат в выходной файл 'input.txt.out'
	
##Тесты
Примеры корректных и не очень(совсем не) корректных тестов можно увидеть в файле 'input.txt' и аналогичных ему.