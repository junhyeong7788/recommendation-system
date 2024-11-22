# 🚀 학습 키워드

## 기본 정의

- Matrix Factorization (행렬 분해) : 행렬을 두 개 이상의 하위 행렬로 분해하여 원래 행렬을 근사하거나 분석하는 기법.
  - 이는 데이터 압축, 차원 축소, 패턴 탐지, 신호 처리 등 다양한 분야에서 사용됨

## 키워드

추천시스템에서의 Matrix Factorization : 사용자와 아이템 간의 관계를 나타내는 **평점행렬** 을 두 개의 작은 행렬로 분해하여 학습

- 사용자와 아이템 간의 잠재요인(Latent Factor)을 학습하여 사용자에게 적합한 아이템을 추천하는 강력한 기법, 이 방법은 주로 **협업 필터링** 의 한 종류로 사용
- 가장 중요한 부분은 `행렬 분해를 통해 예측된 평점` $r_{i,j}$ `가 높은 아이템을 사용자에게 추천하는 프로세스`, 이 과정이 추천 시스템의 핵심 목표이자 최종적인 목적

---

# 📝새로 배운 개념

## MF란?

- 주어진 행렬 $A$ 를 두 개 이상의 하위 행렬로 분해하여 원래 행렬을 표현하려는 과정
- 즉, 행렬 $A$ 를 다음과 같이 분해
  - $A \approx B \times C$
  - $A$ : 원본 행렬
  - $B$ : 분해된 행렬
  - $C$ : 분해된 행렬
  - $k$ : 잠재 요인의 차원 수
- 분해된 두 행렬 B와 C의 곱은 A를 근사. 이 과정은 데이터를 더 간결하게 표현하거나 숨겨진 구조를 발견하는 데 도움

## Matrix Factorization의 주요 방법

1. SVD (Singular Value Decomposition)
   - $A = U \times S \times V^T$
   - 활용 : 차원 축소, 신호처리 및 데이터 압축
2. NMF (Non-negative Matrix Factorization)
   - $A \approx W \times H$
   - 정의 : 모든 값이 음수가 아닌 행렬 $A$ 를 두 개의 음수가 아닌 행렬 $B$ 와 $C$ 로 분해
   - 활용 : 패턴 분석, 주성분 분석(PCA) 대체
3. QR Decomposition
   - $A = Q \times R$
   - 정의 : 행렬 $A$ 를 직교 행렬 $Q$ 와 상삼각 행렬 $R$ 로 분해
   - 활용 : 선형 방정식 풀이, 행렬 계산 단순화
4. LU Decomposition
   - $A = L \times U$
   - 정의 : 행렬 $A$ 를 하삼각 행렬 $L$ 과 상삼각 행렬 $U$ 로 분해
   - 활용 : 연립 방정식 풀이, 행렬 역행렬 계산

---

# ✨

## Matrix Factorization의 주요 목적

1. 차원 축소
   - 고차원 데이터를 낮은 차원으로 압축하여 효율성을 높이고 데이터 패턴 이해
2. 데이터 근사
   - A가 희소 행렬(데이터가 일부만 채워진 행렬)일 경우, 분해된 행렬을 이용해 누락된 데이터를 근사가능
3. 패턴 추출
   - 데이터에 숨겨진 구조나 관계를 파악

## 추천시스템에서의 Matrix Factorization

- 평점 행렬 R : $$R =\begin{bmatrix} r_{1,1} & r_{1,2} & \cdots & r_{1,n} \\ r_{2,1} & r_{2,2} & \cdots & r_{2,n} \\ \vdots  & \vdots  & \ddots & \vdots  \\ r_{m,1} & r_{m,2} & \cdots & r_{m,n} \\\end{bmatrix}$$
- $R$ : 사용자와 아이템 간의 평점을 나타내는 행렬
- $r_{i,j}$ : 사용자 $i$ 가 아이템 $j$ 에 준 평점
- $m$ : 사용자 수, $n$ : 아이템 수

- 행렬 분해 : 평점 행렬 $R$ 을 다음과 같이 두개의 작은 행렬로 분해

  - $R \approx P \times Q^T$
  - $P$ : 사용자와 잠재요인 간의 관계를 나타내는 행렬
  - $Q$ : 아이템과 잠재요인 간의 관계를 나타내는 행렬
  - $k$ : 잠재요인의 차원 수
  - 이 과정에서 $P$ 와 $Q$ 를 학습하여 사용자와 아이템을 **공통의 잠재 공간** 에서 나타냄

- 평점 예측 : $r_{i,j}$ 는 $i$ 가 아이템 $j$ 에 부여할 것으로 예측되는 평점

  - $r_{i,j} = p_i \cdot q_j^T$
  - $P_i$ : 사용자 $i$ 의 잠재요인 벡터
  - $Q_j$ : 아이템 $j$ 의 잠재요인 벡터
  - `예측된 평점` $r_{i,j}$ `가 높은 아이템을 사용자에게 추천`

- 학습 과정 : P와 Q를 학습하기 위해 손실함수를 최소화하는 최적화 과정을 수행
  - `손실함수` : $L = \sum_{(i, j) \in \text{Known Ratings}} (r_{i,j} - P_i \cdot Q_j^T)^2 + \lambda \left( \|P\|^2 + \|Q\|^2 \right)$
    - 첫번째항 : 실제 평점 $r_{i,j}$ 와 예측 평점 $P_i \cdot Q_j^T$ 의 차이를 최소화
    - 두번째항 : L2 정규화 항으로, 모델의 복잡도를 줄이고 과적합을 방지
    - $\lambda$ : 정규화 강도를 조절하는 하이퍼파라미터
  - `확률적 경사 하강법 SGD` : P와 Q를 업데이트
    - $P_i \gets P_i + \alpha \cdot (2 \cdot (r_{i,j} - P_i \cdot Q_j^T) \cdot Q_j - \lambda \cdot P_i)$
    - $Q_j \gets Q_j + \alpha \cdot (2 \cdot (r_{i,j} - P_i \cdot Q_j^T) \cdot P_i - \lambda \cdot Q_j)$

---

# 🔗레퍼런스

## 참고 강의/글

- [SVD.md](https://github.com/junhyeong7788/recommendation-system/blob/c5c214d24b0b32ab34618541922960731c85897d/information-filtering/collaborative-filtering/model-based/SVD.md)
