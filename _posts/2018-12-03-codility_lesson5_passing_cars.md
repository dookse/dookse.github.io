---
title: "Codility lesson4 : MissingInteger"
date: 2018-11-25 17:28:00 +0900
categories: algorithm codility
comments: true
---

## 1. 문제

0과 1로 구성된 배열이 주어진다.

0은 동쪽, 1은 서쪽으로 가는 차를 나타낸다.

지나가는 차가 몇 쌍이나 되는지 세는 문제로, 

지나가는 차량 수가 1,000,000,000 대를 초과할 경우 -1을 반환해야 한다.

## 2. 풀이

문제 설명을 좀 난해하게 해서 어렵게 느껴질 수 있는데,

사실 간단한 문제다.

몇 쌍인지 세는 문제이기 때문에 동쪽, 또는 서쪽 하나를 기준점으로 잡고

기준점의 차 대수를 세다가 반대쪽 방향이 나타났을 때 합산을 해주면 된다.

{% highlight java %}
    int eastCars = 0, passingCounts = 0;
    
    for (final int car : a) {
        if (car == WEST) {
            passingCounts += eastCars;
            if (countExceedLimit(passingCounts)) {
                return -1;
            }
        } else if (car == EAST) {
            eastCars++;
        }
    }
    return passingCounts;
{% endhighlight %}


## 3. 결과
Correctness : 100%

Performance : 100%

Detected time complexity : O(N)

Task Score : 100 point


## 4. 코드 및 테스트 코드
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/main/codility/lesson/lesson5/PassingCars.java"
       class="btn btn-success" 
       target="_blank">
       MissingInteger Code
    </a>
</div>   

