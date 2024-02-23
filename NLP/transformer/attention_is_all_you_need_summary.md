# Transformer 요약

### Transformer 이전 RNN을 이용한 Seq2Seq의 문제점
- 병렬화 문제: RNN(LSTM)을 사용하여 순차적으로 입력을 처리해야 하는 구조이기 때문에 병렬화가 불가능했음.
- Long Distance Dependency: 참조 윈도우의 크기가 고정되어 있었기 때문에 시퀀스에서 멀리 떨어진 시퀀스에서 멀리 떨어진 항목들 간의 관계성은 기울기 소실/폭증 문제가 있음.

### Transformer, Self Attention 
- Transformer: RNN 같은 순환신경망 없이 Attention만으로 이루어진 인코더-디코더 구조의 Seq2Seq 모델, 연산 효율(병렬 계산 가능)과 성능이 좋다.
- Attention: 모델의 성능 향상을 위해 문맥에 따라 집중할 단어를 결정하는 방식.
- Self Attention: Attention중에서 자기 자신에게 Attention 메커니즘을 행하는 방식. (Query, Key,  Value 시작 값이 같음)

### Query, Key, Value
- Query: 입력 시퀀스에서 관련된 부분을 찾으려고 하는 정보 벡터
- Key: 관계의 연관도를 결정하기 위해 query와 비교하는데 사용되는 벡터
- Value: 특정 key에 해당하는 입력 시퀀스 정보로 가중치를 구하는데 사용되는 벡터
- Query와 Key 사이의 유사성을 계산하기 위해 **코사인 유사도**를 구하는 방법을 사용.

### Personal Encoding
- RNN(LSTM) 구조에서는 입력이 자연스럽게 순서대로 모델에 입력되었으나, 어텐션 연산에서는 순서 정보가 고려되지 않음.
- 입력 임베딩에 Positional Encoding이라 불리는 입력 임베딩과 같은 차원의 위치 정보를 담는 벡터를 더해줌.

### Self Attention
- 원하는 문장을 임베디하고 학습을 통해 Query, Key, Value에 맞는 가중치들을 구해줌.
- 각 단어의 임베딩의 Query, Key, Value와 가중치를 점곱 계산(내적)하여 최종 Q, K, V를 구함.
- Query, Key, Value의 시작 값(기원)은 같으나 최종 값은 학습을 통해 달라짐.
- Attention score 공식을 통해 각 단어별 Self Attention value를 도출함.
- Self Attention value의 내부를 비교하면서 상관관계가 높은 단어들을 도출함.

### Multi-head Attention
- Query, Key, Value 값을 한번에 계산하지 않고 head 수만큼 나눠 계산 후, 나중에 Attention Value들을 합치는 메커니즘. (분할 계산 후 합산)
- head의 수만큼 Attention을 각각 병렬로 나누어 계산하여 각각 Attention value들을 도출.
- 도출된 Attention value들은 마지막에 concatenate를 통해 하나로 합쳐서 최종 Attention value 도출
- 사람들이 회의를 하듯이 여러 부분에서 도출돼 결과를 통해 정보를 상호 보완하여 Multi-head Attention 메커니즘 성능이 좋음.

### 참조
- https://velog.io/@jhbale11/%EC%96%B4%ED%85%90%EC%85%98-%EB%A7%A4%EC%BB%A4%EB%8B%88%EC%A6%98Attention-Mechanism%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80

