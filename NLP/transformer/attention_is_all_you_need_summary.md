# Transformer 요약
### Transformer, Self Attention 
- Transformer: RNN 같은 순환신경망 없이 Attention만으로 이루어진 인코더-디코더 구조의 Seq2Seq 모델, 연산 효율(병렬 계산 가능)과 성능이 좋다.
- Attention: 모델의 성능 향상을 위해 문맥에 따라 집중할 단어를 결정하는 방식.
- Self Attention: Attention중에서 자기 자신에게 Attention 메커니즘을 행하는 방식. (Query, Key,  Value 시작 값이 같음)


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
- 