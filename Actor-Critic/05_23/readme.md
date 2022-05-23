## 오늘의 회고
1. 주말동안 훈련을 시켜봤는데 움직임에 큰 변화가 없어서 오늘은 다시 시작한다는 생각으로 epi 1의 화물 리스트로만 훈련을 시켜봤습니다.
  - 하나의 에피소드도 훈련이 제대로 안된다는 결론이 나왔습니다.
2. 의문점
  - 신경망이 cnn 구조와 linear 구조중 어떤걸 사용하는 게 더 나을지? (현재 돌려본 결과로는 두 모델이 거의 유사하다.)
  - 보상의 문제인건지? (보상의 파라미터값 조정이 모델의 움직임에 영향을 줄지?)
  - 스텝당 reward의 값을 키울경우 더 유의미 한 값이 나올 수 있는건지...?
  - 훈련량의 문제인건지 근본적인 모델링의 문제인건지? (10000걸음을 걸어야 하는데 100걸음 째인건지 혹은 길의 방향이 틀려서 모델이 어려움을 겪고 있는건지?)

## CNN
![](https://github.com/youngchurl/Aiffelton_Agilesoda_Urein_Project/blob/main/Actor-Critic/05_23/conv.gif?raw=true)

## Linear
![](https://github.com/youngchurl/Aiffelton_Agilesoda_Urein_Project/blob/main/Actor-Critic/05_23/linear.gif?raw=true)
