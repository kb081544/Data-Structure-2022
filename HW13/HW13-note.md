알고리즘
========
### 분할/정복
1. Greedy
  - 다익스트라
  - 좋아보이는 알고리즘 사용
2. 영토 확장/visited
  - 근처부터 하나씩 정복해 나가가는 컨셉
3. Relax
  - Bellman-ford
  - 차근차근 알아가며 정보를 알게 되므로 Relax를 시켜줌

### 다익스트라
 > V(Vertex, 정점, <V1, V2,...,Vi>), E(path의 경로, (Vi, Vi+1), W(가중치(Vi, Vi+1, Wi,i+1)), 가중치의 값이 최소가 되도록
 > Shortest Path
 > Longest Path: undefined
 >  > Weight를 음수로 바꾸는 것이 불가
 >  > __Negative Cycle__ : 돌면 돌 수록 최소값이 계속 업데이트됨
 >  > Shortest Path: undefined
 >  > Negative Weight이 있으면 다익스트라, 또는 벨만포드로도 구할 수 없음
### 벨만 포드
 > Relax 사용, 알아나가는 것을 Relax라고 함
 > 그래프를 __충분히 Relax__ 를 해주면(알아나가면) __결과__ 를 알아나갈 수 있음
 > 맞는지 __결과를 확인__ 하는 과정이 필요.

### Shortest Path, Negative Cycle
 > Weight를 음수로 바꾸면 순환할 때 마다 값이 바뀜
 > > __Negative Cycle__ : 돌면 돌 수록 최소값이 계속 업데이트됨
 > > Shortest Path: undefined
 > > Negative Cycle이 있으면 벨만포드로도 구할 수 없음
 > 기본적인 동작 방법
 > > 1. 모든 정점까지의 거리를 INF로 둠, 갈 수 있는 방법도 없음, 시작 정점의 거리는 0
 > > 2. select edge -> Relax
 > > > __Dijkstra(greedy)__ : 기존에 알고있던 거리(d[v])>새로 알게 된 거리(d[u]+w(u, v)); d[v]<-d[u]+w(u,v);
 > > > __Bellman-Ford__ : 정점 개수 V에 따라  for 문을 돌림(정점을 충분히 찾음) -> 모든 간선들에 대해 relax 시켜줌. Negatice Cycle 확인 필요.
#### Exmaple
||A|B|C|D|E|
|:---:|:---:|:---:|:---:|:---:|:---:|
|init(i)|0|INF|INF|INF|INF|
|i=0|0|-1|-4|INF|INF|
|i=1|0|-1|2|-1|2|
|i=1|0|-1|2|-2|1|
|i=2||||||
|i=3||||||
|i=4||||||
- 계속해서 업데이트 시켜서 충분히 찾아보면 정답이 나옴
- 간선 (u,v)에서 d[v]>d[u]+w(u,v) 정점을 한번더 봤더니 여전히 더 좋은 곳이 있다는 것을 확인함
- - negative cycle exists
- - Report Undifined

풀고자 하는 문제의 효과
1. 유형효과: 계산 가능한 값을 근거로 한 효과(ex: 그동안의 손실 얼마, 피해 얼마, 개발비용 얼마 등)
3. 무형효과: 계산 불가능한 효과(ex: 대안 마련, 국제적 위상 강화, 사업 확장 기대)

문제: END에 도달했을 때의 베터리 잔량을 최대로 남겨라. 
입력 예시
3
SE -10
SE -8
S -6
E -10
S 20
E -1
NE 5
|:---:|:---:|:---:|
|-10 down ->|-8 down ->|-6 down|
|+7 down |-10->|+20 down|
|-1 ->|+5 up ->|END|
3x3 matrix
방향이 있는 그래프로 구현가능
다익스트라나 벨만포드를 이용해 weight의 총합을 두면 됨
+를 -로, -를 +로 해서 배터리를 최소로 남기는 식으로 배운 것을 활용하면 반대인 최대값을 구할 수 있음
각 셀들을 정점으로 두고, 방향이 있는 간선을 추가. 배터리가 충전되거나 소모되는 양은 간선의 weight로 두면 됨
[알고리즘 공부 책 링크](https://sd.blackball.lv/library/Introduction_to_Algorithms_Third_Edition_(2009).pdf)
