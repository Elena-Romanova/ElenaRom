## Задание 1
Функция получает два списка. В каждом списке не должно быть дубликатов.
Функция возвращает:
1) Количество элементов, присутствующих в обоих списках
2) Количество элементов, присутствующих только в одном списке
3) Количество оставшихся элементов в list1 после извлечения элементов из list2
4) Количество оставшихся элементов в list2 после извлечения элементов из list1
``` Py
def funcName(list1, list2):
    ans1 = list1 & list2
    ans2 = list1 ^ list2
    ans3 = list1 - list2
    ans4 = list2 - list1
    
    return [len(ans1), len(ans2), len(ans3), len(ans4)]


if __name__ == "__main__":
    list1 = input().split()
    list2 = input().split()
    list1 = set(list1)
    list2 = set(list2)

    print(funcName(list1, list2))
    funcName(list1, list2)
```
### Мой результат выполнения программы
``` Py
Input: 
list1 = [0, 33, 37, 6, 10, 44, 13, 47, 16, 18, 22, 25]
list2 = [1, 38, 48, 8, 41, 7, 12, 47, 16, 40, 20, 23, 25]
Output: [3, 19, 9, 10]
```

## Задание 2
Функция получает список элементов. Любой элемент может встречаться более одного раза.
Вернуть количество подмножеств, не содержащих повторяющихся элементов, не включая пустое множество. И сами подмножества.

``` Py
def main():
    from itertools import permutations
    def delete(l):
        n = []
        for i in l:
            if i not in n:
                n.append(i)
        return n, len(n)
    lst = [input() for i in range(int(input('кол-во элементов')))]
    ans = []
    for i in range(1, len(lst) + 1):
        for elem in permutations(lst, i):
            p = set(elem)
            ans.append(p)
    print(*(delete(ans)))
if __name__ == '__main__':
    main()
```
### Мой результат выпонения программы
```
Input: 
4
list = [1, 2, 3, 4]
Output: 
[{'1'}, {'2'}, {'3'}, {'4'}, {'1', '2'}, {'1', '3'}, {'4', '1'}, {'2', '3'}, {'4', '2'}, {'4', '3'}, {'1', '2', '3'}, {'4', '1', '2'}, {'4', '1', '3'}, {'4', '2', '3'}, {'4', '1', '2', '3'}] 15
```

## Задание 3
Ваша задача создать функцию, которую будет находить и возвращать количество данных комбинаций. Данная функция принимает два целочисленных аргументы: Candies (количество конфет) и Packages(количество пакетов) .  Если Packeges>Candies, то вернуть “No solution”

``` Py
import math
def func(C, P):

    s=0
    if P > C:
        print('No solution')
    else:
        rez= (1/ (math.factorial(P))) 
        for i in range(P+1):
            k=(math.factorial(P))/(math.factorial(P-i)*(math.factorial(i)))
            j=(-1)** (P + i)
            s +=  j * k * (i**C)
        rez = rez * s

    print(rez)
   

if __name__=="__main__":
    c= int(input())
    p= int(input())
    func(c,p)
```
### Мой результат выпонения программы
```
Input: 4, 3
Output: 6
 Input: 3, 2
Output: 3
Input: 4, 7
Output: “No solution”
Input: 6,6
Output: 1
Input: 15,9
Output: 67128490

```