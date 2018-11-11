---
title: "Codility lesson3 : ProgJmp"
date: 2018-10-19 12:21:55 +0900
categories: algorithm codility
comments: true
---

## 1. 문제

개구리가 좌표 x에서 시작해 한번에 d 만큼 점프할 수 있다고 했을 때,

좌표 y까지 몇번 뛰어야 도착할 수 있는지 구하는 문제다.


## 2. 풀이

Time Complexity 관련 문제는 보통 루프를 사용하지 않고 풀 수 있는 방법을 먼저 고민해보게 되는데,

해당 방식을 처음 연습해보기 좋은 문제라고 생각한다.

풀이법은 간단한데, 이동 거리를 구한 다음 (y - x) 점프 거리(d)로 나눈 값을 올림하면 된다.

코드는 아래와 같다.

{% highlight java %}
    double jumpCount = (double) (y - x) / d;
    return (int) ceil(jumpCount);
{% endhighlight %}

가독성을 조금 포기한다면, 아래와 같이 한줄로 코드를 작성 가능하다.
{% highlight java %}
    return (int) ceil((double) (y - x) / d);
{% endhighlight %}

## 3. 결과
Correctness 100%,

Performance 는 시간 복잡도 O(1) 로 감지되어 100%로

Task Score는 100 point가 되었다.


## 4. 코드 및 테스트 코드
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/main/codility/lesson/lesson3/FrogJmp.java"
       class="btn btn-success" 
       target="_blank">
       FrogJmp Code
    </a>
</div>   
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/test/codility/lesson/lesson3/FrogJmp.java"
       class="btn btn-warning" 
       target="_blank">
       FrogJmp Test Code
    </a>
</div>

