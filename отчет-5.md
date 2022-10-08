# Отчет №5
## Сушилов Вячеслав
### группа №20121


## Листинг программы:

```python
def main():
    res =str(input("Enter: "))
    l=[]
    flag = True
    count01, count02, count03 = 0, 0, 0
    write = ""
    for i in range(len(res)): #перебор каждого элемента res

        if res[i] == "(": #если у нас круглая скобка, рассмотрим варианты...
            if res[i+1] == ")":  #далее круглая скобка, продрлжаем
                count01+=1
                write+=res[i]
                continue
            elif res[i+1] in "([{": #далее другая скобка, продолжаем
                count01+=1
                write+=res[i]
                continue
            elif res[i+1] in "]}": #правильность скобок нарушается
                flag=False
                write=""
                count01, count02, count03 = 0, 0, 0


        if res[i] == "[":
            if res[i+1] == "]":
                count02+=1
                continue
            elif res[i+1] in "([{":
                count02+=1
                write+=res[i]
                continue
            elif res[i+1] in ")}":
                flag = False
                write=""
                count01, count02, count03 = 0, 0, 0


        if res[i] == "{":
            if res[i+1] == "}":
                count03+=1
                continue
            elif res[i+1] in "([{":
                count03+=1
                write+=res[i]
                continue
            elif res[i+1] in ")]":
                flag = False
                write=""
                count01, count02, count03 = 0, 0, 0
            else:
                flag=False

        elif res[i] == ")":
            if res[i-1] in "[{":
                write=""
                continue
            if count01>0:
                count01-=1
                write+=res[i]
                l.append(write)
                continue

        elif res[i] == "]":
            if res[i-1] in "({":
                write=""
                continue
            if count02>0:
                count02-=1
                write+=res[i]
                l.append(write)
                continue
            else:
                flag=False

        elif res[i] == "}":
            if res[i-1] in "([":
                write=""
                continue
            if count03>0:
                count03-=1
                write+=res[i]
                l.append(write)
                continue
            else:
                flag=False
    if flag == False and l != []:
        print(max(l, key=len))
    else:
        print(flag)


if __name__ == "__main__":
    main()

```
## Блок схема

## Пояснение
