---
title: "Codility lesson2 : CyclicRotation"
date: 2018-09-30 22:00:00 -0900
categories: algorithm codility
comments: true
---

## 1. 문제

배열을 지정된 수 만큼 오른쪽으로 회전시키는 문제다.

배열을 오른쪽으로 회전시킨다는 것은 

각 요소가 하나의 인덱스 만큼 오른쪽으로 이동되고,

마지막 요소는 첫번째 인덱스로 이동하는 것을 말한다.

배열 [3, 8, 9, 7, 6]을 예로 들면,

1회전 : [3, 8, 9, 7, 6] -> [6, 3, 8, 9, 7]

2회전 : [6, 3, 8, 9, 7] -> [7, 6, 3, 8, 9]

3회전 : [7, 6, 3, 8, 9] -> [9, 7, 6, 3, 8]

4회전 : [9, 7, 6, 3, 8] -> [8, 9, 7, 6, 3]

5회전 : [8, 9, 7, 6, 3] -> [3, 8, 9, 7, 6]

결국 길이가 5인 배열은 5번 회전 후에 원래대로 돌아가게 된다.

## 2. 풀이

지금처럼 주어진 배열을 큐로 변환하기만 하면 실 수행 로직이 간단해 질 경우에는

데이터 변환 작업과 실 수행 작업을 분리하는 형태로 구현하는 것을 선호하는 편이다.

queue를 사용하면 아래와 같이 간단하게 배열 회전을 구현할 수 있다.

{% highlight java %}
    for (int i = 0; i < k; i++) {
        list.push(list.pollLast());
    }
{% endhighlight %}


문제에서 원하는 것이 배열을 받아 K만큼 회전시킨 배열을 반환하는 것이므로 

배열을 queue로 변환하는 메소드가 필요하다.

{% highlight java %}
    private LinkedList<Integer> getLinkedListFrom(final int[] intArray) {
        return of(intArray)
            .boxed()
            .collect(toCollection(LinkedList::new));
    }
{% endhighlight %}

그리고 마지막으로 회전시킨 queue를 다시 배열로 변환하는 메소드를 작성하면 된다.

다만 이때 빈 배열이 주어졌을 때 NullPointerException이 발생하지 않도록 주의해야 한다.
 
{% highlight java %}
    private int[] getIntArrayFrom(final LinkedList<Integer> list) {
        return list.stream()
            .filter(Objects::nonNull)
            .mapToInt(i -> i)
            .toArray();
    }
{% endhighlight %}


## 3. 결과
이번 문제도 지난 문제와 같이 Performance 점수가 없다.

Correctness 100% 로 Task Score는 100 point가 되었다.


## 4. 코드 및 테스트 코드
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/main/codility/lesson/lesson2/CyclicRotation.java"
       class="btn btn-success" 
       target="_blank">
       CyclicRotation Code
    </a>
</div>   
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/test/codility/lesson/lesson2/CyclicRotationTest.java"
       class="btn btn-warning" 
       target="_blank">
       CyclicRotation Test Code
    </a>
</div>

