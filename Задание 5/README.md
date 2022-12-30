## Задание 1
С клавиатуры поступает строка. Необходимо вывести самую длинную подстроку без повторных символов.  
``` Py
def main():
    def largest_substring(s):
        b = 0
        for i in range(len(s)):
            curr = ""
            stroka = ""
            for j in range(i, len(s)):
                if s[j] not in curr:
                    curr += s[j]
                    stroka += s[j]
                else:
                    if len(stroka)>b:
                        b = len(stroka)
                        rez = stroka
                    break
        return rez
    s=input()
    print(largest_substring(s))
if  __name__=="__main__":
    main()
```
### Мой результат выполнения программы
``` Py
Input: “qweasdfdqw”
Output: “qweasd”
Input: “aaaaaaa”
Output: “a”
Input: “prrker”
Output: “rke”

```

## Задание 2
С клавиатуры поступает строка. Необходимо вывести строку, где порядок слов в противоположном направлении. Первое слово с заглавной буквы, остальные с маленькой. МЕЖДУ словами только ОДИН пробел.  
``` Py
def main():
    
    s=input()
    s=s.strip()
    k=s.split()
    rez=k[::-1]
    rez=" ".join(rez)
    print(rez.capitalize())
    
    
if  __name__=="__main__":
    main()
```
### Мой результат выпонения программы
```
Input: “пРивет мИР”
Output: “Мир привет”
Input: “  it       was     cool     ”
Output: “Cool was it”
Input: “good”
Output: “Good”

```

## Задание 3
С клавиатуры поступает строка, которая имеет только символы: '(', ')', '{', '}', '[' и ‘]’. Необходимо проверить правильно ли сформированы скобки. Если ВСЕ скобки сформированы правильно, то вывести True, если нет, то вывести самую длинную правильно сформированную подстроку скобок, если такой подстроки нету, то вывести False. (Сначала лучше сделать True и False, а потом работать с подстроками).

``` Py
def main():
    def check(s):
        brackets_open = ('(', '[', '{')
        brackets_closed = (')', ']', '}')
        stack = []
        for i in s:
            if i in brackets_open:
                stack.append(i)
            if i in brackets_closed:    
                if len(stack) == 0:
                    return False
                else:
                    index = brackets_closed.index(i)
                    open_bracket = brackets_open[index]
                    if stack[-1] == open_bracket:
                        stack = stack[:-1]  
                    else: 
                        return False  
        return True
        
    def check_false(s):
        stack = []
        is_current_correct = True

        maxi = []
        promeg = []

        for bracket in s:
            if bracket in brackets_open:
                stack.append(bracket)
                is_current_correct = True

            if bracket in brackets_closed:
                if len(stack) == 0:
                    is_current_correct = False
                    continue

                previous_bracket = stack.pop()
                if bracket == '}' and previous_bracket != '{':
                    is_current_correct = False
                if bracket == ']' and previous_bracket != '[':
                    is_current_correct = False
                if bracket == ')' and previous_bracket != '(':
                    is_current_correct = False


            if is_current_correct:
                promeg.append(bracket)
                if len(promeg) >= len(maxi):
                    maxi = promeg
            else:
                if len(promeg) >= len(maxi):
                    maxi = promeg
                promeg = []
        
        return "".join(maxi[:-1])
    
    
    
    
    brackets_open = '{[('
    brackets_closed = ']})'
    s=input()
    if check(s) == False:
        print (check(s))
        print(check_false(s))
    else:
        print (check(s))
     

if  __name__=="__main__":
    main()
```
### Мой результат выпонения программы
```
Input: "()[]{}"
Output: True
Input: "(]"
Output: False
Input: ")()())"
Output: "()()“
Input: “{[()]{[()]}}”
Output: True
Input: “{[(]){[()]}}”
Output: “ {[()]}”

```