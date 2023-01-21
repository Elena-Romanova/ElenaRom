## Задание лабиринт
Нужно с помощью рекурсивной функции узнать сможет ли Нора выйти из лабиринта(True) или нет(False). На вход подаётся список/массив.
``` Py
def is_exit(i: int, j:int, maze: list, var_exit: list, k: int ):
    if [i,j] in var_exit:
        if maze[i][j]=='N':
            k=1
        elif maze[i][j]=='N' and k==1:
            return False
        elif maze[i][j]=='#':
            return False
        return is_exit(i-1,j,maze,var_exit,k) or is_exit(i,j+1,maze,var_exit,k) or is_exit(i+1,j,maze,var_exit,k) or is_exit(i,j-1,maze,var_exit,k)
    else:
        return True

def main():  
    
    f=open("mazeinput.txt","r")

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
    if k>1:
        print("Неверные входные данные(Нора)")
    
    # найдём все возможные выходы из лабиринта
    var_exit = []
    for i in range (len(maze)):
        for j in range (len(maze[i])):
            if i==0 or i==(len(maze)-1):
                var_exit.append([i,j])
            if j==0 or j==7:
                var_exit.append([i,j])

    # Проверим есть ли вообще выход из лабиринта
    del0=0
    for j in range (len(var_exit)):
        if maze[var_exit[j][0]][var_exit[j][1]] == " ":
            del0=1
    if del0==0:
        print("Выхода из лабиринта не существует")

    f = open("mazeoutput.txt","w")
    f.write(f"{is_exit(nora[0],nora[1],maze,var_exit,k=0)}")
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