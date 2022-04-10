---
layout: post
title: review_핵심 c++ 표준 라이브러리, 2판
categories:
 - thinking
---

* toc
{:toc .large-only}

## 추천 독자
- 사전 형식의 책이기 때문에 목표를 잡고 챕터별로 읽는 형식이라고 생각하고 읽으면 다소 지루할 수 있음.  
하지만 필요한 부분에 대해 찾아서 읽으면 단원별로 필수적으로 필요한 부분을 간단한 예제로 잘 설명해줘 바로 써먹을 수 있도록 구성하였음.  

## 총평
총    점 : ★★★★☆
읽기쉬움 : ★★★★☆  
이 해 도 : ★★★★☆  
내용알참 : ★★★☆☆  
 (stl은 너무 방대하다 모든 것을 담을 수 없다. 하지만 필요한 것들 위주로 담겼다.)
 
## 이게 좋더라

### 1.사전식에 충실한 구성 :  
<img src='/assets/img/thinking/contents.jpg' width= '300px' height='500px'>

찾아보기로 원하는 함수를 찾을 수도 있을 것이다.  
하지만 익숙해지기 전까지는 짝 달라붙지 않은 함수명으로 찾을리 만무하다.  
구글링으로도 "c++ 문자열 찾기" 로 std::find 를 찾는 게 순서 아닌가?  
그래서 이 책은 목차 -> 대주제 -> 메서드 찾기에 구성이 너무 잘 되어있다.  
문자열 --> 찾기 는  
11장 스트링-->탐색  
으로 str.find() 에 대한 정보를 찾을 수있다.
사전식 책은 죽 읽어나가는 책이 아니다.
찾고 싶은게 있을 때 그 때 그 때 꺼내서 콕 집어 보는 책이다.
아주 충실하다.

### 2.간단한 예제가 적용하기 가장 좋다 :  
개발하면서 예제가 너무 복잡하면 사용하기 싫다.
이 메서드를 사용했을 때 사용결과가 어떤지를 보고싶은데 주저리주저리 코드가 나열되어 있어도  
원하는 함수를 보고 그 주위 += 3 line 정도만 보는게 다반사일 것이다.  
그런 의도를 알았을까?  
저자는 메서드의 5줄 이내로 메서드들을 사용하고 그 결과를 주석으로 입력해두었다.  
심플하다.  
그래서 적용하기가 쉽다.

### 3.자투리 필기가 눈에 더 띄는 법 :  
<img src='/assets/img/thinking/warningAndnote.jpg' width= '600px' height='400px'>

warning이나 note는 개발하다가 한번 쯤 궁금할만한 내용을 실거나 insight를 줄 수 있는 내용을 채웠다. 어디서 한번 쯤 봤을 법한 내용이 있을 수도 있다. 하지만 정보라는 것은 어디에나 있는 내용이라서 가치가 있는 것이 아니라 독자에게 잘 전달되었을 때 가치가 있는 것이다.  
이런 warning, note는 독자의 집중을 환기하여 좀 더 노련하게 정보를 전달한다.

### 4.그림은 그 페이지의 구성까지도 기억하게 해준다 :  
<img src='/assets/img/thinking/addGoodPracticeImg.jpg' width= '600px' height='400px'>

책을 읽다보면 갑작스레 등장한 그림에 대해 반가운 느낌을 줄 뿐만 아니라  
글보다 훨씬 더 기억하기 쉽다.  
뿐만 아니라 그 페이지 전체의 구성에 대해서도 기억하게 해 그림 주변에 대한 내용까지도 연쇄적으로 기억하게 해준다.  
적재적소에 독자들이 이해하기 쉽게 그림으로 설명한 부분들은 필연 독자의 이해를 훨씬 더 높여줄 뿐 아니라  
어차피 자주 사용할 메서드인데 기억하기도 쉽게 해준다.  
쉽고 기억하기 쉽게 읽히게 하는 책이 좋은 책이다.  

## 이게 아쉽더라

### 1.번역 용어가 변역한 한글 기준 사전순으로 정리가 되어있었으면 찾기가 쉬웠을 것 같음

### 2.개념 설명과 사전의 모호한 경계 :  
 개념 설명은 꽤나 직관적이고 명쾌하다. 하지만 제한된 쪽수 및 최대한 내용을 정제하여 실어서  
 더 자세한 설명에 대해 궁금해지게 하는 경우도 있다.  
 개념서를 옆에 끼고 두면 더 효과가 좋을 거 같은 책이다.