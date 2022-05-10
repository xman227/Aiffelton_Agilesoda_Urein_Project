# [ Agile Soda : Urein 🐳]

## Urein 
- **울산 + 인천**
- **우린 잘할 수 있다!!!!**
- **rein**forcement **(강화학습)의 앞자를 땄습니다.**

## 🤔 who is Urein  우린 누구냐면..

| Name  |E.T.|Github  |
| :------------ |:---------------:| :-----|
| 박준희      |Team Leader |https://github.com/phthys |
| 정문희      || https://github.com/flowerJung |
| 이광민      || https://github.com/kwang-min-lee1 |
| 김영철      || https://github.com/youngchurl |
| 하성민      || https://github.com/xman227 |

## ✈️Study for here 

[바닥부터 시작하는 강화학습](https://github.com/seungeunrho/RLfrombasics)

## Notion Page
[우린(Urein)](https://www.notion.so/Urein-54f86ceb881b40879de67cd29f2f7d13)



## 🤔프로젝트 상세 설명

### 👨‍🎓 About baseline code

10행 9열로 된 grid 환경

1. 아이템이 최대7개

2. 액션은 a 앞에서 a 안으로 들어가서 a를 잡고 a를 나오는 것으로 한다.

3. 정해진 주황색 원에서만 뽑을 수 있도록 한다.

4. 멈춤. 좌우상하 액션이 가능하다.

5. train, test 데이터들은 같은 item 이 중복되지 않는다.

6. simulation 코드 사용 가능 (이하 sim 코드라 한다.)

### ✈️ Sim 코드 설명

#### 변수 설명

`inds` : a~q 아이템 리스트

csv 에 나온 아이템 리스트의 위치좌표에만 -100 을 한다.

`reset()` : 9행 4열로 start 지점으로 이동하고 장애물과 아이템 초기화

`apply_action`  : 액션한 곳으로 에이전트의 위치 변경

0123 각각 상 하 좌 우 로 구분된다.

`get_reward` : 상황에따라서 액션을 옳게 했는지 판단하는 지표  
**리워드 식을 변경할 필요가 있다.**

#### `step()`

위에서 나온 모든 함수가 step 에서 사용이 된다.

`local_target()` : 지금 당장 가야할 곳은 가장 앞에 타겟  
그래서 local_target[0] 부터 시작한다.

`cur` : current 현재 위치

`done()` :  으로 에피를 끝낼건지 말건지 정함 True 면 끝났다
끝났을 때 아이템도 챙기고 무사히 도착하면 gif 로 그것을 볼 수 있음

지금은 에이전트가 없고
epi range(2) 로 하고 있는데 
여기 그냥 한바퀴 돈 설정만 해놓았다. 때문에 
**우리가 무조건 바꾸어야 하는 부분이다.**

---

7. 학습이 잘 됐는지 확인하는 지표 3가지, 경로탐색 알고리즘과의 비교를 한다.

8. 이후 최종 결과 보고서 작성

### ++ 추가로..
노트북에서도 충분히 트레이닝 가능하다.
baseline 이기 때문에 최소한의 조치만 해둔 상태이다.

우리는 환경에 대한 고민을 많이 해야 한다.
환경의 제약조건은 우리가 변경할 수 있다.

## 👨‍🎓 이러한 내용을 바탕으로 우리가 할 일은??

0. 코드 이해

- Sim 코드가 어떻게 구성되어 있는지 이해 및 토론

1. 환경 설정

- 어떻게 train, test 데이터를 받아올 것인지.
- reward 를 어떻게 설정할 것인지.

2. Agent 설정

- 어떤 알고리즘을 따를 것인지
- 어떻게 코드를 구현할 것인지

(추후)

3. 비교 알고리즘 설정

- 다익스트라, A star 의 알고리즘으로과의 성능 비교

4. 프로젝트 심화(방식 미정)

## 👨‍👩‍👧‍👦 우리들의 Git Flow

### ⚡ 구성요소
1. main branch (실제 프로젝트. 계속 남아있음)
2. develop branch (다음 업데이트 버전을 개발)

develop bracnh 를 업데이트 하여 main branch 를 관리한다.

### 🐳 방법

1. 원본 소스를 Fork
2. 각자 개인 branch 에서 작업 및 코드 수정
3. Pull request 후 내용 공유
4. 팀장(박준희) 검토 후 commit. 논의가 필요한 내용은 토의.
5. Fetch
