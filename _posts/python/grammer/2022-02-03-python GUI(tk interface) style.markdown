---
layout: post
title:  "python GUI(tk interface)스타일 변경"
date:   2022-02-06 15:08:00 +0900
categories: 
  - python
  - grammer
mNumber: 4
---

* toc
{:toc .large-only}

### {{page.mNumber}}.1 폰트 변경
widget의 font=(<<font>>,<<size>>,<<characteristic>>)
으로 지정해준다.

```python
import tkinter
window=tkinter.Tk()

button=tkinter.Button(window,text='Hello',font=('Verdana',14,'bold italic'))
button.pack()

window.mainloop()
```
<img src='/assets/img/python/grammer/python GUI(tk interface) style01.font.PNG'>

### {{page.mNumber}}.2 색 변경
widget의 bg(background),fg(foreground) 로 색을 지정해준다.
으로 지정해준다. 
색의 표기
-16진법을 이용 : '#RGB'꼴로 '#XXXXXX'로 표현
-색깔명을 이용 : 'white','blue','green','cyan'등으로 표현

```python
import tkinter
window=tkinter.Tk()

button=tkinter.Button(window,text='Hello',bg='#AABBCC',fg='white')
button.pack()

window.mainloop()
```
<img src='/assets/img/python/grammer/python GUI(tk interface) style02.color.PNG'>

### {{page.mNumber}}.3 배치
widget의 위치 선택은 widget을 생성할 때가 아닌 '붙일 때' 결정하므로 pack(side='left') 와 같이 적용해준다.
pack으로 결정할 수 있는 위치조절
-left
-right
-bottom
-top
뿐인데 더 세밀하게 배치를 원하면 pack() 이 아닌 grid()를 사용하여 window를 좌표처럼 취급하여 widget을 원하는 위치에 붙인다.

```python
import tkinter

window = tkinter.Tk()

frame=tkinter.Frame(window,borderwidth=3,relief=tkinter.GROOVE,bg='yellow')
frame.pack(side='right')

label=tkinter.Label(frame, text='Name', font=(14),bg='#0000AA',fg='white')
label.pack(side='left')

button=tkinter.Button(frame, text='button',bg='#AA00BB')
button.pack(side='left')

window.mainloop()
```

<img src='/assets/img/python/grammer/python GUI(tk interface) style03.side.PNG'>

### {{page.mNumber}}.3.1 grid 이용하기

|매개변수|설명|
|---|---|
|row|widget을 삽입할 행 수, 시작 값 0|
|column|widget을 삽입할 열 수 ,시작 값 0|
|rowspan|widget이 차지할 행 수, 기본값 1|
|columnspanh|widget이 차지할 열 수, 기본값 1|

```python
import tkinter

window = tkinter.Tk()

frame=tkinter.Frame(window, bg='black')
frame.grid(row=1,column=1)

label=tkinter.Label(frame, text='r1c3', font=(14),bg='#0000AA',fg='white')
label.grid(row=1,column=3)

label=tkinter.Label(frame, text='r2c2', font=(14),bg='#0044CC',fg='white')
label.grid(row=2,column=2)

label=tkinter.Label(frame, text='r0c0', font=(14),bg='#0088CC',fg='white')
label.grid(row=0,column=0)

label=tkinter.Label(frame, text='rowspan=3', font=(14),bg='#00AACC',fg='black')
label.grid(rowspan=3)

label=tkinter.Label(frame, text='columnspan=5', font=(14),bg='#00CCCC',fg='black')
label.grid(rowspan=3,columnspan=5)

window.mainloop()
```

<img src='/assets/img/python/grammer/python GUI(tk interface) style04.grid.PNG'>