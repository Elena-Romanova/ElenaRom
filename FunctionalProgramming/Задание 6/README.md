## Задание 1
Задается количество элементов в списке ( >4). Задается целочисленный список длины N. Задается цель. Необходимо найти сумму 4 чисел, которые равны цели или находятся близко к ней и вывести их.   
``` Py
def main():
     from itertools import combinations
     N = int(input()) 
     s = [int(input()) for _ in range(N)]
     С = int(input())
     s_comb = list(combinations(s, 4))
     
     res = s_comb[0]
     min_razn= abs(sum(s_comb[0]) - С)
     for i in s_comb:
         if abs(sum(i) - С) < min_razn:
             res=list(i)
             min_razn= abs(sum(i) - С)

     print(res) 
     print (sum(res))
if __name__ == '__main__':
    main()
```
### Мой результат выполнения программы
``` Py
Input:  
N = 5
[1, 2, 4, -5,-2] 
C = 1
Output:
[1,2,4,-5]
```

## Задание 2
Задается список целых чисел. Вывести список разделенный списками со всеми возможными уникальными перестановками целых чисел из заданного списка.
``` Py
def main():
    from itertools import permutations
    s = input('введите числа через пробел').split()
    s = [int(s[i]) for i in range(len(s))]
    s_len = len(s)
    s = list(permutations(s, s_len))
    s = [list(s[i]) for i in range(len(s))]
    rez = []
    for i in s:
        if i not in rez:
            rez.append(i)
    print(rez)
if __name__ == '__main__':
    main()
```
### Мой результат выпонения программы
```
Input:
[1,2,3]
Output:
[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
Input:
[1,1,2]
Output:
[[1,1,2], [1,2,1], [2,1,1]]
Input:
[0]
Output:
[[0]]
```

## Задание 3
Задается список строк.  Необходимо сгруппировать их в общий список по двум критериям:
1) слова имеют одни и те же буквы
2) слова одинаковой размерности
``` Py
def main():
    s=input().split()
    l = ["".join(sorted(i)) for i in s]
    res = []
    

    while len(s) != 0:
        res += [[s[0]]]
        delete = [0]
        for i in range(1, len(s)):  
            if l[i] == l[0]:
                res[-1] += [s[i]] 
                delete += [i]
        for i in range(len(delete)): 
            del s[delete[i] - i]
            del l[delete[i] - i]
    print(res)


if __name__ == "__main__":
    main()
```
### Мой результат выпонения программы
```
Input:
["qwe", "ewq", "asd", "dsa", "dsas", "qwee", "zxc", "cxz", "xxz", "z", "s", "qweasdzxc", "zzxc"]
Output:
[['qwe', 'ewq'], ['asd', 'dsa'], ['dsas'], ['qwee'], ['zxc', 'cxz'], ['xxz'], ['z'], ['s'], ['qweasdzxc'], ['zzxc']]
Input
["a","a",""]
Output
[['a', 'a'], ['']]
```