## :memo: 알고리즘

- 유한한 단계를 통해 문제를 해결하기 위한 절차나 방법
- 컴퓨터가 어떤 일을 수행하기 위한 단계적 방법
- 문제를 해결하기 위한 절차



#### <좋은 알고리즘>

① 정확성  ② 작업량(적은 연산)  ③ 메모리 사용량  ④ 단순성  ⑤ 최적성



#### <시간 복잡도(Time Complexity)>

- 실제 걸리는 시간을 측정 
- 실행되는 명령문의 개수를 계산
- 빅-오(O)(Big-Oh Notation) 표기법
  - 시간 복잡도 함수 중에서 가장 큰 영향력을 주는 n에 대한 항만을 표시
  - 계수(Coefficient)는 생략하여 표기
  - O(1) < O(logn) < O(n) < O(nlogn) < O(n^2) < O(2^n) < O(n!)



------

## 1. 1차원 배열

`Arr = list()` `Arr = []` `Arr = [1, 2, 3]` `Arr = [0] * 10`



#### <정렬>

- 버블 정렬 (Bubble Sort)

  - 인접한 두 개의 원소를 비교하며 자리를 계속 교환하는 방식
  - 첫 번째 원소부터 인접한 원소끼리 계속 자리를 교환하면서 맨 마지막 자리까지 이동
  - 한 단계가 끝나면 가장 큰 원소가 마지막 자리로 정렬
  - O(n**2)

  ```
  def BubbleSort(a, N):  # 정렬할 List, N 원소 수
  	for i in range(N-1, 0, -1):  # 범위의 끝 위치
  		for j in range(0, i):
  			# 왼쪽 원소가 더 크면 오른쪽 원소와 교환
  			if a[j] > a[j+1]:
  				a[j], a[j+1] = a[j+1], a[j]
  ```

  

- 카운팅 정렬 (Counting Sort)

  - 집합에 각 항목이 몇 개 씩 있는지 세는 작업을 하여, 선형 시간에 정렬하는 효율적인 알고리즘
  - 정수나 정수로 표현할 수 있는 자료에 대해서만 적용 가능
  - 충분한 공간을 할당하려면 집합 내의 가장 큰 정수를 알아야 한다.
  - O(n + k) : n = 리스트의 길이, k = 정수의 최대값

  ```
  def Counting_Sor(A, B, k)
  # A [] -- 입력배열(1 to k)
  # B [] -- 정렬된 배열
  # C [] -- 카운트 배열
  
  	C = [0] * (k + 1)
  	
  	for i in range (0, len(A)):
  		C[A[i]] += 1
  	
  	for i in range (1, len(C)):
  		C[i] += C[i-1]
  	
  	for i in range (len(B)-1, -1. -1):
  		C[A[i]] -= 1
  		B[C[A[i]]] = A[i]
  ```

  

- 선택 정렬 (Selection Sort)

- 퀵 정렬 (Quick Sort)

- 삽입 정렬 (Insertion Sort)

- 병합 정렬 (Merge Sort)



#### <완전 검색>

- 모든 경우의 수를 나열해보고 확인
- Brute-fore / generate-and-test
- 경우의 수가 상대적으로 작을 때
- 수행속도 느림
- 순열 : 서로 다른 것들 중 몇개를 뽑아서 한줄로 나열하는 것 [nPr]



#### <탐욕(Greedy) 알고리즘>

- 최적해 구하기
- 여러 경우 중 하나를 결정해야 할 때마다 그 순간에 최적이라고 생각되는 것을 선택해 나가는 방식

<탐욕 알고리즘 동작 과정>

1. 해 선택
2. 실행 가능성 검사
3. 해 검사



------

## 2. 2차원 배열

1. ##### 2차원 배열의 선언

   ```
   N = int(input())
   arr = [list(map(int, input().split())) for _ in range(N)]
   ```

   

2. ##### 행 우선 순회

   ```
   # i 행의 좌표
   # j 열의 좌표
   
   for i in range(n):
   	for j in range(m):
   		Array[i][j]
   ```

   

3. ##### 열 우선 순회

   ```
   # i 행의 좌표
   # j 열의 좌표
   
   for j in range(m):
   	for i in range(n):
   		Array[i][j]
   ```

   

4. ##### 지그재그 순회

   ```
   # i 행의 좌표
   # j 열의 좌표
   
   for i in range(n):
   	for j in range(m):
   		# i%2 - > 짝수행 : 0, 홀수행 : 1
   		Array[i][j + (m-1-2*j) * (i%2)]  # 짝수행 : j + 0, 홀수행 : m-1-j
   ```

   

5. ##### 델타를 이용한 2차 배열 탐색

   - `arr[i][j]` : `arr[i-1][j]` `arr[i+1][j]`  `arr[i][j-1]`  `arr[i][j+1]` (상하좌우) 

   ```
   arr[0...N-1][0...N-1]  # N*N 배열
   
   # 우하좌상
   di = [0, 1, 0, -1]
   dj = [1, 0, -1, 0]
   
   for i in range(N):
   	for j in range(M):
           for k in range(4):
               ni = i + di[k]
               nj = j + dj[k]
   
               if 0 <= ni < N and 0 <= nj < M:
                   arr[ni][nj]
   ```

   ```
   for i in range(n):
   	for j in range(m):
           for di, dj in[(0,1), (1,0), (0,-1), (-1,0)]:
               ni = i + di
               nj = j + dj
   
               if 0 <= ni < N and 0 <= nj < M:
                   arr[ni][nj]
   ```

   

6. ##### 전치 행렬

   ```
   # i : 행의 좌표, len(arr)
   # j : 열의 좌표, len(arr[0])
   
   arr = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]  # 3*3 행렬
   
   for i in range(N):
   	for j in range(N):
   		if i < j:
   			arr[i][j], arr[j],[i] = arr[j][i], arr[i][j]
   ```

------

#### <부분집합>

- ##### 재귀함수

  ```
  bit = [0, 0, 0, 0]
  
  for i in range(2):
  	bit[0] = i  # 0번째 원소
  	for j in range(2):
  		bit[1] = j  # 1번째 원소
  		for k in range(2):
  			bit[2] = k  # 2번째 원소
  			for l in range(2):
  				bit[3] = 1  # 3번째 원소
  				print_subset(bit)  # 생성된 부분집합 출력
  ```

  ------

- ##### 비트 연산자

  ```
  & : 비트 단위로 AND 연산을 한다.
   : 비트 단위로 OR 연산을 한다.
  << : 피연산자의 비트 열을 왼쪽으로 이동시킨다.
  >> : 피연산자의 비트 열을 오른쪽으로 이동시킨다.
  ```

  - << 연산자
    - 1 << n : 원소가 n개일 경우 모든 부분집합의 수를 의미

  - & 연산자
    - i & (1 << j) : 번째 비트가 1인지 아닌지를 검사

  ```
  arr = [3, 5, 7, 1, 5, 4]
  
  n = len(arr)  # n : 원소의 개수
  
  for i in range(1<<n):
  	for j in range(n):
  		if i & (1<<j):
  			print(arr[j], end=", ")
  	print()
  print()
  ```

------

#### <검색>

- 순차 검색

- 이진 검색 - 자료가 정렬된 상태

  ```
  def dinarySearch(a, N, key):
  	start = 0
  	end = N-1
  	while start <= end:
  		middle = (start + end) // 2
  		if a[middle] == key:
  			return True
  		elif a[middle] > key
  			end = middle -1
  		else:
  			start = middle + 1
  	return False
  ```

#### <인덱스>

- 선택 정렬(Selection Sort)

  ```
  def selectionSort(a, N):
  	for i in range(N-1):
  		minIdx = i
  		for j in rnage(i+1, N):
  			if a[minIdx] > a[j]
  				minIdx = j
  		a[i], a[minIdx] = a[minIdx], a[i]
  ```

  


------

## 3. 문자열(String)

- ASCII(American Standard Code for Information Interchange)
  - 7bit 인코딩 : 128문자 표현 (33개 출력 불가 + 95개 출력 가능)



1. **고지식한 패턴 검색**
   - 본문 문자열을 처음부터 끝까지 차례대로 순회하면서 패턴 내의 문자들을 일일이 비교하는 방식

``` 
p = "is"  # 찾을 패턴
t = "This is a book~!"  # 전체 텍스트
M = len(p)  # 찾을 패턴의 길이
N = len(t)  # 전체 텍스트의 길이

def BruteForce(p, t):
	i = 0  # t의 인덱스
	j = 0  # p의 인덱스
	while j < M and i < N:
		if t[i] != p[j]:
			i = i - j
			j = -1
		i = i + 1
		j = j + 1
	if j == M:
		return i - M  # 검색 성공
	else:
		return -1  # 검색 실패 
```

```
def BruteForce2(p, t):
    M = len(p)  # 찾을 패턴의 길이
    N = len(t)  # 전체 텍스트의 길이
    for i in range(N-M+1):
        for j in range(M):
            if t[i] != p[j]:
                break
            else:
                i += 1
                j += 1
        if j == M:
            return i - M
    else:
        return -1
```



2. **KMP 알고리즘**
   - 불일치가 발생한 텍스트 스트링의 앞 부분에 대하여 다시 비교하지 않고 매칭을 수행

```
def kmp(t, p):
	N = len(t)
	M = len(p)
	lps = [0] * (M + 1)
	
	j = 0  # 일치할 개수 = 비교할 패턴 위치
	lps[0] = -1
	for i in range(1, M):
		lps[i] = j
		if p[i] == p[j]:
			j += 1
		else:
			j = 0
	lps[M] = j 
	
	i = 0  # 비교할 텍스트 위치
	j = 0  # 비교할 패턴 위치
	while i < N and j <= M:
		if j == -1 or t[i] == p[j]:
			i += 1
			j += 1
		else:  # 불일치
			j = lps[j]
		if j == M:  # 패턴을 찾을 경우
			print(i-M, end = ' ')  # 패턴의 인덱스 출력
			j = lps[j]  # 다음패턴을 찾기 위함
	print()
	return
```

```
        if j == M:  # 패턴을 찾을 경우
            answer_list.append(str(i - M))  # 패턴의 인덱스 LIST
            j = lps[j]  # 다음패턴을 찾기 위함

    return ' '.join(answer_list)
```



3. **보이어-무어 알고리즘**
   - 오른쪽에서 왼쪽으로 비교
   - 패턴 오른쪽 끝에 있는 문자가 불일치하고 이 문자가 패턴 내에 존재하지 않는 경우, 패턴의 길이만큼 이동



------

## 4. 스택(Stack)

- **push** : 삽입

  ```
  def push(item):
  	s.append(item)
  ```

  ```
  def push(item, size):
  	global top
  	top += 1
  	if top == size:
  		pirnt('overflow!')
  	else:
  		stack[top] = item
  		
  size = 10
  stack = [0] * size
  top = -1
  
  push(10, size)
  top += 1         # push(20)
  stack[top] = 20  #
  ```

- **pop** : 삭제(자료의 역순)

  ```
  def pop():
  	if len(s) == 0:
  		return
  	else:
  		return s.pop(-1)
  ```

  ```
  def pop():
  	global top
  	if top == -1:
  		print('underflow')
  		return 0
  	else:
  		top -= 1
  		return stack[top+1]
  
  print(pop())
  
  if top > -1:
  	top -= 1
  	print(stack[top])
  ```

- **isEmpty** : 스택이 공백이지 아닌지 확인

- **peek** : 스택의 top에 있는 item(원소)을 반환



1. **DFS 알고리즘**

   - 시작 정점 v를 결정하여 방문
   - 정점 v에 인접한 정점 중에서 ① 방문하지 않은 정점 w가 있으면, 정점 v를 스택에 push하고 정점 w를 방문 ② 방문하지 않은 정점이 없으면, 탐색의 방향을 바꾸기 위해서 스택을 pop하여 받은 가장 마지막 방문 정점을 v로 하여 다시 반복
   - 스택이 공백이 될 때까지 반복

   ```
   def dfs(v):
       global visited
       stack = [v]                 # dfs의 출발 정점이 담긴 상태로 스택 초기화
       while stack:                # 스택이 비어있을때까지 반복
           v = stack.pop()         # 시작 정점을 스택에서 꺼냄
           if not visited[v]:      # 아직 방문하지 않은 정점이라면
               visited[v] = 1      # 방문 체크
               print(f'방문 정점: {v}, 방문 체크: {visited}')
               for j in range(1, V+1):                     # 시작 정점과 연결된 정점 찾기
                   if G[v][j] == 1 and not visited[j]:     # v 정점과 연결된 정점이면서 아직 방문하지 않은 경우에만
                       stack.append(j)                     # 스택에 정점 추가
   
   V, E = map(int, input().split())
   temp = list(map(int, input().split()))                  # 연결된 정점 정보 입력
   # print(temp)
   
   G = [[0]*(V+1) for _ in range(V+1)]                     # 2차원 행렬 초기화
   # print(G)
   visited = [0]*(V+1)                                     # 방문 정점 표시할 리스트 초기화
   
   for i in range(E):                                      # 방향성이 없으므로
       G[temp[i * 2]][temp[i * 2 + 1]] = 1                 # 시작 정점 행에 연결된 정점 열을 1로 변경
       G[temp[i * 2 + 1]][temp[i * 2]] = 1                 # 시작 정점 열에 연결된 정점 행도 1로 변경
   # pprint(G)
   
   dfs(2)
   ```
   
   ```
   def dfs(v):
       global visited
       stack = [v]
       answer = []
       while stack:
           v = stack.pop()
           if visited[v] == 0:
               visited[v] = 1
               answer.append(v)
               for j in range(V, 0, -1):
                   if G[v][j] == 1 and visited[j] == 0:
                       stack.append(j)
       return answer
   
   
   V, E = map(int, input().split())       # V = 정점, E = 간선
   arr = list(map(int, input().split()))  # 연결된 정점 정보
   
   G = [[0]*(V+1) for _ in range(V+1)]    # 2차원 행렬
   visited = [0]*(V+1)                    # 방문 정점 표시할 리스트
   
   # 양방향 간선
   for i in range(E):
       G[arr[i * 2]][arr[i * 2 + 1]] = 1
       G[arr[i * 2 + 1]][arr[i * 2]] = 1
   
   print(dfs(1))
   ```
   
   

2. **부분집합 구하기**

   ```
   def backtrack(a, k, input):
   	global MAXCANDIDATES
   	c = [0] * MAXCANDIDATES
   	
   	if k == input:
   		process_solution(a, k)
   	else:
   		k += 1
   		ncandidates = construct_candidates(a, k, input, c)
   		for i in range(ncandidates):
   			a[k] = c[i]
   			backtrack(a, k, input)
   			
   def construct_candidates(a, k, input, c):
   	c[0] = True
   	c[1] = False
   	retur 2
   
   MAXCANDIDATES = 2
   NMAX = 4
   a = [0] * NMAX
   backtrack(a, 0, 3)
   ```




3. **부분집합의 합**

   ```
   # i: 부분집합에 포함될지 결정할 원소의 인덱스
   # N: 전체 원소 개수
   # K: 찾는 합
   def f(i, N, K):
       if i == N:
           # print(bit, end = ' ')
           s = 0
           for j in range(N):
               if bit[j]:
                   s += a[j]
                   # print(a[j], end = ' ')
           # print(s)
           if s == K:
               for j in range(N):
                   if bit[j]:
                       print(a[j], end=' ')
               print()
       else:
           bit[i] = 1
           f(i+1, N, K)
           bit[i] = 0
           f(i+1, N, K)
       return
   
   
   a = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
   N = len(a)
   bit = [0]*N
   f(0, 10, 10)
   ```

   

------

## 6. 트리(Tree)

1. **전위 순회(preorder traversal)**

   - 현재 노드 n을 방문하여 처리 : V
   - 현재 노드 n의 왼쪽 서브트리로 이동 : L
   - 현재 노드 n의 오른쪽 서브트리로 이동 : R

   ```
   def preorder_traverse(T):
   	if T:
   		visit(T)
   		preorder_traverse(T.left)
   		preorder_traverse(T.right)
   ```

2. **중위 순회(inorder traversal)**

   - 현재 노드 n의 왼쪽 서브트리로 이동 : L
   - 현재 노드 n을 방문하여 처리 : V
   - 현재 노드 n의 오른쪽 서브트리로 이동 : R

   ```
   def inorder_traverse(T):
   	if T:
   		preorder_traverse(T.left)
   		visit(T)
   		preorder_traverse(T.right)
   ```

3. **후위 순회(postorder traversal)**

   - 현재 노드 n의 왼쪽 서브트리로 이동 : L
   - 현재 노드 n의 오른쪽 서브트리로 이동 : R
   - 현재 노드 n을 방문하여 처리 : V

   ```
   def inorder_traverse(T):
   	if T:
   		preorder_traverse(T.left)
   		preorder_traverse(T.right)
   		visit(T)
   ```



- 배열을 이용한 이진 트리의 표현

  - 노드 번호의 성질 

    ```
    노드 번호가 i인 부모 노드 번호 : i//2
    노드 번호가 i인 왼쪽 자식 노드 번호 : 2*i
    노드 번호가 i인 오른쪽 자식 노드 번호 : 2*i + 1
    레벨 n의 노드 번호 시작 번호 : 2^n
    ```

    