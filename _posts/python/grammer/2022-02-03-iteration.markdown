---
layout: post
title:  "반복문"
date:   2022-02-03 09:28:00 +0900
categories: 
  - python
  - grammer
mNumber: 1
---
* toc
{:toc .large-only}

#### {{page.mNumber}}.1 리스트 내 항목 처리

```python
for <<variable>> in <<list>> :
    <<code block>>
```
<img src="/assets/img/python/grammer/01.iteration_list.PNG" width="200px" height="30px">
<img src="/assets/img/python/grammer/02.iteration_list2.PNG" width="200px" height="30px">

#### {{page.mNumber}}.2 문자열 내 문자처리

```python
for <<variable>> in <<str>> :
    <<code block>>
```
<img src="/assets/img/python/grammer/03.iteration_string.PNG" width="200px" height="30px">

#### {{page.mNumber}}.3 range로 순회하기
> range(start, stop, step) : 정수 수열 객체를 생성하는 내장함수 
<br/> -start : 시작(이상)
<br/> -stop : 끝(미만)
<br/> -step : 단계 크기
<br/> 많은 프로그래밍 언어에서 이상 ~ 미만의 형태를 취하므로 알아두자
```python
range(stop)
range(start,stop)
range(start,stop,step)
```

##### {{page.mNumber}}.3.1 range(stop)
```python
for item in range(5):
    print(item)
#0 1 2 3 4
```
##### {{page.mNumber}}.3.2 range(start,stop)
```python
for item in range(2,6):
    print(item)
#2 3 4 5
```

##### {{page.mNumber}}.3.3 range(start,stop,step)
> step = 0 : ValueError : range() arg3 must not be zero

> step > 0 : start < stop
<br/>
```python
for item in range(1,10,3):
    print(item)
#1 4 7
for item in range(10,1,3):
    print(item)
#
for item in range(10,10,3):
    print(item)
#
```

> step < 0 : start > stop
<br/>
```python
for item in range(10,1,-3):
    print(item)
#10 7 4
for item in range(1,10,-3):
    print(item)
#
for item in range(10,10,-3):
    print(item)
#
```

#### {{page.mNumber}}.4 인덱스로 리스트 처리
> c,c++ 처럼 인덱스로 배열에 접근하는 방법도 가능하다. 
<br/>즉, 주소값 접근처럼 리스트의 값을 사용하는 방법

```python
arr=[1,1,2,3,5,1,12,3,4]
for idx in range(len(arr)):
    print(idx)
```
```c
int arr[10];
for(int i= 0; i<sizeof(arr)/sizeof(int); i++)
    printf("%d\n",i);
```

|python|c|
|---|---|
|len(arr)|sizeof(arr)/sizeof(int)|
|range(len(arr))|int i=0; i<sizeof(arr)/sizeof(int); i++ |

---

> 항목에 접근하는 for문은 list내의 항목을 수정할 수 없지만
인덱스로 접근하는 경우는 list의 항목을 수정할 수 있다.

```python
for item in list:
    item = item * 4
```
의 경우 item 이라는 변수가 for문에서의 지역변수로 사용되므로 list의 항목에 대한 얕은 복사가 되어 list에 직접접근하여 값이 변경되지 않는다.

```python
for idx in range(len(list)):
    list[idx] = list[idx]*4
```
의 경우 list의 직접접근을 하므로 list의 값 변경이 가능하다.

#### {{page.mNumber}}.5 while 문

```python
while <<loop condition>> :
    <<code block>>
```

#### {{page.mNumber}}.6 루프 제어
> break 와 continue 로 제어할 수 있음
<br/> break와 continue는 감싸고 있는 '반복문'을 탈출하는 분기임
<br/> continue -> if문으로 대체할 수 있는 지 다시한번 확인하기
