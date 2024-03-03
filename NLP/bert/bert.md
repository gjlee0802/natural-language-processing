# BERT(Bidirectional Encoder Representations from Transformers)
## Introduction
- 사전 훈련 언어 모델이며, 총 3.3억개 단어의 Corpus를 이용하여 학습시킨 모델

- BERT-base, BERT-large 두가지 버전이 존재함.
~~~
L : (Transformer의 블록 숫자)
H : (hidden size)
A : (Transformer의 Attention block 숫자)
를 의미함.

BERT-base는 (L=12, H=768, A=12)로 구성됨.
BERT-large는 (L=24, H=1024, A=16)로 구성됨

BERT-large의 파라미터 값이 더 큼.
은닉층이 크고 Attention 개수를 많이 사용함.

base는 1.1억개 학습 파라미터, 
large는 3.3억개 학습 파라미터 사용함.
~~~

## Input
Token Embedding + Segment Embedding + Position Embedding

BERT는 세가지 임베딩을 합치고 Layer 정규화와 Dropout을 적용하여 입력으로 사용함.  

아래 3가지 임베딩 값의 합으로 구성됨.
- Token Embedding
- Segment Embedding
- Position Embedding


### Token Embedding

- Word piece 임베딩 방식을 사용함.
- 자주 등장하면서 가장 긴 길이의 sub-word를 하나의 단위로 만듦.
- 자주 등장하지 않는 단어는 더 작은 sub-word로 쪼개어짐.
- 이는 이전에 자주 등장하지 않은 단어를 모두 Out-of-Vocabulary(OOV), UNK로 처리하여 모델링의 성능을 저하했던 문제를 해결할 수 있음.
- 입력받는 모든 문장의 시작으로 CLS 토큰이 주어짐.
- CLS 토큰은 입력되는 시퀀스 데이터의 시작을 알려주는 역할을 하며, 시퀀스 전체의 정보를 반영함.
- SEP 토큰은 두개의 시퀀스가 입력되었을 때, 문장을 구분하는 역할을 하며, 문장의 끝에 SEP 토큰을 사용함.

### Segment Embedding
- 토큰화한 단어들을 다시 하나의 문장으로 만들고, 첫번째 SEP 토큰까지는 0으로 만들고, 그 이후의 SEP 토큰까지는 1값으로 MASK를 만들어 각 문장들을 구분함.
~~~
"I love her." "I hate him." 두 문장의 Input이 주어졌을 때,

둘을 결합하고, SEP토큰을 기준으로 각 문장들이 구분되기 위해 MASK(0과 1로 구성)를 만들면 아래와 같다.

<CLS> I love her . <SEP> I hate him .
  0   0  0    0  0   0   1  1    1  1
~~~

### Position Embedding


## 참고 자료
- https://happy-obok.tistory.com/23
- https://yeong-jin-data-blog.tistory.com/entry/Transfomer-BERT
- https://velog.io/@jochedda/NLP-BERT-%EA%B0%9C%EB%85%90-%EC%A0%95%EB%A6%AC
- OOV 문제: https://f7project.tistory.com/286