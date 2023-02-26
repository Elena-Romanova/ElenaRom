## Лабораторная работа №1
Даны количество чисел, сами числа и значение, которое нужно получить с помошью этих чисел. Необходимо вывести последовательность действий.

``` Py
# Рекурсивная функция
def check(chisla: list, schetchik: int, prom_rez: str, treb_znach: int, pervoe_chislo: str):
    # если список чисел пустой, возвращаем результат, если было досигнуто требуемое значение,\
    #  иначе возвращаемся в рекурсии на шаг назад/говорим об отсутствии решения
    if len(chisla)==0:              
        if schetchik==treb_znach:
            return  prom_rez
        else:
            return False

    return (check(chisla[1:], schetchik + chisla[0],prom_rez + '+' + str(chisla[0]),treb_znach,pervoe_chislo) \
            or check(chisla[1:], schetchik - chisla[0],prom_rez + '-' + str(chisla[0]),treb_znach,pervoe_chislo))
             
def main():

    t= open("text.txt", "r+")
    chisla=t.readline().split()

    #производим подготовительную работу, выделяя нужные значение и объявляем используемые в коде переменные
    chisla=[int(x) for x in chisla]
    n=chisla.pop(0)   #выделяем в переменную n количество чисел
    treb_znach=chisla.pop(-1) #сохраняем требуемое значение
    schetchik=0 #для подсчёта получаемой суммы и разности чисел
    prom_rez="" # для сохранения строки действий с числами
    rez = " "

    pervoe_chislo = chisla[0]
    rez = check(chisla[1:], schetchik, prom_rez, treb_znach, pervoe_chislo)
    
    if rez == False:
        t.write('\n No solution')
    else:
        posled = str(pervoe_chislo) + rez + '=' + str(treb_znach)
        t.write('\n'+ (posled))


if __name__=="__main__":
    main()
```
# Мои результаты
Input: 3 2 3 4 3
Output: 2-3+4=3
Input: 4 12 4 8 5 11
Output: 12-4+8-5=11