## Задание лабиринт
Нужно с помощью рекурсивной функции узнать сможет ли Нора выйти из лабиринта(True) или нет(False). На вход подаётся список/массив.
``` Py
# i,j - координаты текущего нахождения; maze - сам лабиринт, чтобы понимать где стена, а где свободный проход;
# var_exit - клетки по краям лабиринта, если ; l - переменная флаг; way - переменная, в которой хранится путь; t - файл output
def is_exit(i: int, j:int, maze: list, maze_exit: list, l: int,way: list,t) -> str:
    if [i,j] in maze_exit:
        t.write("True")
        return True
    else:
        if maze[i][j]=='N' and l==0:
            l=1
        elif maze[i][j]=='N' and l==1:
            return False
        elif maze[i][j]=='#':
            return False
        elif [i,j] in way:
            return False
        way.append([i,j])
        if  not (is_exit(i-1,j,maze,maze_exit,l, way, t) or is_exit(i,j+1,maze,maze_exit,l, way, t) \
            or is_exit(i+1,j,maze,maze_exit,l, way, t) or is_exit(i,j-1,maze,maze_exit,l, way, t)):
            way.remove([i,j])
 
def main():  
    
    f = open("mazeinput.txt","r")
    t = open("mazeoutput.txt","w+")

    #создаю бесконечный цикл while, чтобы 
    maze=[]
    while True:
        line = f.readline()
        line=line[9:17]
        if not line:
            break
        else:
            maze.append(line)

    # делаем двумерный список и проверем правильность входных данных (одна ли Нора)
    k=0
    for i in range (len(maze)):
        if maze[i].find('N') != -1:
            nora=[i,maze[i].find('N')]
            k+=1
        maze[i]=[c for c in (maze[i])]
    
    # найдём все возможные выходы из лабиринта
    var_exit = []
    for i in range (len(maze)):
        for j in range (len(maze[i])):
            if i==0 or i==(len(maze)-1):
                var_exit.append([i,j])
            if j==0 or j==7:
                var_exit.append([i,j])

    # Проверим есть ли вообще выход из лабиринта, и сохраняем выходы в переменную maze_exit
    del0=0
    maze_exit=[]
    for j in range (len(var_exit)):
        if maze[var_exit[j][0]][var_exit[j][1]] == " ":
            del0=1
            maze_exit = [[var_exit[j][0],var_exit[j][1]]]


    l=0
    way=[]
    # анализируем данные и выводим нужный результат        
    if k!=1:
        t.write("Неверные входные данные(Нора)")
    elif del0==0:
        t.write("Выхода из лабиринта не существует")
    elif k==1 and del0==1:
        is_exit(nora[0],nora[1],maze,maze_exit,l, way,t)
        if t.tell()==0:
            t.write("False")

  
    t.close()
    f.close()
                

if __name__=="__main__":
    main()
```
# Мои результаты
Input:
maze = ["########",
        "# # ####",
        "# #N#   ",
        "# # # ##",
        "# # # ##",
        "#      #",
        "########"]
Output: True