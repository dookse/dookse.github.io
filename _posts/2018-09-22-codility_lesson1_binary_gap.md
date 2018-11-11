---
title: "Codility lesson1 : BinaryGap"
date: 2018-09-22 18:25:00 -0900
categories: algorithm codility
comments: true
---

## 1. 문제
코딜리티 lesson 첫번째 문제.

양수 n을 받아 binary gap을 계산하면 되는 문제다.

binary gap이란 2진수에서 1로 둘러싸인 0의 길이를 말한다.

숫자 9의 경우, 이진수로 변환하면 1001이 되는데, 이것은 1과 1 사이에 0이 2개가 있으므로 binary gap은 2가 된다.

숫자 20의 경우, 이진수로 변환하면 10100이 되는데, 1로 둘러싸인 0은 101 에 있는 하나밖에 없기 때문에 binary gap은 1이 된다.

물론 이진수 100000의 경우에는 binary gap은 0이 된다.


## 2. 풀이
문제에서 제시한 대로 시뮬레이션 코드를 만들면 된다.

입력받은 int n을 2진수로 변환한 후, 0의 길이가 가장 긴 값을 찾으면 된다.

2진수로 변환한 후 1로 split 한 다음, 해당 배열 중에서 길이가 가장 긴 값을 찾으면 된다.

해당 메소드는 아래와 같다.

{% highlight java %}
    private int getMaxLengthFrom(final String[] zeros) {
       return stream(zeros)
           .max(comparingInt(String::length))
           .orElse(EMPTY)
           .length();
    }
{% endhighlight %}

다만 이렇게 할 경우 1000 과 같은 2진수의 경우 실제 답인 0이 아닌 3으로 결과가 나오기 때문에 예외 처리가 필요하다.

아래와 같이 2진수 값이 0으로 끝나는 경우에만 예외 처리를 해 주었다.

{% highlight java %}
    if (binary.endsWith("0")) {
        zeros[zeros.length - 1] = EMPTY;
    }
{% endhighlight %}

## 3. 결과
첫번째 문제는 Performance 점수가 없다.

Correctness 100% 로 Task Score는 100 point가 되었다.


## 4. 코드 및 테스트 코드
<div markdown="0"><a href="https://github.com/parksolo/algoStudy/blob/master/src/main/codility/lesson/lesson1/BinaryGap.java" class="btn btn-success" target="_blank">BinaryGap Code</a></div>   
<div markdown="0"><a href="https://github.com/parksolo/algoStudy/blob/master/src/test/codility/lesson/lesson1/BinaryGapTest.java" class="btn btn-warning" target="_blank">BinaryGap Test Code</a></div>

