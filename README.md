# Task 1 - Tuples
# 1.1Программа получает от пользователя слово без пробелов и сохраняет его буквы в кортеже. Например, если пользователь вводит "TheBigBen," кортеж будет содержать ('T', 'h', 'e', 'B', 'i', 'g', 'B', 'e', 'n'). Использовала tuple, для хранения последовательности 
user_input = input("Enter a string without whitespaces: ")
my_tuple = tuple(user_input)
print("Created tuple is:", my_tuple)

# 1.2 точь в точь как 1,1 задание. только наоборот 
my_tuple = ('T', 'h', 'e', 'B', 'i', 'g', 'B', 'e', 'n')
result = ''.join(my_tuple)
print("The string is:", result)

# 1.3 Объединение двух кортежей, беря первую половину из кортежа A и вторую половину из кортежа B.
tuple_A = (1, 2, 3, 4, 5, 6, 7)
tuple_B = (5, 6, 7, 9, 7, 1, 10, 10)
result = tuple_A[:len(tuple_A)//2] + tuple_B[len(tuple_B)//2:]
print(result)

# 1.4  Подсчет, сколько раз каждый элемент встречается в кортеже, и создание другого кортежа, который содержит элементы и их количество. 
def count_occurrences(input_tuple):
    occurrences = {}
    for item in input_tuple:
        if item in occurrences:
            occurrences[item] += 1
        else:
            occurrences[item] = 1
    return tuple((key, value) for key, value in occurrences.items())

input_tuple1 = (55, 6, 777, 54, 6, 76, 7777, 1, 777, 6)
input_tuple2 = ('55', '6', '777', 54, 6, 7777, 9, 777, 6)
input_tuple3 = ((1,2,3), (['A', 'B']), (1,2,3), (['A']))

output1 = count_occurrences(input_tuple1)
output2 = count_occurrences(input_tuple2)
output3 = count_occurrences(input_tuple3)

print("Elements and their occurrences:")
print(output1)
print(output2)
print(output3)

# 1.5 Создание кортежей для хранения определенных объектов данных. Например, если у вас есть (55, 6, 777, 70.0, '7', 'A'), вы получите три кортежа: для чисел (55, 6, 777), для чисел с плавающей запятой (70.0) и для строк ('7', 'A')
data = (55, 6, 777, 70.0, '7', 'A')

result = tuple(item for item in data if isinstance(item, int) or isinstance(item, float))
string_result = tuple(item for item in data if isinstance(item, str))

print(result)
print(string_result)

# Task 2 - Sets and Set Comprehensions
# 2.1  этой задаче программа просит пользователя ввести строку без пробелов. Затем она создает множество, которое содержит уникальные буквы из этой строки. Например, если пользователь вводит "TheBigBen," программа создаст множество, которое будет содержать {'T', 'h', 'e', 'B', 'i', 'g', 'B', 'e', 'n'}. Это множество содержит только уникальные буквы, и оно не учитывает повторяющиеся символы.
user_input = input("Enter a string without whitespaces: ")
my_set = {char for char in user_input}
print("Created set is:", my_set)

# 2.2 Здесь есть два множества: set_A и set_B. Программа находит разницу между этими множествами. Она находит элементы, которые уникальны для каждого из них, и объединяет их в одно множество.
set_A = {1, 2, 3, 4, 5}
set_B = {5, 7, 8, 9, 2, 10}
result = set_A.difference(set_B) | set_B.difference(set_A)
print(result)

# 2.3 Удаление общих элементов

Здесь также есть два множества: set_A и set_B. Программа удаляет из set_A все элементы, которые присутствуют в set_B. Результатом будет множество элементов, которые есть в set_A, но отсутствуют в set_B. Например, если set_A содержит {1, 2, 3, 4, 5}, а set_B содержит {5, 7, 8, 9, 2, 10}, результатом будет {1, 3, 4}. Это элементы, которые есть только в set_A и не пересекаются с set_B.
set_A = {1, 2, 3, 4, 5}
set_B = {5, 7, 8, 9, 2, 10}
result = set_A - (set_A & set_B)
print(result)

# 2.4 Удалить элемент из set_A и добавить его в set_B, если этот элемент также есть в set_C. Если set_A - {1, 2, 3, 4, 7}, set_B - {8, 7, 9, 4, 2, 0, 10}, и set_C - {4, 0, 1}, вы обновите set_C до {4, 1, 0, 2, 7}.
set_A = {1, 2, 3, 4, 7}
set_B = {8, 7, 9, 4, 2, 0, 10}
set_C = {4, 0, 1}
set_C.update(set_A & set_C)
set_A.difference_update(set_A & set_C)
print("Updated set_C =", set_C)

# 2.5 Создать список множеств. Из надмножества A создать множества размером n и сохранить их в списке m раз. Например, из {1,2,3,4,5,6} создать список множеств размером 3: [{1,2,3}, {1,2,4}, {1,5,6}, {3,4,5}, {5,6,2}].
import itertools

A = {1, 2, 3, 4, 5, 6}
n = 3
m = 5

combinations = list(itertools.combinations(A, n))
sets_list = [set(combination) for combination in combinations[:m]]

print(sets_list)

# Task 3 - Grouping Data Сгруппировать данные по производителю автомобилей и вывести таблицу с именем производителя, количеством моделей и списком моделей автомобилей. Например, если у вас есть список автомобилей вида [('BMW', 'X6'), ('Toyota', 'Yaris'), ('Fiat', '500'), ('Fiat', 'Panda'), ('Toyota', 'Camry 30')], вы выведете:
from itertools import groupby

cars_list = [('BMW', 'X6'), ('Toyota', 'Yaris'), ('Fiat', '500'), ('Fiat', 'Panda'), ('Toyota', 'Camry 30')]

cars_list.sort(key=lambda x: x[0])

for key, group in groupby(cars_list, lambda x: x[0]):
    group_list = list(group)
    print(f"{key} {len(group_list)}")
    for car in group_list:
        print(f"- {car[1]}")
