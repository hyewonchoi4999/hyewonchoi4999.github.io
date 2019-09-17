---
sidebar:
    nav: "category"
title: "[Machine Learning] Introduction to Machine Learning"
excerpt: "머신러닝 소개"
categories:
    - Lecture/Machine Learning
permalink: /posts/Lecture/Machine Learning/Introduction
tags: [machine learning, intro]
use_math: true
toc: true
toc_sticky: true
comments: true
share: true
last_modified_at: 2019-09-17T16:00:00-10:00
---

<br>

# Machine Learning Basics
최근 컴퓨터공학 분야에서 가장 핫한 키워드 하나를 꼽으라면 단연 인공지능일 것입니다. 알파고의 등장을 기점으로 굉장히 많은 관심이 몰리고 있지요.
구글에 인공지능을 검색하면 기계학습, 딥러닝, 강화학습, 등 연관 검색어가 굉장히 많이 나옵니다. 그래서, 본격적으로 기계학습에 대한 포스팅을 하기 전,
기계학습이 무엇이고 어떤 것인지에 대해 간략하게 포스팅하고자 합니다.

## Machine Learning이란 무엇인가?
원론적인 이야기부터 하면, 1997년 Tom Mitchell이 발간한 "Machine Learning"이란 책에서는 기계학습을 "컴퓨터 프로그램은 **P라는 방법**으로 측정된 **T라는 작업**의 성능이 **E라는 경험**으로부터 향상된다면, T라는 작업과 P라는 측정방법에 대한 경험 E로부터 배운다고 한다."라고 정의했습니다. 조금 더 쉽게 말하면 기계학습에서 **학습**은
**컴퓨터 프로그램이 어떠한 상황에서 일반적인 결론을 낼 수 있도록 데이터를 통해 훈련시키는 과정**입니다. 

## 학습의 유형과 학습 방법
프로그램을 학습시키는 방식에 따라 **지도 학습(Supervised Learning)**, **비지도 학습(Unsupervised Learning)**, **강화 학습(Reinforcement Learning)** 그리고 반지도 학습(Semi-supervised Learning) 네 가지의 유형으로 묶을 수 있습니다. 반면, 프로그램을 학습시키는 방법도 딥러닝, K-Nearest Neighbor(KNN), Support Vector Machine(SVM) 등 여러가지가 존재합니다. 유형과 방법이 조금 헷갈릴 수도 있는데, 예를 들면, 어느 초등학교에서 수업을 한다고 가정합시다. 수업 유형에는 주입식 교육과 토론식 교육이 있고, 수업 방법에는 발표식 방법, 설명식 방법이 있다고 합니다. 어떤 수업 유형이든 발표식 방법과 설명식 방법을 모두 사용할 수 있지만, 수업의 내용이나 학습 효과에 따라 주로 사용되는 수업 방법이 달라질 수 있습니다. 마찬가지로, 기계학습에서도 지도 학습이든 강화 학습이든 딥러닝을 사용할 수 있지만, 프로그램 개발의 목적에 따라 딥러닝이 효과적일 수도 있고, KNN이 효과적일 수도 있습니다. 이번 포스팅에서는 학습 유형에 대해서 간략히 언급하고, 방법에 대해서는 추후에 조금 더 깊게 다루도록 하겠습니다.

### 지도 학습 (Supervised Learning)
지도 학습에는 **정답이 존재**합니다. 따라서 훈련에 사용되는 데이터는 입력값과 출력값의 쌍으로 이루어져 있으며, 프로그램은 입력값에 따라 출력값을 내도록 지도를 받습니다.
지도 학습의 목표는 훈련에 사용된 데이터가 아닌 **새로운 데이터가 입력으로 들어왔을 때, 정답을 출력하도록 프로그램을 훈련시키는 것**입니다.

- Classification

### 비지도 학습 (Unsupervised Learning)
비지도 학습은 지도학습과는 달리 **정답이 존재하지 않습니다**. 따라서 트레이닝 데이터와 테스트 데이터 모두 입력값만 존재하며, 주로 **입력값들 사이의 숨겨진 의미를 찾기 위한 통계 모델을 만드는 데에 사용**됩니다.

- Clustering
- Outlier Detection
- Dimensionality Redcution
- Topic Extraction
- Density Estimation
- Generative Adversarial Nets (GAN)
- Matrix Completion
- Recommender Systems

### 강화 학습 (Reinforcement Learning)
지도 학습과 비지도 학습에서 프로그램은 입력값에 따라 결과를 도출합니다. 반면, 강화 학습에서 프로그램은 매번 어떠한 **상황(state)**에 처해져 있다고 가정합니다. 그리고 프로그램의 **선택(action)**에 따라 **보상(rewards)**이 주어지는데, 주어진 보상은 다시 다음 상황에서 프로그램의 선택에 영향을 줍니다. 따라서 프로그램은 **보상을 극대화하기 위한 행동을 하도록 학습**됩니다.
