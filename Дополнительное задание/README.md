## Дополнительное задание
Найти числа, которые больше или равны тысячи, таким образом, что сумма каждых четырех последовательных цифр не может быть больше определенного заданного значения.
[(1), (2), (3)]

(1) - сумма чисел, которые удовлетворяют вышеприведенному ограничению

(2) - ближайшее число к среднему значению результатов, если их несколько, то выбирается наименьшее число.

(3) - общая сумма всех найденных чисел.

``` Py
def maximumSumD(nMaximum,maximumSum):
    nabor=[]
    s=0
    kol_vo = 0 
    
    for i in range (1000, nMaximum + 1):
        s = str(i)
        suma = int(s[0]) + int(s[1]) + int(s[2]) + int(s[3])
        if suma <= maximumSum:
            nabor.append(i)
        
    kol_vo = len(nabor)
    suma = sum(nabor)
    sr_znach = suma/kol_vo
    bliz_sr_znach = min(nabor, key=lambda x:abs(x-sr_znach)) # lambda это оператор, который позволяет создать функцию без имени, для разового использования
    rez = [kol_vo, bliz_sr_znach, suma]
    return rez

nMaximum = int(input('Введите максимальное значение в диапозоне'))
maximumSum = int(input ("Введите максимальную сумму цифр"))

print (maximumSumD(nMaximum,maximumSum))
```
# Мои результаты

input: maximumSumD(2000, 4)
output: [21, 1120, 23665]

input: maximumSumD(2000, 7)
output: [85, 1200, 99986]

input: maximumSumD(3000, 7)
output: [141, 1600, 220756]
