---
layout: post
title:  "GUI(tk interface)"
date:   2022-02-04 11:44:00 +0900
categories: 
  - python
  - gui
mNumber: 3
---

* toc
{:toc .large-only}

### {{page.mNumber}}.1 tkinter module 사용하기(tk interface)
> Tk interface는 GUI library toolkit을 제공하는 open source 이다.
<br/> Toolkit이라 Tk 인가 싶다.
```python
import tkinter
window=tkinter.Tk()
window.mainloop()
```
tkinter module의 Tk() 를 호출하여 GUI root window 인스턴스를 호출한다.
<br/>이 root window 내에서 label, button 등 widget을 붙여(pack) GUI를 구성하게된다.
<br/>root window는 하나뿐이여야하지만 자식 window는 TopLevel 위젯으로 window를 더 생성할 수 있다.
<br/>즉, 배경으로 쓰이는 하나의 커다란 window 안에서 여러가지를 붙여서(pack) GUI 를 꾸미는 것이다.

#### {{page.mNumber}}.1.1 window에 widget 붙이기
>
```python
import tkinter
window=tkinter.Tk()
label = tkinter.Label(window,text='This is test!')
label.pack()
window.mainloop()
```
다양한 widget이 있는데 원리는 동일하다
<br/> widget(붙일 곳, widget 내용)
<br/> __widget.pack()__ 으로 window에 붙이기
<img src='/assets/img/python/grammer/python GUI(tk interface)01.label.PNG'/>

widget 종류

|widget|기능|
|---|---|
|Button| 클릭가능한 버튼|
|Canvas| 이미지를 그리거나 표시가능|
|Entry|사용자가 입력할 수 있는 한줄의 텍스트 필드|
|Text|사용자가 입력할 수 있는 여러줄의 텍스트 필드|
|Label|한줄짜리 텍스트 표시|
|TopLevel|자식 window|

등이 있다.

#### {{page.mNumber}}.1.1 widget의 내용(config) 업데이트하기
```python
import tkinter
window=tkinter.Tk()

label=tkinter.Label(window,text='this is test!')
label.pack()
label.config(text='hello!')

window.mainloop()
```
<img src='/assets/img/python/grammer/python GUI(tk interface)02.config update.PNG' />

label은 최신에 할당한 text 값을 window에 보여주고 있다.
하지만 동적으로 label에 표시되는 text 이 변경되려면 어떻게 하면될까?

> tkinter module의 ___V___ ariable class 사용하기
<br/>___V___ ariable class : 다른 widget이나 동작에 의해 widget의 변수값이 바뀌면 그 값을 바로 업데이트 할 수 있도록 해주는 class
Variable class에 값의 할당과 호출은 setter, getter 인 set(),get() 으로 한다.
<br/>또한 widget의 config엔 text가 아닌 __textvariable__ 에 입력하여 가변(variable) 되는 값으로 사용할 수 있도록 한다.

```python
import tkinter
window = tkinter.Tk()

data=tkinter.StringVar()
data.set('This can change at any time.')

label=tkinter.Label(window, textvariable=data)
label.pack()

entry=tkinter.Entry(window, textvariable=data)
entry.pack()

window.mainloop()
```
<img src='/assets/img/python/grammer/python GUI(tk interface)03.entry.PNG'/>

<img src='/assets/img/python/grammer/python GUI(tk interface)03.entry2.PNG'/>

Variable class에는
<br/>StringVar()
<br/>IntVar()
<br/>DobuleVar()
<br/>BooleanVar()
<br/>이 있다.

#### {{page.mNumber}}.1.2 widget grouping 하기
> tkinter의 Frame container를 이용하여 다른 widget을 grouping 할 수 있다.

```python
import tkinter

window=tkinter.Tk()

frame=tkinter.Frame(window,borderwidth=3,relief=tkinter.GROOVE )
frame.pack()

labelWindow=tkinter.Label(window,text='packed in window')
labelWindow.pack()

labelFrame1=tkinter.Label(frame,text='packed in Frame')
labelFrame2=tkinter.Label(frame,text='packed in Frame')
labelFrame1.pack()
labelFrame2.pack()

window.mainloop()
```

<img src='/assets/img/python/grammer/python GUI(tk interface)04.frame.png'>


### {{page.mNumber}}.2 MVC pattern 적용하기
>Model, View, Controller 로 분리하여 유지보수를 용이하게 할 수 있다.
<br/>데이터의 표현과 프로그램의 사용자와의 상호작용을 분리하여 수정의 범위를 구분할 수 있게 하는 것이다.
<br/> -Model : data model 관리하는 부분 ex)StringVar
<br/> -View : 사용자에게 보여지는 부분 ex)Label
<br/> -Controller : 사용자가 프로그램과 직접 상호작용하여 data를 변경하는 부분 ex)Button

```python
import tkinter

#Controller : Button 객체의 callback fun으로 동작
def addCount():
    counter.set(counter.get() + 1)

window=tkinter.Tk()

#Model : int data를 관리, python은 shell 처럼 global variable이여서 addCount()에서 접근 가능함
counter=tkinter.IntVar()
counter.set(0)

#View : counter의 증가를 보여줌
label=tkinter.Label(window,textvariable=counter)
label.pack()

button=tkinter.Button(window,text='count++',command=addCount)
button.pack()

window.mainloop()
```

<img src='/assets/img/python/grammer/python GUI(tk interface)05.MVC.png'>

#### {{page.mNumber}}.2.1 Button의 command에 인수가 필요한 method를 전달해야할 땐?
> controller 역할을 하는 버튼과 같은 함수는 command로 전달되는 함수가 항상 같은 방식으로 호출될 수 있도록 하기위해 인수를 받지 않는다.
하지만 인수를 받아서 동작해야할 함수의 필요성은 필연적인데, 이를 lambda 함수를 이용하는 것이다.
command='함수주소'가 전달된다.

```python
#함수 선언 
lambda <<argv1>>, <<argv2>>, ... : <<code block>>

#함수 동작 시
(lambda <<argv1>>, <<argv2>>, ... :<<code block>>)(<<variable1>>, <<variable2>>, ...)
```
구조를 이해하기 쉽게 생각해보자면
예를들어 
x,y가 인수인 함수 : x+y
라고 표현한 것을
lambda x,y : x+y
로 표현한 것이다.
보통 설명 시 a:b 라고 하면 b는 a의 설명인 것처럼
lambda 함수는 위와 같은 구조로 생각하면 될 것 같다.

1.인수는 없을 수 있다.

<img src='/assets/img/python/grammer/python GUI(tk interface)06.lambda1.PNG'/>

2.함수 선언 code block은 반드시 있어야한다.

<img src='/assets/img/python/grammer/python GUI(tk interface)06.lambda2.PNG'/>

3.함수 선언에는 인수와 동일한 변수가 있어야한다. 함수선언에 인수가 아닌 다른 변수가 있을 경우 define error가 발생한다.

<img src='/assets/img/python/grammer/python GUI(tk interface)06.lambda3.PNG'/>

4.동작을 위해서는 (lambda argv:code block)(variable)괄호를 사용해야하고
단순히 선언하면 함수의 주소값이 반환된다.

<img src='/assets/img/python/grammer/python GUI(tk interface)06.lambda1.PNG'/>

```python
import tkinter

#Controller : Button 객체의 callback fun으로 동작
def generalCount(variable, value):
    variable.set(variable.get() + value)

window=tkinter.Tk()

#Model : int data를 관리, generalCount의 인수로 전달됨
counter=tkinter.IntVar()
counter.set(0)

#View : counter의 증감을 보여줌
label=tkinter.Label(window,textvariable=counter)
label.pack()

#lambda 함수를 사용하여 Button의 command에 인수가 있는 함수를 전달함
button=tkinter.Button(window,text='count++',command=lambda : generalCount(counter,1))
button.pack()

button=tkinter.Button(window,text='count--',command=lambda : generalCount(counter,-1))
button.pack()

window.mainloop()
```

