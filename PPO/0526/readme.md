## 오늘의 회고
### 하이퍼 파라미터
---
- move_reward = -0.1
- obs_reward = -0.2
- goal_reward = 50
- learning rate
- lr_actor = 0.0003
- lr_critic = 0.0005
- max episode len = 300
---
### 훈련 진행 사항
훈련이 대략 평균 리워드가 일정 이상에 가면 수렴하는 듯한 모습을 보여준다.<br>
그래서 시도해보고 싶은 사항은 
- learning rate 그때 그때 변하도록 부하를 주는 방법
- 완전 훈련을 더 많이 시켜보는 방법 (코랩으로 동시 진행)

local minima에 빠질 가능성이 있다라는 관련 자료를 봐서 현재로선 learning rate decay가 현 상황을 개선하는데 도움을 줄것 같다.

훈련 속도가 생각보다 빠르기 때문에 3억번 까지는 무리더라도 timestep을 1억까지는 도달해 보고 그래프로 비교해봐도 좋을 것 같다.
