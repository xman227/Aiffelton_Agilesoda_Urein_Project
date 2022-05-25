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

## 5.25 일 기준 PATCH ✒️

### 🌏 환경

1. 보상   
move_reward = -1   
obs_reward = -10   
out_reward = -10   
goal_reward = 1000   
noitem_reward = -0.1 -> 추가.   
- 아이템이 없는곳을 장애물로 취급하는건 그 장소의 보상 점수를 깎는것이라 생각했고 그걸 줄이려고 추가.   

2. 레이어   
- Conv2d 채널 수를 16-32애서 6-16으로 줄여봄.   

3. 처음에만 위로 올라가는 것에서, [9,4]에 에이전트가 들어가면 무조건 위로 올라가도록 수정.   

4. 아이템의 순서를 없앴음.   

```python

```
