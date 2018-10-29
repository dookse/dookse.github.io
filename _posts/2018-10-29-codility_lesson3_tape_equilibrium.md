---
title: "Codility lesson3 : TapeEquilibrium"
date: 2018-10-29 20:35:55 +0900
categories: algorithm codility
---

## 1. 문제

주어진 배열에서 한칸씩 밀려나면서 왼쪽 합 - 오른쪽 합을 했을 때 가작 작은 값을 구하면 된다.

[3, 1, 2, 4, 3] 이라는 배열이 주어졌을 경우

3 − 10 = 7, 4 − 9 = 5, 6 − 7 = 1, 10 − 3 = 7

이므로 답은 1이 된다.


## 2. 풀이

Time Complexity 문제에서 가장 중요한 것은 for문을 몇번 사용하느냐가 아니라

가장 빠른 수행 시간을 가지는 알고리즘을 짜는 것이기 때문에 stream은 거의 사용되지 않는다.

배열의 갯수가 많아지면 많아질수록 stream.sum() 보다 차라리 for문을 세번 수행하는 것이 훨씬 좋은 성능을 보인다.  

간단하게는 왼쪽합 배열, 오른쪽 합 배열을 구한 후 왼쪽 배열에서 오른쪽 배열을 뺀 값 중 최소값을 구하면 되지만,

합계를 구한 뒤 A[N] * 2 만큼 빼는것을 반복하면 왼쪽 합과 오른쪽 합을 구하지 않고도 최소값을 계산할 수 있다. 


{% highlight java %}
    int sum = getSum(a),
        min = MAX_VALUE;
    
    for (int i = 1; i < a.length; i++) {
        sum -= a[i - 1] * 2;
        min = min(min, abs(sum));
    }
    
    return min;
{% endhighlight %}

## 3. 결과
Correctness 100%,

Performance 는 시간 복잡도 O(N) 으로 감지되어 100%로

Task Score는 100 point가 되었다.


## 4. 코드 및 테스트 코드
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/main/codility/lesson/lesson3/TapeEquilibrium.java"
       class="btn btn-success" 
       target="_blank">
       TapeEquilibrium Code
    </a>
</div>   
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/test/codility/lesson/lesson3/TapeEquilibriumTest.java"
       class="btn btn-warning" 
       target="_blank">
       TapeEquilibrium Test Code
    </a>
</div>

