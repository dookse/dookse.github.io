---
title: "Codility lesson4 : FrogRiverOne"
date: 2018-11-10 19:35:55 +0900
categories: algorithm codility
---

## 1. 문제

개구리가 건너편 강으로 넘어가는 가장 빠른 시간을 구하는 문제로

나뭇잎이 1부터 X까지 모든 위치에 나타났을 때만 건널 수 있다.

아래와 같은 배열이 있고 X가 5라면, 답은 6이 된다.

  A[0] = 1,
  A[1] = 3,
  A[2] = 1,
  A[3] = 4,
  A[4] = 2,
  A[5] = 3,
  A[6] = 5,
  A[7] = 4

## 2. 풀이

X를 정해진 step으로 사용해 나뭇잎 위치를 set에 넣을 수 있을 때 

step을 하나씩 줄여나가는 방식으로 진행한다. 

마지막 step까지 진행되었을 때의 시간이 답이 되며,

반복문이 종료될 때 까지 마지막 step이 진행되지 않았다면, 건너는 못하는 상황이므로 답은 -1이 된다.

배열의 범위는 [1..X] 이기 때문에 set의 size를 비교하는 등 다른 예외 처리는 할 필요 없다.

{% highlight java %}
    initSteps(x);
    for (int seq = 0; seq < a.length; seq++) {
        goNextStep(a[seq]);
        if (isLastStep()) {
            return seq;
        }
    }
    return -1;
{% endhighlight %}

{% highlight java %}
    private void initSteps(final int x) {
        set = new HashSet<>();
        steps = x;
    }
{% endhighlight %}

{% highlight java %}
    private void goNextStep(final int num) {
        if (set.add(num)) {
            steps--;
        }
    }
{% endhighlight %}

{% highlight java %}
    private boolean isLastStep() {
        return steps == 0;
    }
{% endhighlight %}


## 3. 결과
Correctness : 100%

Performance : 100%

Detected time complexity : O(N)

Task Score : 100 point


## 4. 코드 및 테스트 코드
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/main/codility/lesson/lesson4/FrogRiverOne.java"
       class="btn btn-success" 
       target="_blank">
       FrogRiverOne Code
    </a>
</div>   
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/test/codility/lesson/lesson4/FrogRiverOneTest.java"
       class="btn btn-warning" 
       target="_blank">
       FrogRiverOne Test Code
    </a>
</div>

