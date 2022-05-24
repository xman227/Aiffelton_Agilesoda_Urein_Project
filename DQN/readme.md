## 5.24 일 기준 PATCH ✒️

### 🌏 환경

1. 보상 : move : -1 obstacle : -2 items : 1000
2. 에이전트 : 0.3 아이템 : 0.6
3. 아이템이 당장 목표 한 개씩만 나오는 형태 (마지막 반환지까지 표현)

### 😗 에이전트


1. 하이퍼 파라미터  
- learning_rate = 0.0005
- gamma = 0.99
- buffer_limit  = 50000
- batch_size = 32
- interval = 50
- a_step = 300
- buffer_size > 4000: train

2. 레이어
- Conv2d 레이어 2계층의 CNN 사용 (Atari reinforcement 논문 참고)


```python

```
