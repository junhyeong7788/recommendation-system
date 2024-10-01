# 추천 시스템 (Recommendation System)

## 🚀 학습 키워드

### 정의

- 추천 시스템 : 정보 필터링(IF) 기술의 일종으로, 특정 사용자가 관심을 가질만한 정보(영화, 책, 뉴스, 이미지, 웹 페이지 등)를 추천하는 것

### 키워드

- 추천은 예측이다. 추천은 상대방이 선호할 만한 결과를 제안하는 것

---

## 📝새로 배운 개념

### 개요

- 추천은 결과를 얻고자 하는 대상을 분석하는 일부터 시작, 그것은 대상에게 주고자 하는 것을 분석하는 일이 될 수 도 있고, 그 대상을 분석하는 일이 될 수도 있다.
- 추천 시스템은 이러한 추천을 데이터적이고, 컴퓨터적으로 옮겨온 것이다.
  - 또한 데이터의 양이 아주 많아지고, 유의미한 데이터를 분석하는 기법이 발달함에 따라 추천시스템을 구축할 수 있게 되었다.
- 하지만 추천은 데이터적으로 완전한 정답이 나오기는 힘들다.
  - 이유 : 결과로 보여준 것들의 대부분은 사용자가 경험하지 못한 것들에 대한 것이기 때문이다.
  - 이는 결과를 받은 후에, 평가로 확인하여야 비로소 정확한지 아닌지를 따질 수 있다.

#### 추천 시스템의 목적

- 관련성 : 사용자에게 적합한 아이템을 추천
- 참신성 : 사용자가 전에 본 적 없던 새로운 아이템을 추천
- 우연성 : 사용자에게 다소 의외이거나 놀라움을 주는 아이템을 추천

### 추천 시스템 알고리즘

- 기존의 단순한 알고리즘에서 다양한 대응을 할 수 있는 시스템의 구축을 위해 알고리즘이 더 복잡해진다.
- `Personalized Recommender` : Association Rule
  - 고객들의 상품 묶음 정보를 규칙으로 표현 (장바구니 분석)
  - 통계에 기반한 방법, 전체 상품 중에 고객이 함께 주문한 내역을 살펴본 뒤 상품간의 연관성을 수치화하여 나타내는 알고리즘
- `Attribute-based Recommender` : Content-based approach
  - 사용자의 행동이나 선호도를 기반으로 추천
- `Non-personalized Recommender` : Collaborative Filtering
  - 아이템의 콘텐츠를 기반으로 추천

```
- 추천 시스템
    |
    + --- 정보 필터링 --- + --- 콘텐츠 기반
    |                  |
    |                  + --- 협업 필터링 --- + --- 기억 기반
    |                  |                  |       사용자 기반
    |                  |                  |       아이템 기반
    |                  |                  |
    |                  |                  |
    |                  |                  + --- 모델 기반
    |                  |                          Clustering
    |                  |                          Bayesian
    |                  |                          Regression
    |                  |                          Matrix Factorization
    |                  |                          others
    |                  |
    |                  + --- 하이브리드
    |                          Weight
    |                          Mixed
    |                          Switching
    |                          Feature Combination
    |                          Feature Augmentation
    |                          Cascasde
    |                          Meta-level
    |
    + --- 연관성 분석
    |
    + --- 자연어 처리 기반
    |        Topic model(LDA)
    |        Word2Vec
    |
    + --- 딥러닝 기반
    |        Neural Collaborative Filtering
    |        Wide & Deep
    |        DeepFM
    |        AutoEncoder
    |
    + --- 발전적 주제
             편향(bias)
             context-aware
```

### 추천 시스템이 고려해야 할 요소

- 추천 시스템은 거의 대부분 B2C 비즈니스 환경에서 적용, 즉 고객, 아이템을 고려해야하고 추가적으로 시스템의 업데이트와 추천 시스템의 알고리즘적 성능을 고려해야한다.
- 시스템의 업데이트 : 얼마나 자주 추천되는 아이템의 리스트가 업데이트 되는 지에 대한 것
- 추천 시스템에서의 알고리즘 성능
  - 추천 모델의 계산량이나 연산 속도
  - 최신의 알고리즘 보다 훨씬 쉽고 간단하면서도 연산량이 작고, 그럼에도 불구하고 고급 알고리즘들과 비슷한 성능을 낼 수 있는 알고리즘들을 사용해야한다.
  - 빅데이터 처리할 수 있는 좋은 환경을 갖추어야 한다.

### 추천 시스템의 장애 요소

- Sparsity Problem (차원의 저주): 추천할 아이템과 고객은 계속 늘어나는 반면, 고객이 실제로 소비하게 되는 콘텐츠나 아이템의 비율은 현저하게 감소
- Information Utilization Problem : 사용자가 아이템에 대한 정보를 제공하지 않는 경우
  - 로그 데이터 속에 숨어있는 정보 (implicit score)를 explicit score처럼 데이터를 utilization하는 문제
- Filter Bubble : 사용자의 선호도나 관심사항을 고려하지 않고, 사용자의 행동을 기반으로 추천을 하는 경우 사용자의 관심사항이 한정적으로 제한될 수 있다.

---

## ✨

- REMIND : 추천시스템 정의, 목적, 알고리즘, 고려해야 할 요소, 장애 요소

## 💻활용 사례

### 활발한 사용 분야

- 페이스북
  - 사용자가 좋아하는 페이지, 친구의 활동, 사용자의 행동을 기반으로 추천
- 넷플릭스
  - 사용자가 시청한 영화, 평가한 영화, 시청한 영화의 장르를 기반으로 추천
  - Cine - match Algorithm : Content-based Filtering, Collaborative Filtering을 함께 사용하는 하이브리드 추천 알고리즘
- 아마존
  - 사용자가 구매한 상품, 평가한 상품, 상품의 카테고리를 기반으로 추천
  - Item-to-Item Collaborative Filtering
    - 제품들 간의 유사성을 계산, 특정 제품을 구매한 모든 고객에 대해서 각 고객이 구매한 다른 제품과 이 제품과의 유사성의 합을 계산, 모든 고객들에게 적용

## 🔗레퍼런스

### 참고 강의/글

- [추천시스템(1)-개요 및 알고리즘](https://davinci-ai.tistory.com/12)
- [추천시스템(2)-실제시스템분석](https://davinci-ai.tistory.com/13)
- [[Recommender System] 추천시스템의 전반적인 내용](https://yamalab.tistory.com/67)
- [DataScience School 13.1 추천시스템](https://datascienceschool.net/03%20machine%20learning/07.01%20%EC%B6%94%EC%B2%9C%20%EC%8B%9C%EC%8A%A4%ED%85%9C.html)
- [추천 시스템 A to Z : 추천 알고리즘의 종류](https://calmmimiforest.tistory.com/100)
