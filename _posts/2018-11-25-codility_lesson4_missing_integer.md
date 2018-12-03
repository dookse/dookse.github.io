---
title: "Codility lesson4 : MissingInteger"
date: 2018-11-25 17:28:00 +0900
categories: algorithm codility
comments: true
---

## 1. 문제

주어진 배열에서 포함되지 않는 0보다 큰 정수를 찾는 문제다.

최소 정답은 1로, 배열에 음수만 주어졌을 경우에는 1이 return 되어야 한다.


## 2. 풀이

단순하게 정렬 후 비어있는 값인지 아닌지 반복문을 통해 체크하면 되는데,

음수가 있을 경우가 있기 때문에 마지막 정수값을 담고 있는 임시 변수를 사용해 해당 값을 통해 비교했다.

{% highlight java %}
    Arrays.sort(a);
    for (final int num : a) {
        if (isMissingNumber(num)) {
            return index;
        } else if (isNotMissingNumber(num)) {
            lastPositiveNum = num;
            index++;
        }
    }
    return index;
{% endhighlight %}

이번 코드에는 반복문 내에서 증감값으로 사용하는 index를 필드로 사용하고

필드 선언시 초기값을 할당해 주었는데, 이렇게 되면 thread safe 하지 않을 수 있다.

다만, JUnit을 포함한 대부분의 테스트 유틸은 테스트 케이스 마다 새로운 객체를 생성하기 때문에
  
코딜리티나 테스트 코드로 테스트하는 경우에는 문제가 되지 않는다.


## 3. 결과
Correctness : 100%

Performance : 100%

Detected time complexity : O(N) or O(N * log(N))

Task Score : 100 point


## 4. 코드 및 테스트 코드
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/main/codility/lesson/lesson4/MissingInteger.java"
       class="btn btn-success" 
       target="_blank">
       MissingInteger Code
    </a>
</div>   

