---
title: "Codility lesson4 : PermCheck"
date: 2018-11-04 13:10:55 +0900
categories: algorithm codility
---

## 1. 문제

주어진 배열이 순열인지 아닌지 체크하는 문제이다.

순열일 경우 1을, 순열이 아닐경우 0을 return하는 알고리즘을 구현하면 된다.

예를 들어, [4, 1, 3, 2] 의 경우 순열이므로 1을,

[4, 1, 3] 의 경우 2가 빠졌기 때문에 0을 return하면 된다.


## 2. 풀이

Time Complexity 문제를 풀기 위해서는 아래와 같은 고민이 필요하다.

1. 반복문 없이 수식을 이용해 계산이 가능한가?

2. 반복문을 몇 번 사용해야 하는가?

3. 반복문 사용 시 모든 배열에 접근이 필요한가?   

이 문제의 경우 반복문은 한 번만 사용하면 되며, 주어진 배열을 그대로 사용한다면 모든 배열의 확인이 필요하지만

배열을 먼저 정렬하게 되면 순열이 아니라고 판단되는 시점에서 반복문을 중단할 수 있다. 

{% highlight java %}
    sort(a);
    int seq = 1;
    for (int num : a) {
        if (isNotSequential(seq++, num)) {
            return 0;
        }
    }
    return 1;
{% endhighlight %}

{% highlight java %}
    private boolean isNotSequential(final int seq, final int a) {
        return seq != a;
    }
{% endhighlight %}

가독성을 살리려다 보니 오히려 코드가 길어지게 되었는데, 일반적인 코드는 아래와 같다.

{% highlight java %}
    sort(a);
    for (int i = 1; i <= a.length; i++) {
        if (i != a[i - 1]) {
            return 0;
        }
    }
    return 1;
{% endhighlight %}



## 3. 결과
Correctness : 100%

Performance : 100%

Detected time complexity : O(N) or O(N * log(N))

Task Score : 100 point


## 4. 코드 및 테스트 코드
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/main/codility/lesson/lesson4/PermCheck.java"
       class="btn btn-success" 
       target="_blank">
       PermCheck Code
    </a>
</div>   
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/test/codility/lesson/lesson4/PermCheck.java"
       class="btn btn-warning" 
       target="_blank">
       PermCheck Test Code
    </a>
</div>

