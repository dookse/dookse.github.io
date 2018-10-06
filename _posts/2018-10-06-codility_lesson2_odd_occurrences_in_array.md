---
title: "Codility lesson2 : OddOccurrencesInArray"
date: 2018-10-06 08:47:00 +0900
categories: algorithm codility
---

## 1. 문제

주어진 N 길이의 배열 중에서 짝이 없는 unique한 값을 찾아내는 문제다.

예를 들어 [9, 3, 9, 3, 9, 7, 9] 와 같은 배열이 있다고 하면

9와 3은 동일한 값이 있기 때문에 7이 답이 된다.  

N은 1..1,000,000 범위의 홀수로 주어지기 때문에 예외 처리를 할 필요는 없으나 performance에 신경써야 한다.


## 2. 풀이

Set.add()는 기존에 같은 값이 있는지에 따라 boolean 값을 반환하는 점을 이용해,

주어진 배열에 있는 데이터를 하나씩 Set에 넣으면서 중복된 값을 제거해 unique한 값만 남도록 구현했다.

{% highlight java %}
    for (int num : a) {
        if (!set.add(num)) {
            set.remove(num);
        }
    }
{% endhighlight %}


for 문이 수행된 이후에는 Set에는 하나의 데이터만 남아있기 때문에 아래와 같이 return하면 된다.

문제에서 주어진 배열의 길이가 홀수이고 빈 배열이 전달되는 경우는 없기 때문에 예외 처리는 따로 하지 않았다.

{% highlight java %}
    return set.iterator().next();
{% endhighlight %}


## 3. 결과
Correctness 100%,
Performance 는 시간 복잡도 O(N) or O(N*log(N)) 로 감지되어 100%로
Task Score는 100 point가 되었다.


## 4. 코드 및 테스트 코드
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/main/codility/lesson/lesson2/OddOccurrencesInArray.java"
       class="btn btn-success" 
       target="_blank">
       OddOccurrencesInArray Code
    </a>
</div>   
<div markdown="0">
    <a href="https://github.com/parksolo/algoStudy/blob/master/src/test/codility/lesson/lesson2/OddOccurrencesInArrayTest.java"
       class="btn btn-warning" 
       target="_blank">
       OddOccurrencesInArray Test Code
    </a>
</div>

