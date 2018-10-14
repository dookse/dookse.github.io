---
title: "Codility lesson3 : PermMissingElem"
date: 2018-10-14 12:20:00 +0900
categories: algorithm codility
---

## 1. 문제

배열 중에서 빠진 값을 찾는 문제다. 

예를 들어 [2, 3, 1, 5] 와 같은 배열이 있다고 하면, 답은 4가 된다.

lesson3의 주제가 Time Complexity기 때문에, 다른 것보다 performance에 중점을 두고 알고리즘을 작성해야 한다.


## 2. 풀이

[2, 3, 1, 5] 라는 배열이 주어졌을 경우

1..5 까지의 합을 구한후 주어진 배열의 합을 빼면, 빠진 값을 찾을 수 있다.

{% highlight java %}
    int missingSum = Arrays.stream(a).sum();
    int rangeSum = IntStream.rangeClosed(1, a.length + 1).sum();
    return rangeSum - missingSum;
{% endhighlight %}

코드 중, a.length + 1 이 가독성이 조금 떨어지기 때문에 IntSummaryStatistics를 사용하는 것도 생각해 볼 수 있는데,

IntSummaryStatistics를 사용하게 되면 빈 배열에 대한 예외 처리를 또 해줘야 하기 때문에 코드가 더 복잡해진다.

물론, 앞서 말했던 것처럼 lesson3의 주제가 Time Complexity 이기 때문에 위와 같이 문제를 풀면

근소한 차이로 performance 점수를 만점을 받지 못하는 경우가 있다. 

(테스트 메소드의 수행 시간에 따라 1ms 정도 차이가 나면서 통과할 때도 있고 통과하지 못할때도 있다.)  


실제 적용한 코드는 아래와 같다.

{% highlight java %}
    sort(a);
    for (int i = 0; i < a.length; i++) {
        int next = i + 1;
        if (isNextValueMissing(next, a[i])) {
            return next;
        }
    }
    return a.length + 1;
{% endhighlight %}

해당 배열을 정렬한 후, 배열의 다음 값을 하나씩 비교하면서 빠진 값을 찾으면 된다.  

for 문이 정상적으로 모두 수행되었다면, 마지막 값이 빠진 것이므로 해당 값을 리턴해주면 된다.


isNextValueMssing method 내용은 아래와 같다

{% highlight java %}
    private boolean isNextValueMissing(final int next, final int curr) {
        return next != curr;
    }
{% endhighlight %}

아주 간단한 수식이지만 메소드로 추출해서 사용했는데
 
첫번째 이유는 가독성 때문이고,

두번째 이유는 해당 수식에 대한 코드 작성자의 의도를 알 수 있기 때문이다.

if 문 내의 수식을 잘못 짠 경우 어떤 의도의 수식인지 알기 어렵기 때문에,
 
수식 오류인지 코드를 잘못 이해한 것인지 분석하는데 더 오랜 시간이 필요하다. 

하지만 메소드로 추출하고 메소드명을 문장 형태로 작성한 경우에는 

메소드 내의 수식을 확인하지 않고도 로직을 이해할 수 있으며,

수식이 잘못되었더라도 해당 오류를 조금 더 빨리 찾을 수 있게 된다.

물론 이것은 개인차가 존재하며, 내가 선호하는 방식일 뿐이다.
 

## 3. 결과
Correctness 100%,

Performance 는 시간 복잡도 O(N) or O(N*log(N)) 로 감지되어 100%로

Task Score는 100 point가 되었다.


## 4. 코드 및 테스트 코드
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/main/codility/lesson/lesson3/PermMissingElem.java"
       class="btn btn-success" 
       target="_blank">
       OddOccurrencesInArray Code
    </a>
</div>   
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/test/codility/lesson/lesson3/PermMissingElemTest.java"
       class="btn btn-warning" 
       target="_blank">
       OddOccurrencesInArray Test Code
    </a>
</div>

