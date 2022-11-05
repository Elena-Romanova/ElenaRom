## Задание 1
На вход поступает целое число, вернуть true, если число является целым палиндромом. Целое число является палиндромом, если оно читается так же, как в прямом, так и в обратном порядке. 
``` Py
def main(): 
  stroka = input() 
  if stroka == stroka [::-1]: 
    print ("True") 
  else: 
    print ("False") 
if __name__=="__main__": 
 main()
```
### Мой результат выполнения программы
``` Py
Input: 121
Output: True
Input: 123
Output: False
```

## Задание 2
На вход подается 8-битное целое число со знаком(проверить нужно), на выходе вы должны вернуть перевернутое значение. Если значение выходит за пределы диапазона 8-битных целых чисел со знаком, тогда возвращаем сообщение ("no solution").
p.s. Диапазон(-2^7, 2^7 - 1). В седьмой степени
``` Py
def main():
  chislo =float(input())
  if -2**7<=chislo<=+2**7:
    i=chislo
    rez=0
    while i>0:
      a = i % 10  # находим остаток - последнюю цифру  
      i = i // 10   # делим нацело - удаляем последнюю цифру 
      rez = rez * 10    # увеличиваем разрядность второго числа
      rez = rez + a # добавляем очередную цифру
  
    print(rez)
  else:
    print ("no solution")
if __name__=="__main__":
  main()
```
### Мой результат выпонения программы
```
Input: 12
Output: 21
Input: 123
Output: "no solution"
Input: -150
Output: -51
```

## Задание 3
``` Py
def main(s, k):
    if k == 0:
        return
    if k == 1:
        print(s, end='')
        return
    for i in range(0, len(s), (k - 1) * 2):
        print(s[i], end='')
    for j in range(1, k - 1):
        down = True
        i = j
        while i < len(s):
            print(s[i], end='')
            if down:
                i += (k - j - 1) * 2
            else:
                i += (k - 1) * 2 - (k - j - 1) * 2
            down = not down
    for i in range(k - 1, len(s), (k - 1) * 2):
        print(s[i], end='')

if __name__ == '__main__':
    k = 4
    s = 'перфекционист'
    main(s, k)
```
### Мой результат выпонения программы
```
Input: перфекционист, 4 
output: пцтекисреоифн
```
