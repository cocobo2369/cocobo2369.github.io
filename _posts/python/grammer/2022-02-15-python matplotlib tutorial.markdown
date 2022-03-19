---
layout: post
title:  "python matplotlib tutorial"
date:   2022-02-15 21:00:00 +0900
categories: 
  - python
  - grammer
mNumber: 1
---

* toc
{:toc .large-only}

출처 : https://matplotlib.org/stable/tutorials/introductory/usage.html

## Basic Usage



### Figure 의 구성
<img src='/assets/img/python/grammer/matplotlib/PartsAfFigure.PNG'>
<img src='/assets/img/python/grammer/matplotlib/PartsAfFigure01.PNG'>

#### Figure
> 도화지
<br/> Figure 안에는 여러개의 그래프가 추가 될 수 있다.
<br/> 또한 matplotlib에서는 그래프를 Axes 라고 부른다.

```python
fig = plt.figure()  # an empty figure with no Axes
fig, ax = plt.subplots()  # a figure with a single Axes
fig, axs = plt.subplots(2, 2)  # a figure with a 2x2 grid of Axes
```
<img src='/assets/img/python/grammer/matplotlib/PartsAfFigure02.PNG'>

#### Axes
> 그래프

#### Axis
> 축
<br/> 축과 관련한 구성들
<br/> - tick : 눈금
<br/> - label : 축 이름

#### Spine
> Axes 의 외부 프레임, tick이 아닌 axes를 감싸는 부분

<img src='/assets/img/python/grammer/matplotlib/PartsAfFigure03.PNG'>

#### Artist
> Figure 위에 그려지는 모든 요소들을 일컬음

<img src='/assets/img/python/grammer/matplotlib/PartsAfFigure04.PNG'>


### Coding style

<img src='/assets/img/python/grammer/matplotlib/oopvspyplot.PNG'>

#### OO style

```python
import matplotlib as mpl
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 2, 100)  # Sample data.

# Note that even in the OO-style, we use `.pyplot.figure` to create the Figure.
fig, ax = plt.subplots(figsize=(5, 2.7), layout='constrained')

ax.plot(x, x, label='y=x')  
ax.plot(x, x**2, label='y=x^2')  
ax.plot(x, x**3, label='y=x^3')  

ax.set_xlabel('x-label')  
ax.set_ylabel('y-label')  
ax.set_title("plot test") 

ax.legend();

plt.show()
```

#### pyplot style

```python
import matplotlib as mpl
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 2, 100)  # Sample data.

# Note that even in the OO-style, we use `.pyplot.figure` to create the Figure.
plt.figure(figsize=(5, 2.7), layout='constrained')

#layout='constrained' 로 세 Axes가 한 
plt.plot(x, x, label='y=x')  
plt.plot(x, x**2, label='y=x^2')  
plt.plot(x, x**3, label='y=x^3')  

plt.xlabel('x-label')  
plt.ylabel('y-label')  
plt.title("plot test") 

plt.legend();

plt.show()
```

<img src='/assets/img/python/grammer/matplotlib/oopstyle.PNG'>