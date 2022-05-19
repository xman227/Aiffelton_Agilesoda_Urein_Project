## 오늘의 회고

1. 훈련도중에 발생하는 /runtimeerror: function 'softmaxbackward0' returned nan values in its 0th output./ 에러 수정
  - 곱연산이 되는 부분에 1e9를 더함으로 해결
2. 장애물에 부딪혔을때 Agent가 죽는 경우와 안죽는 경우 비교(아직 좀 더 훈련 및 비교해볼 필요가 있습니다.)
3. 현재 최단 경로가 아니라 빙글빙글 도는 등의 이상 행동을 잡아야하는데 이유를 찾아야합니다.
