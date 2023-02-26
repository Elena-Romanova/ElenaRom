## Задание 1
Вы хотите ограбить банки вдоль улицы, которые идут подряд. В каждом банке есть сейф, в котором лежим определенная сумма денег ( в миллионах рублей). Так же в каждом банке есть система защиты, которая сработает если были ограблены два ближайших банка. 
На вход поступает количество банков на улице. Далее пользователь вводит (по мере их расположения): название банка и сумма денег в сейфе. 
Вам необходимо вернуть максимальную сумму денег,  которую вы можете получить (так чтобы не сработала сигнализация), название банков и их порядковые номера на улице.
``` Py
n=int(input())
name_bank=list(input("Enter the names of banks\n").split(','))
money=list(map(int,input().split(',')))

if ((money[0]+money[2])>money[1]):
    money[1]==0
    for i in range (1,n-1):
        if money[i]>(money[i+1]+money[i-1]):
            money[i-1]=0
            money[i+1]=0
        else:
            money[i]=0
else:
    money[0]=0
    money[2]=0
    for i in range(3,n-1):
        if money[i]>(money[i+1]+money[i-1]):
            money[i-1]=0
            money[i+1]=0

a=[]
print(sum(money))
for i in range(n):
    if money[i]!=0:
        a.append(tuple([name_bank[i],i,money[i]]))
print(a)
```
### Мой результат выполнения программы
``` Py

Input: 
3
1,2,3
11,12,53
Output: 64
[('1', 0, 11), ('3', 2, 53)]
```

## Задание 2
Поворот матрицы по часовой стрелке.

``` Py
def main():
    rows, cols = int(input('кол-во строк')), int(input('кол-во столбцов'))
    matrix = [[int(input()) for _ in range(cols)] for _ in range(rows)]
    

    for i in range(len(matrix)):
        for j in range(i,len(matrix)):
            matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
    for i in range(len(matrix)):
            matrix[i].reverse()
    for k in range(len(matrix)):
        print(matrix[k])
    print()

if __name__ == '__main__':
    main()
```
### Мой результат выпонения программы
```
Input: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 
Output: 
[13, 9, 5, 1]
[14, 10, 6, 2]
[15, 11, 7, 3]
[16, 12, 8, 4]
```

## Задание 3
Вернуть все элементы матрицы в спиральном порядке.
``` Py
def main():
    def spiral(matrix):
        ans = []
        if len(matrix) == 0:
            return ans
        left, right, top, bottom = 0, len(matrix[0]) - 1, 0, len(matrix) - 1
        while (top <= bottom and left <= right):
            for i in range(left,right+1):
                ans.append(matrix[top][i])
            top += 1
            for i in range(top,bottom+1):
                ans.append(matrix[i][right])
            right -= 1
            if (top <= bottom):
                for i in range(right,left-1,-1):
                    ans.append(matrix[bottom][i])
                bottom -= 1
            if (left <= right):
                for i in range(bottom,top-1,-1):
                    ans.append(matrix[i][left])
                left += 1
        return ans
    rows, cols = int(input('кол-во строк')), int(input('кол-во столбцов'))
    matrix = [[int(input()) for _ in range(cols)] for _ in range(rows)]
    print(spiral(matrix))
if __name__ == '__main__':
    main()
```
### Мой результат выпонения программы
```
Input: 1 2 3 8 9 4 7 6 5
output: [1, 2, 3, 4, 5, 6, 7, 8, 9]
```
