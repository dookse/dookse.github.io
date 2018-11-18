---
title: "Codility lesson4 : MaxCounters"
date: 2018-11-18 20:03:55 +0900
categories: algorithm codility
comments: true
---

## 1. 문제

N개의 카운터와 입력 배열이 주어지며, 아래 두 가지 기능을 수행할 수 있어야 한다.

increase(X) − 카운터 X 를 1 증가시킨다.

max counter − 모든 카운터를 최대값으로 설정한다.

배열 값이 N + 1 일 경우는 max counter, 그 외의 경우에는 increase를 수행하면 된다. 

(문제에는 1 ≤ X ≤ N 일 경우 incrase라고 되어 있지만, 배열의 범위값이 1..N + 1 이기 때문에 

X 가 N + 1 인지 아닌지만 체크하면 된다.) 

## 2. 풀이

문제에 주어진 대로 우선 기본 골격은 max counter와 increase를 분기하는 것으로 한다.

{% highlight java %}
    int[] result = init(n, a);
    for (int i = 0; i < a.length; i++) {
        int num = a[i];
        switch (getOperation(num)) {
            case MAX_COUNTER:
                maxCounter(result, i);
                break;
            case INCREASE:
                increase(result, num);
                break;
        }
    }
    return result;
{% endhighlight %}

기본적인 프로세스는 max counter 일 때는 값만 저장하고, increase 일 때는 maxCount 값과 비교 후 1 증가시킨다. 

마지막 max counter를 수행할 index를 구해서 해당 index에서만 max counter 처리를 수행한다. 

코드를 분리하다 보니 엄청나게 길어져 버렸는데, lastCounterIndex 구하는 부분 로직이 좀 아쉽다.

increase 및 max counter 코드는 아래와 같다.

{% highlight java %}
    private void increase(final int[] result, final int i) {
        if (maxCount > result[i - 1]) {
            result[i - 1] = maxCount;
        }
        currentMaxValue = max(++result[i - 1], currentMaxValue);
    }
{% endhighlight %}

{% highlight java %}
private void maxCounter(final int[] ans, final int idx) {
    if (lastCounterIndex == idx) {
        for (int i = 0; i < ans.length; i++) {
            ans[i] = currentMaxValue;
        }
    }
    maxCount = currentMaxValue;
}
{% endhighlight %}


## 3. 결과
Correctness : 100%

Performance : 100%

Detected time complexity : O(N + M)

Task Score : 100 point


## 4. 코드 및 테스트 코드
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/main/codility/lesson/lesson4/MaxCounters.java"
       class="btn btn-success" 
       target="_blank">
       MaxCounters Code
    </a>
</div>   
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/test/codility/lesson/lesson4/MaxCountersTest.java"
       class="btn btn-warning" 
       target="_blank">
       MaxCounters Test Code
    </a>
</div>

