# 이진 트리, 순회, 이진 탐색 트리
## Tree의 특징
1. 가장 위의 node는 root node
2. 각 노드들은 edge로 연결되어 있다.
3. 루트노드에서 각 노드까지의 경로는 유일하다.
4. 자식이 없으면 leaf node라고 한다.
5. 차수(degree)는 노드에서 아래로 향하는 간선의 갯수이다.

## 이진 트리의 특징
1. 이진 트리는 노드의 최대 차수가 2를 넘지 않는 트리이다. 즉, 각 노드에 대한 간선이 최대 2개이다.
2. 배열이나 포인터로 만들 수 있다.
3. 배열로 만들 경우 다음의 규칙을 따른다.
    - 루트 노드가 인덱스 1번이면
        - 왼쪽 자식 노드는 부모 노드 인덱스의 *2
        - 오른쪽 자식 노드는 부모 노드 인덱스의 *2 + 1
    - 루트 노드가 인덱스 0번이면
        - 왼쪽 자식 노드는 부모 노드 인덱스의 *2 + 1
        - 오른쪽 자식 노드는 부모 노드 인덱스의 *2 + 2
4. 배열로 만든 경우에는 메모리에 빈 자리가 많고, 노드 갯수가 N개이면 O(N)을 가진다.
5. 이진 트리의 순회는 다음의 3가지 방법이 있다.
    - 전위 순회(preorder): 부모 노드를 방문한 다음 왼쪽 노드를 모두 방문하고 다시 아래서부터 올라가면서 오른쪽 노드를 방문 한다. (부모 - 왼쪽 - 오른쪽)
    - 중위 순회(inorder): 부모 노드에서부터 왼쪽 노드로 쭉간다. 이때 방문하지 않고 왼쪽 노드로 쭉 간다음 leaf node에 다다르면 방문하고, 부모 노드, 오른쪽 노드 순서로 방문 한다. (왼쪽 - 부모 - 오른쪽)
    - 후위 순회(postorder): 부모 노드에서부터 왼쪽으로 쭉간다. 단, 방문하지 않고 왼쪽 노드로 쭉 간다음 leaf node에 다다르면 방문하고, 오른쪽 노드, 부모 노드 순서로 방문 한다. (왼쪽 - 오른쪽 - 부모)
6. 조심해야할 것은 전위 순회는 바로 노드에서 방문하지만, 중위 순회와 후위 순회는 방문하지 않고 거쳐간다는 특성이 있다는 것이다.

## 이진 탐색 트리의 특징
1. 데이터를 미리 잘 정리해놓으면, 검색하기 편하다는 특징을 이용
2. 부모 기준으로 왼쪽은 나보다 작은 노드, 오른쪽은 나보다 큰 노드이다.
3. 이진 탐색 트리의 탐색
    - 찾으려는 값이 현재 노드의 값과 같으면 탐색 종료, 크면 오른쪽 노드를 탐색
    - 본인이 찾으려는 값이 현재 노드의 값보다 작으면 왼쪽 노드를 탐색
    - 값을 찾으면 종료, 노드가 없을 때까지 계속 탐색했는데 값이 없으면 현재 트리에 값이 없는 것
4. 이진 탐색 트리의 삽입과 탐색은 O(logN)이 평균적으로 걸리지만, 만약 균형이 맞지 않으면 O(N)이 걸린다. 
5. 균형 이진 탐색 트리로 AVL 트리, red-black 트리가 있다.

## 3. 예상 대진표
홀수라면 = a/2 + 1  
찍수라면 = a/2  
같아지면 정답  

## 4. 다단계 칫솔 판매
트리를 구성하되, 나누면 0이 되는 순간 다단계 업데이트 종료를 해야한다. 안하면 시간초과

## 5. 미로 탈출
1. 시작 -> 레버
2. 레버 -> 목적지

두 번의 BFS를 돌리면 된다. 

## 6. 양과 늑대
늑대가 더 많거나 같은 경우만 빼고, 모두 순회한다. 각 노드에 대한 재귀로 방문, 방문하지 않음 상태가 있음으로 2^17 가지 경우의 수가 있다. 

우아하게 풀 수 있는 방법이 있는 줄 알고 괜히 고민...

## 7. 길 찾기 게임
1. y축으로 정렬해서 맨 위에 있다면 root node이다.
2. root node의 x축 기준으로 왼쪽, 오른쪽을 나눈다.
3. 왼쪽 node 중에 y축이 가장 높은 것 중에 x축이 가장 큰 값이 root node의 왼쪽 node이다.
4. 오른쪽 node 중에 y축이 가장 높은 것 중에 x축이 가장 작은 값이 root node의 오른쪽 node이다.
5. root node를 후보에서 제거하고, 각 child node에 대해 같은 연산을 반복해준다.

python은 재귀 호출 횟수가 기본적으로 1000이기 때문에 재귀 횟수를 늘려주지 않으면 런타임 에러가 발생한다. ~~이것 때문에 한 시간 날림~~
```py
import sys
sys.setrecursionlimit(10**6)
```