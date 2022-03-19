---
layout: post
title:  "python GUI(tk interface)기타 위젯"
date:   2022-02-06 17:08:00 +0900
categories: 
  - python
  - grammer
mNumber: 5
---

* toc
{:toc .large-only}

#### {{page.mNumber}}.1 Text
> Entry와 달리 여러줄을 입력받을 수 있음. 또한 이미지,태그, 특정 줄 선택 등도 가능

```python
import tkinter

def addX(text):
    text.insert(tkinter.INSERT,'X')

window=tkinter.Tk()

frame=tkinter.Frame(window)
frame.pack()

text=tkinter.Text(frame,height=3, width=10)
text.pack()

button=tkinter.Button(frame,text='Add',command=lambda:addX(text))
button.pack()

window.mainloop()
```

<img src='/assets/img/python/grammer/python GUI(tk interface)widget01.text.PNG'>

#### {{page.mNumber}}.2 Checkbutton
> Entry와 달리 여러줄을 입력받을 수 있음. 또한 이미지,태그, 특정 줄 선택 등도 가능

```python
import tkinter

def changeColor(widget,r,g,b):
    color='#'
    for var in r,g,b: # r,g,b 의 순서가 강제되는 효과가 있다. 
        color += 'FF' if var.get() else '00' # c의 삼항연산과 같은 효과  x ? a : b
    widget['bg']=color #widget.config(bg=color)

window=tkinter.Tk()

frame=tkinter.Frame(window)
frame.pack()


red=tkinter.IntVar()
green=tkinter.IntVar()
blue=tkinter.IntVar()

label=tkinter.Label(frame,height=13,width=20, bg='black')
label.pack()

for (name, var) in ('R',red),('G',green),('B',blue) :
    checkbutton=tkinter.Checkbutton(frame,text=name,variable=var,
    command=lambda : changeColor(label,red,green,blue)) 
    #checkbutton 은 variable의 값을 0 또는 1로만 바꿔준다.
    checkbutton.pack(side='left')

window.mainloop()
```

<img src='/assets/img/python/grammer/python GUI(tk interface)widget02.Checkbutton.PNG'>

#### {{page.mNumber}}.3 Menu

```python
import tkinter
import tkinter.filedialog as dialog

def save(root, text) :
    data=text.get('0.0',tkinter.END)
    filename= dialog.asksaveasfilename(parent=root,filetypes=[('Text','*.txt')], title='Save as...')

    with open(filename,'w') as file:
        file.write(data)

def quit(root):
    root.destroy()


window=tkinter.Tk()

text=tkinter.Text(window)
text.pack()

menubar=tkinter.Menu(window) #1

filemenu=tkinter.Menu(menubar) #2
filemenu.add_command(label='Save',command=lambda : save(window,text))
filemenu.add_command(label='Quit',command=lambda : quit(window))
menubar.add_cascade(label='File',menu=filemenu)

settingmenu=tkinter.Menu(menubar) 
settingmenu.add_command(label='style')
menubar.add_cascade(label='setting',menu=settingmenu)

fontmenu=tkinter.Menu(settingmenu) #3
fontmenu.add_command(label='size')
fontmenu.add_command(label='style')
settingmenu.add_cascade(label='font',menu=fontmenu)

window.config(menu=menubar) #1
window.mainloop()
```

<img src='/assets/img/python/grammer/python GUI(tk interface)widget03.Menu.PNG'>

>
```python
menu.add_command(label='command name',command=function)
parentMenu.add_cascade(label='childMenu name',menu=childMenu)
```
처럼 menu에 command 또는 자식 menu를 붙일 수 있다.
<br/> 자식 menu 는 add_cascade를,
<br/> leaf가 될 command는 add_command
<br/> 를 이용한다.

__1.window에 붙일 menubar 만들기__

```python
import tkinter.filedialog as dialog

menubar=tkinter.Menu(window)
...
window.config(menu=menubar)
```

__2.menubar 에 자식 menu인 filemenu를 붙이고 filemenu 안에 leaf 역할을 할 command 추가하기__
<br/>즉 tree의 관점으로
<br/>root=menubar
<br/>child=menu
<br/>leaf=command
<br/>로 볼 수 있다.

```python
filemenu=tkinter.Menu(menubar)
filemenu.add_command(label='Save',command=lambda : save(window,text))
filemenu.add_command(label='Quit',command=lambda : quit(window))
menubar.add_cascade(label='File',menu=filemenu)
```

__3.child menu 안에 child menu 추가하기__
```python
fontmenu=tkinter.Menu(settingmenu)
fontmenu.add_command(label='size')
fontmenu.add_command(label='style')
settingmenu.add_cascade(label='font',menu=fontmenu)
```


