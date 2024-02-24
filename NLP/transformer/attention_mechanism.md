# Attention Mechanism

## Attention function
~~~
Attention(Q, K, V) = Attention Value
~~~
- 어텐션 함수는 주어진 '쿼리(Query)'에 대해서 모든 '키(Key)'와의 유사도를 각각 구한다.
- 구해낸 이 유사도를 '키(Key)'와 맵핑되어 있는 각각의 '값(Value)'에 반영해준다.
- 유사도가 반영된 '값(Value)'들을 모두 더해서 리턴한다. 이를 '어텐션 값(Attention Value)' 혹은 '문맥 벡터(Context Vector)'으로 부른다.
~~~
Q = Query : t 시점의 디코더 셀에서의 은닉 상태
K = Keys : 모든 시점의 인코더 셀의 은닉 상태들
V = Values : 모든 시점의 인코더 셀의 은닉 상태들
~~~

## Dot-Product Attention
1. 어텐션 스코어(Attention Score)를 구한다.
2. 소프트맥스(Softmax)를 통해 '어텐션 분포(Attention Distribution)'를 구한다.
3. 각 인코더(각 단어)의 **어텐션 가중치**와 **은닉 상태**를 **가중합**하여 '**어텐션 값(Attention Value, Context Vector)**'을 구한다.
4. '어텐션 값(문맥 벡터)'과 디코더의 t 시점의 은닉 상태를 연결(Concatenate)한다.
5. 출력층 연산의 입력이 되는 St를 계산한다.
6. St를 출력층의 입력으로 사용한다.

## 다양한 종류의 Attention

- dot
- scaled dot
- general
- concat
- location-base
