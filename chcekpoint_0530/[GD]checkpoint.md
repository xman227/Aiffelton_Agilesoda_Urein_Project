# ✒️회고

### Content

#### 핵심 ISSUE

    1. 가상환경설정 
    2. Agent 코드 
    3. Sim 코드


## 🧩 핵심 ISSUE

### 1. 가상 환경 설정 🌏

`pyvirtualdisplay` 는 리눅스의 display 환경에서만 작동.
때문에 GCP 내부 jupyter notebook 에서  
특정 패키지 설치 후 agent 를 시각화 하였다.

우리가 구축한 가상환경의 순서는 다음과 같다.

1. GCP로 가상환경 구축  
- GCP에 접속해 인스턴스를 생성한다.
- 고정 IP 와 방화벽을 설정한다
- 아나콘다를 설치하고 가상환경을 구축한다.
- 쥬피터 노트북을 설정한다.

자세한 GCP 사용방법은 [링크](https://www.notion.so/GCP-e48565c2fe7c46c3888fbe28ccb3409b) 를 통해 확인할 수 있다.

2. display 모듈 설치  
리눅스 창에서   
다음의 display 관련 패키지를 설치한다.
- `sudo apt install xvfb`  
- `sudo apt install ffmpeg`  
- `sudo apt-get update`   
- `sudo apt-get install freeglut3-dev`  

3. jupyter open
다음의 명령어로 jupyter notebook 을 실행한다.
- `xvfb-run -a jupyter notebook`

### 2. Agent 코드 구축 😎

전체적으로 value based 코드인 

DQN 과

policy based 인

A2C, A3C, PPO 를 구축해 보았다.

DQN 은 해당 state 에서 Deterministic 한 결과를,

policy based 는 stochastic 한 결과를,

그 중에서도 특히 A3C 는 multi-processing 을 이용하고
PPO 는 clip 방법 과 GAE train 방법 개선을  통해 성능을 올렸다.

특히 CNN 도입에 있어서 
Atari 논문과 
한동대학교 학부생의 뱀게임 강화학습 프로젝트를 토대로 구상 중에 있다.

Atari 논문 : [여기](https://github.com/Neo-47/Atari-DQN/blob/master/Estimator.py)

뱀게임 코드 : [여기](https://github.com/choyi0521/snake-reinforcement-learning)



### 3. Sim 환경 구축

1. 아이템 Get
첫번째로 환경에서 아이템의 순서를 정해주었다. 다시말해 우리가 정해주는 아이템부터 먹어야 하는 상태.
두번째로는 순서 상관없이 모든 아이템을 먹을 수 있도록 바꿔주었다.  
그 방법이 경우의 수가 더 많이 생겨 모든 아이템을 먹는 경우를 학습할 수 있다고 판단했다.

2. 좌표값

처음에는 0과 1, 100과 150 으로 구성되어 있었다.
이것을 0~255의 흑백데이터라고 가정하고
길 1 , item : 150. 장애물 및 아이템이 없는 창고 : 50 으로 sclae up, 단순화 처리를 하였다.
원래는 0 에서 1 사이의 값을 정해주었지만, 소수점에서는 다양한 문제가 있어 재수정하였다.

3. 보상

첫번째로 모든 행동에 양수의 보상을 주었다.
두번째로 움직임은 -1. 장애물은 -10. 완수시 200의 보상을 주었다.

다만 보상을 받을 방법이 너무 적기 때문에 아이템의 보상값을 극단치로 올려보기도 하였지만  
크게 유의미하지 않았다.

세번째로는 모든 아이템을 먹었을 때 추가 보상으로 300 을 주었다.

4. 액션 제한

처음에는 액션 제한을 주지 않았지만, 
약 500 ~ 3000의 수를 두고 제한을 하고 있다.

action 수가 지정한 수만큼 넘었을 때, break 한다.

우리의 과제 상 수를 100 정도만 두어도 충분하다고 생각하지만,
실제 학습시에는 그렇지 않았음을 확인했다.

5. Episode 단일화

한번에 여러 경우의 수를 학습하는 것이 어려울까봐  
우선 1번 Epi 에 대해 학습한 뒤 그 파라미터로
나머지 train 데이터를 학습하는 것이 쉬울 것이라고 판단했다.

왜냐하면 마지막에 도착지로 돌아오는 과정 등 겹치는 지점이 많기 때문이다.

하지만 아직 유의미한 결과는 내고 있지 못하다.




## 🍼 기타 ISSUE

### 1. from string import `ascii_ string`

파이썬에서는 기본 알파벳이나 숫자 데이터 정도는 상수로 정의되어 있다.


```python
import string 

string.ascii_lowercase # 소문자 abcdefghijklmnopqrstuvwxyz
string.ascii_uppercase # 대문자 ABCDEFGHIJKLMNOPQRSTUVWXYZ
string.ascii_letters # 대소문자 모두 abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
string.digits # 숫자 0123456789


```




    '0123456789'



### 2. 다양한 배열 처리 오류

- `tensor(list)` 를 사용하면서 생긴 오류 :  
> expected sequence of length 90 at dim 1 (got 10)

리스트 안의 리스트들이 90개의 데이터를 가지고 있는데, 지금 받은 건 10개의 데이터밖에 없다는 의미였다.
`reshape()` 가 아닌 `flatten()` 함수를 이용해 차원을 축소해 해결하였다.

- `gather(1, list)` 를 사용하면서 생긴 오류 :  
> Expected dtype int64 for index  

gather 를  쓸 수 없는 타입이 list 에 들어있다는 뜻이다.

- `tensor(array)` 오류
> c:\Users\82102\Oha\Urien\project\Agent.py:42: UserWarning:   
Creating a tensor from a list of numpy.ndarrays is extremely slow.  
Please consider converting the list to a single numpy.ndarray with numpy.array() before converting to a tensor.  
(Triggered internally at  ..\torch\csrc\utils\tensor_new.cpp:210.)  

array 안에 arrray 형식이 2 개이상 있어 속도가 느려질 수 있다는 뜻이다. 예를 들어,  

`array = [[array([1, 2, 3, 4, 5]), array([1, 2, 3, 4, 5],[1,2,3,4,5])]`

이런식으로 리스트 안에 array 가 여러번 반복되면 tensor화에 좋지 않다.

이를 합쳐주기 위해서는  
`numpy.concatenate( array, axis=0 )`  
`numpy.stack( array, axis=0 )`  
등을 사용할 수 있다.


### 3. GPU 사용 오류

강화학습 시에는 많은 Epi 시행착오 끝에 훌륭한 Agent 를 만들어낸다.  
때문에 학습 시의 GPU 사용이 권장되는데, GPU 사용 시에 사용하는

`.to(devise)` 메서드 사용 중 오류가 발생했다.
> 1. Input type (torch.cuda.FloatTensor) and weight type (torch.FloatTensor) should be the same

이 문제를 해결하기 위해서는 '모델' 과 'input data' 두 종류에 cuda 처리를 해야 한다.

![image.png](attachment:image.png)

![image-2.png](attachment:image-2.png)

> 2. Expected all tensors to be on the same device, but found at least two devices, cuda:0 and cpu! (when checking argument for argument index in method wrapper_gather)

>3. 'float' object has no attribute 'to'

이 외에도 위와 같은 오류가 떴는데, 이는 우리의 네트워크를 학습시킬 때,  
파라미터와 함께 reward, gamma 같은 실수값을 이용하기 때문이다. 

Gpu 에 저장된 cuda.tensor 데이터와 cpu에 저장된 float 데이터를 연산할 수는 없다.  
때문에 우리가 이용할 float 데이터도 cuda.tensor 로 변환시켜주어야 한다.

![image-3.png](attachment:image-3.png)



사진을 보면, 우리가 학습에 이용하는  
a, r, gamma, done_mask 를 모두 cuda.tensor 화 시켰다.


```python

```
