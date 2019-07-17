---
sidebar:
    nav: "category"
title: "[Data Structure] Performance Analysis"
excerpt: "퍼포먼스 분석을 하는 이유와 분석 방법"
categories:
    - lecture/Data Structure
permalink: /categories/lecture/Data Structure/performance-analysis
tags: [data structure, time complexity, performance analysis]
use_math: true
toc: true
toc_sticky: true
comments: true
share: true
last_modified_at: 2019-07-17T15:00:00-10:00
---

<br>

# 자료구조와 퍼포먼스

## 자료구조란?
먼저 자료구조란 **여러가지 데이터들을 담을 수 있는 바구니**라고 생각하시면 됩니다. 바구니에는 사과도 담을 수 있고, 바나나도 담을 수 있고, 귤도 담을 수 있습니다. 즉, **여러가지 형태의 데이터들을** 담을 수 있고, 이러한 데이터들을 **사용자가 원하는 방식으로 배치하거나 정렬하여 저장**할 수 있습니다. 이렇게 저장된 자료들은 추 후에 사용자가 원할 때 언제든 꺼내어 쓸 수 있고, 그래야 합니다.

## 알고리즘과 퍼포먼스
다시 바구니 예시로 돌아와서 바구니에 과일을 담을 수도 있고, 바구니 안에 과일을 일정한 기준에 따라 정렬할 수도 있고, 과일을 뺄 수도 있습니다. 마찬가지로 자료구조에도 데이터를 넣고, 정렬하고, 찾고, 뺄 수 있는데, 이러한 기능들을 수행하는 방법을 알고리즘이라고 합니다. 그리고 한 기능을 수행하는 데에는 여러가지 알고리즘이 있을 수 있겠지요. 예를 들어 정렬을 하는 방법 중에는 앞에서부터 정렬할 수도 있고, 뒤에서부터 정렬할 수도 있고, 가운데에서부터 정렬을 할 수도 있습니다. 

하나의 알고리즘을 수행하는 데에 걸리는 시간을 **time complexity**라고 하며, 알고리즘을 수행하는 데에 사용된 메모리의 양을 **spatial complexity**라고 합니다. (두 complexity는 단순 양을 의미하는 것은 아닌데 추 후에 더 자세하게 설명하도록 하겠습니다.) 즉, 알고리즘을 수행하는 데에 사용된 시간과 공간의 양에 따라 퍼포먼스가 달라지게 되고, 이 시간과 공간의 양을 분석하는 것을 퍼포먼스 분석이라고 합니다.

참고로 **알고리즘은** 위에서 언급한 것처럼 단순히 자료구조의 기능을 수행하는 방법만을 의미하는 것이 아니라, **어떠한 문제를 푸는 방법**이라는 개념으로 이해하시는 것이 좋습니다.

<br>

# 퍼포먼스 분석
퍼포먼스를 분석하는 이유는 어떠한 문제던 간에 절대적으로 좋은 알고리즘은 없기 때문에 여러 알고리즘을 비교하고 문제를 푸는 데에 더 적합한 알고리즘을 선택하기 위해서입니다. 따라서 당연히 퍼포먼스 분석을 통해 얻은 결과가 좋을수록 알고리즘의 성능도 좋아집니다. 그리고 이 퍼포먼스를 분석하는 데에 사용되는 개념 중 하나가 time complexity입니다.

## Time Cmoplexity
Time complexity란 위에서 언급했듯이 알고리즘을 수행하는 데에 걸리는 시간입니다. 그런데 퍼포먼스 분석을 하기 위해 매번 알고리즘을 짜고 실행하여 실행 시간을 측정하는 것은 굉장히 비효율적입니다. 따라서 퍼포먼스 분석을 좀 더 용이하게 하기 위해, time complexity를 나타내기 위한 여러 표기법들이 존재합니다. 그럼 time complexity를 표기할 때 자주 쓰이는 표기법들에 대해 알아보도록 하겠습니다.

### 1. Big Oh($O$)
<p align="center">
    <img width="250" height="250" src="/assets/images/datastructure/BigOh.png">
</p>

> def) $n \geq n_0$인 모든 $n$에 대하여, $f(n) \leq c \cdot g(n)$을 만족하는 양의 상수 $c$와 $n_0$이 존재한다면,

$$ f(n) = O(g(n)) $$

그림에서 알 수 있듯이 $n_0$ 이 후로 $f(n)$은 항상 $c \cdot g(n)$ 보다 작습니다. 이 때, $c \cdot g(n)$은 $f(n)$의 **upper bound를 보장**하고 이를 $f(n) = O(g(n))$이라 표기합니다. upper bound를 보장한다는 말은 최악의 경우를 고려한다는 뜻으로, "아무리 오래 걸려도 $g(n)$보다는 같거나 적은 시간이 걸린다"라는 의미를 갖습니다.

예를 들어 $f(n) = 2n^2, g(n) = n^2$이고 $c = 3$이면, $2n^2 \leq 3n^2$이 성립하고, 이를 $f(n) = O(n^2)$이라 표기합니다. 일반적으로 $g(n)$은 $f(n)$의 최고차항의 계수가 1인 함수로 표기됩니다.

### 2. Big Omega($\Omega$)
<p align="center">
    <img width="250" height="250" src="/assets/images/datastructure/BigOmega.png">
</p>

> def) $n \geq n_0$인 모든 $n$에 대하여, $f(n) \geq c \cdot g(n)$을 만족하는 양의 상수 $c$와 $n_0$이 존재한다면,

$$ f(n) = \Omega(g(n)) $$

Big Oh와는 반대로 $f(n)$은 $n_0$ 이 후로 항상 $c \cdot g(n)$ 보다 큽니다. 따라서 이 때 $c \cdot g(n)$은 $f(n)$의 **lower bound를 보장**하고 이를 $f(n) = \Omega(g(n))$이라 표기합니다. lower bound를 보장한다는 것은 최선의 경우를 고려한다는 뜻으로, "아무리 빨라도 $g(n)$보다는 같거다 많은 시간이 걸린다"라는 의미를 갖습니다.

예를 들어 $f(n) = 2n^2, g(n) = n^2$이고 $c = 1$이면, $2n^2 \geq n^2$이 성립하고, 이를 $f(n) = \Omega(n^2)$이라 표기합니다.

### 3. Big Theta($\Theta$)
<p align="center">
    <img width="250" height="250" src="/assets/images/datastructure/BigTheta.png">
</p>

> def) $n \geq n_0$인 모든 $n$에 대하여, $c_1 \cdot g(n) \leq f(n) \leq c_2 \cdot g(n)$을 만족하는 양의 상수 $c_1, c_2$와 $n_0$이 존재한다면,

$$ f(n) = \Theta(g(n)) $$

Big Oh가 $f(n)$의 upper bound를 보장하는 표기법이고, Big Omega가 $f(n)$의 lower bound를 보장하는 표기법이었다면, **Big Theta는 $f(n)$의 upper bound와 lower bound 모두를 보장**하는 표기법입니다. 그림에서 $f(n)$은 $c_1 \cdot g(n)$과 $c_2 \cdot g(n)$ 사이에 존재합니다. 이 때 $g(n0)$은 양의 상수 $c_1$과 $c_2$에 의해 $f(n)$의 upper bound가 될 수도 있고, lower bound가 될 수도 있습니다. upper bound와 lower bound가 모두 보장된다는 것은 알고리즘의 수행시간을 상당히 구체적으로 알 수 있다는 뜻입니다. 따라서, Big Theta 표기법은 보통 알고리즘의 수행시간이 명확할 때 사용됩니다.

예를 들어 $f(n) = n^2 + 2n$, $g(n) = n^2 + n$, $c_1 = 1, c_2 = 3$이라 하면, 어림잡아 $n \geq 1$일 때, $n^2 + n \leq n^2 + 2n \leq 3n^2 + 3n$이 성립하고, 이를 $f(n) = \Theta(n^2)$이라 표기합니다.

## Polynomial time and Exopnential time
동일한 알고리즘이라도 메모리 상황이나 데이터의 양 등 다른 요인으로 인해 실행할 때 마다 수행시간이 달라질 수 있습니다. 그래서 보통은 정확한 수행시간을 특정하기 힘들고, 일반적으로 수행 시간의 worst case, 즉 최악의 경우를 고려하여 퍼포먼스를 측정합니다. 따라서 알고리즘의 upper bound를 보장하는 Big Oh 표기법이 가장 많이 사용됩니다. 아래 그림에서 $g(n)$이 exponential 함수에 가까울수록 수행시간이 길어진다는 의미이고 이는 알고리즘의 퍼포먼스가 낮아진다는 뜻입니다.

<p align="center">
    <img width="400" height="400" src="/assets/images/datastructure/complexities.png">
</p>

다음은 각 함수의 크기를 오름차순으로 정렬하고 함수의 크기가 커짐에 따라 걸리는 시간을 그래프로 나타낸 것입니다.

$$ 1, logN N, NlogN, N^2, N^3, ..., 2^N, ..., N!, N^N $$

<p align="center">
    <img width="350" height="350" src="/assets/images/datastructure/orderofgrowth.png">
</p>