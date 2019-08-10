---
sidebar:
    nav: "category"
title: "[Data Structure] Linear List"
excerpt: "자료구조 선형 리스트"
categories:
    - Lecture/Data Structure
permalink: /posts/Lecture/Data Structure/linear-list
tags: [data structure, linear list]
use_math: true
toc: true
toc_sticky: true
comments: true
share: true
last_modified_at: 2019-08-10T19:00:00-10:00
---

<br>

# Linear List

## Linear List란?
앞서 자료구조는 여러가지 데이터를 담을 수 있는 바구니라고 했습니다. **Linear List는 자료구조라는 바구니의 종류 중 하나**입니다. Linear List에 들어가는 데이터들은 말 그대로 선형적인 구조를 가지고, 순서대로 정렬될 수 있어요. 그리고 이 데이터들은 고정된 사이즈를 가질 수도, 다양한 사이즈를 가질 수도 있습니다. 또한, **List는 Abstract Data Type(ADT)**인데, ADT란 명칭에서도 언급되듯 추상적, 개념적 데이터 타입입니다. 즉, **명시적으로 구현되지 않고, 데이터의 기능이나 역할이 개념적으로만 정의되어 있다**는 뜻이에요. 따라서, **필요에 따라 다양한 방식으로 구현**할 수 있고, 그 대표적인 구현 방법들이 Array나 Linked-list입니다.

간단하게 언급하자면, Array는 고정된 크기의 메모리를 미리 할당하고, 할당된 메모리 안에 데이터들을 저장하는 방법으로, 이렇게 구현한 것을 정적으로(Statically) 구현했다고 합니다.

<p align="center">
    <img width="600" height="100" src="/assets/images/datastructure/staticlist.png">
</p>

반면, Linked-list는 동적으로(Dynamically) 구현되는데, 필요에 따라 그 때 그 때 메모리를 할당하여 사용할 수 있습니다.

<p align="center">
    <img width="600" height="100" src="/assets/images/datastructure/linkedlist.png">
</p>

## Examples of operations
다음으로 Linear List에서 사용할 수 있는 간단한 기능들에 대해 알아보겠습니다. 앞서 말했듯이 List는 ADT이기 때문에 다양한 방식으로 구현할 수 있고, 구현자에 따라 다양한 기능을 가질 수 있습니다. 따라서 아래에 언급하는 기능들이 전부가 아니며, 또한 반드시 있을 필요도 없습니다.

아래에 언급되는 리스트 및 함수들은 파이썬에 내장된 리스트가 아닌 사용자가 필요에 따라 배열 기반으로 직접 구현했다고 가정하고, 코드는 편의상 파이썬 문법의 형태를 따르도록 하겠습니다.

### 1. length()
예를 들어 파이썬에서 사용자가 구현한 리스트의 함수(기능) 중 선언된 리스트 변수의 크기를 반환해주는 length()라는 함수가 있다고 합시다. 파이썬 인터프리터에서 다음과 같은 코드를 입력하면 5를 반환합니다.

    >>> L = ['a', 'b', 'c', 'd', 'e']
    >>> L.length() # len(L)과 동일한 결과값을 반환
    5

### 2. retrieve(index)
retrieve(index) 함수는 인덱스를 인자로 받고 그 인덱스의 위치에 있는 데이터를 반환하는 함수입니다.

    >>> L = ['a', 'b', 'c', 'd', 'e']
    >>> L.retrieve(2)
    'c' 

### 3. indexOf(element)
indexOf(element) 함수는 데이터를 인자로 받고, 데이터의 인덱스를 반환하는 함수입니다.

    >>> L = ['a', 'b', 'c', 'd', 'e']
    >>> L.indexOf('b')
    1

### 4. delete(index)
delete(index) 함수는 인덱스를 인자로 받아 인덱스 위치의 데이터를 제거하는 함수입니다.

    >>> L = ['a', 'b', 'c', 'd', 'e']
    >>> L.delete(3)
    >>> L
    ['a', 'b', 'c', 'e']

### 5. add(element)
add(element) 함수는 리스트의 가장 뒤에 인자로 받은 데이터를 추가하는 함수입니다.

    >>> L = ['a', 'b', 'c', 'd', 'e']
    >>> L.add('f')
    >>> L
    ['a', 'b', 'c', 'd', 'e', 'f']

앞서도 말했듯이, 각 프로그래밍 언어마다 내장되어 있는 리스트 자료구조를 사용하지 않고 직접 구현하여 사용할 경우 위의 함수들 외에도 다양한 함수들을 구현하고 사용할 수 있습니다.