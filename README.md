# Отчет №5
## Сушилов Вячеслав
### группа №20121


## Листинг программы:

```python
res =str(input("Enter: "))
l=[]
def main():
    flag = True
    count01, count02, count03 = 0, 0, 0
    write = ""
    for i in range(len(res)):

        if res[i] == "(":
            if res[i+1] == ")":
                count01+=1
                write+=res[i]
                continue
            elif res[i+1] in "([{":
                count01+=1
                write+=res[i]
                continue
            elif res[i+1] in "]}":
                flag=False
                write=""
                count01, count02, count03 = 0, 0, 0
            else:
                write+=res[i]
                flag=False


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
            else:
                flag=False

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
            else:
                flag=False

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
