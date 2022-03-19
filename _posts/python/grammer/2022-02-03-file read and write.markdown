---
layout: post
title:  "python 파일 읽기와 쓰기"
date:   2022-02-03 14:51:00 +0900
categories: 
  - python
  - grammer
mNumber: 2
---

* toc
{:toc .large-only}

### {{page.mNumber}}.1 파일 열기
#### {{page.mNumber}}.1.1 파일 열기
> 
```python
file=open(<<file path>>,<<file mode>>)
contents=file.read()
file.close()
```
```python
file=open('test.txt','r')
contents=file.read()
file.close()
```
open(<<file path>>,<<file mode>>)
<br/> : 파일을 열고 파일을 얼마나 읽었는지 추적하는 객체를 생성
<br/> -file path : file 위치, linux 계열 /(slash), windows \(backslash)
<br/> -file mode : r = 읽기(read), w = 쓰기(write), a = 추가(append)
<br/> read()
<br/> : 파일 내용 전체를 하나의 문자열로 읽음
<br/> close()
<br/> : 열린 file 객체와 관련된 모든 자원을 해제함

#### {{page.mNumber}}.1.2 with문
> 코드 오류로 open 된 file에 대해 close()를 수행할 수 없는 경우를 대비하여 어떠한 경우라도 항상 close가 될 수 있도록 해줌
```python
with <<experssion>> as <<variable>> :
    <<code block>>
```
```python
with open('test.txt','r') as file:
    contents=file.read()    
```
open file 객체에는 special method인 __enter__, __exit__ 이 있음
<br/>  -<<expression>> : open file 의 객체를 반환하고 __enter__ method를 호출함
<br/>  -<<variable>> : <<expression>>의 객체가 할당됨
<br/>  -<<code block>> : code 실행 시 정상/오류 상관없이 <<variable>>에 할당된 객체의 __exit__ 을 호출하여 어떠한 경우라도 file을 close하도록 함

#### {{page.mNumber}}.1.3 파일 위치 파악
>
```python
import os
os.getcwd()
os.chdir(<<directory>>)
```
```python
import os
os.getcwd() #'D:\\github\\blog\\cocobo2369.github.io'
os.chdir('../')
os.getcwd() #'D:\\github\\blog'
os.chdir('D:/github')
os.getcwd() #'D:\\github'
```
window os 에서 getcwd 출력 시 backslash로 출력됨 하지만 chdir 로는 linux 계열처럼 /(slash) 를 사용하면 됨
<br/> -getcwd() :__get current working directory__
<br/> -chdir() : __change directory__

### {{page.mNumber}}.2 파일 읽기

#### {{page.mNumber}}.2.1 read()
>
```python
with open('test.txt','r') as file :
    file.read()
with open('test.txt','r') as file :
    file.read(5)
    file.read() #file curser 의 현재위치는 6이므로 6부터 끝까지 읽게됨
```
read() : 파일 내용 전체를 하나의 문자열로 읽음
<br/> <img src="/assets/img/python/grammer/python file read and write01.read.PNG" >
<br/> read(n) : 파일 내용 중 문자열을 정수 n만큼만 읽음
<br/> <img src="/assets/img/python/grammer/python file read and write02.readn.PNG" >

#### {{page.mNumber}}.2.2 readlines()
>
```python
with open('test.txt','r') as file:
    file.readlines()
```
파일의 각 줄을 문자열로 취급하여 리스트로 만듦
newline '\n' 도 그대로 남겨 어떠한 문자열도 제거하지 않음
예제의 마지막 문자열은 '\n'이 없는데 이는 파일에 쓸 때 '\n'을 표시하지 않았기 때문
추 후 파일 관리 시 마지막 문자열에도 '\n'을 추가하여 파일의 모든 문자열들이 '\n'으로 끝나게하면 이를 이용할 수도 있음
<br/><img src="/assets/img/python/grammer/python file read and write03.readlines.PNG" >

#### {{page.mNumber}}.2.3 for line in file
>
```python
with open('test.txt','r') as file:
    for line in file:
        print(line)
```
readlines() 는 file을 newline 마다 문자열을 구분하여 list 객체로 반환하는 반면
file 객체 자체에 반복문으로 접근하여 문자열을 반환할 수 도 있다.
<br/><img src="/assets/img/python/grammer/python file read and write04.forlineinfile.PNG" >

#### {{page.mNumber}}.2.4 readline
>
```python
with open('test.txt','r') as file:
    print('readline string')
    print(file.readline().strip())
    print('other strings')
    for line in file :
        print(line.strip())
```
readline() 은 file의 newline으로 구분되는 한 줄을 문자열로 반환한다.
<br/> readline() 함수를 호출할 때마다 file cursor는 다음 줄 맨 앞으로 이동한다.
<br/> print시 문자열 안에 '\n'이 있을 수 있으므로 '\n'이나 공백등을 제거하고싶을 때 strip() 함수를 이용한다.
<br/><img src="/assets/img/python/grammer/python file read and write05.readline.PNG" >
 <img src="/assets/img/python/grammer/python file read and write06.readlinestrip.PNG" >

#### {{page.mNumber}}.2.5 url 읽기
>
```python
import urllib.request
url='https://robjhyndman.com/tsdldata/ecology1/hopedale.dat'
with urllib.request.urlopen(url) as webdata:
    for line in webdata:
        line=line.strip()
        line=line.decode('utf-8')
        print(line)
```
인터넷 상의 파일을 읽기용으로 open하기 위해 open()함수 대신 urllib.request 모듈의 urlopen() 을 이용한다. 다만 이때 파일의 종류가 사진,음악,텍스트,동영상 등 다양하기 때문에 이를 __bytes__ type 으로 반환하므로 decode 하여 문자열로 변환해야한다.
<br/> hopedale.dat는 utf-8로 encode 되어있으므로 bytes(utf-8) --> 문자열로 변환하고 사용한다.

### {{page.mNumber}}.3 파일 쓰기
> 
```python
file=open(<<file path>>,<<file mode>>)
n=file.write(<<contents>>)
file.close()
```
```python
file=open('test.txt','w')
n=file.write('write things')
file.close()
with open('test.txt','w') as file:
    file.write('hello')
```
open(<<file path>>,<<file mode>>)
<br/> - filemode='w' : 존재하지 않는 file이면 새 file이 생성되고, file이 존재하면 덮어씀.
<br/> - filemode='a' : file을 덮어쓰지 않고 그 뒤에 덧붙임.
<br/> write(<<contents>>)
<br/> : file에 문자를 쓰고, 쓴 문자 개수를 반환함
<br/>   자동으로 '\n'을 덧붙이지 않음, 새 줄로 시작하게하려면 문자열에 수동으로 '\n'을 추가해야함.
<br/> close()
<br/> : 열린 file 객체와 관련된 모든 자원을 해제함
