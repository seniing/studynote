## 01_01. 파이썬 기초

### 1. 기초 문법

- type() : 변수에 할당된 값의 타입

- id() : 변수에 할당된 값(객체)의 고유한 아이덴티티(identity) 값이며, 메모리주소

- 내장함수(이름으로 사용할 수 없다.)

  ```
  False, None, True, and, as, assert, async, await, break, class, continue, def, del, elif, else, except, finally, for, from, global, if, import, in, is, lambda, nonlocal, not, or, pass, raise, return, try, while, with, yield
  ```



### 2. 자료형(Data Type)

- **불린형**(Boolean Type)

  - True 
  - False : ```0, 0.0, (), [], {}, '', None```

- **수치형**(Numeric Type)

  - int (정수, integer) : ```2진수 : 0b , 8진수 : 0o, 16진수 : 0x```
  - float (부동소수점, 실수, floating point number)
  - complex (복소수, complex number)

- **문자열**(String Type)

  ```
  \n : 줄 바꿈
  \t : 탭
  \r : 캐리지리턴
  \0 : 널(Null)
  \\ : \
  \' : 단일인용부호(')
  \" : 이중인용부호(")
  ```

  ```
  %-formatting
  	print('Hello, %s' % name)
  	print('내 성적은 %d' % score)
  	print('내 성적은 %f' % score)
  
  str.format()
  	print('Hello, {}! 성적은 {}'.format(name, score))
  
  f-string
  	print(f'Hello, {name}! 성적은 {score}')
  ```

- **None**
  - 값이 없음을 표현하기 위한 타입

### 3. 컨테이너(Container)

![container](python_note.assets/148164052-3b12d3a2-a95e-4d4d-ae25-86ca1ba9657b.png)

- **List**

  ```
  [], list()    # List 생성
  my_list[i]    # 값에 대한 접근 - 0부터 시작
  ```

  ```
  list_name.append(dict_name['key_name']) : List에 Dict의 'key_name'에 할당된 값 추가
  ```

  

- **Tuple**

  ```
  (), tuple()    # Tuple 생성 - 불변자료형
  my_tuple[i]    # 값에 대한 접근 - 0부터 시작
  ```

- **Range()**

  ```
  range(n)    # 0부터 n-1까지 값을 가짐
  range(n, m)    #n부터 m-1까지 값을 가짐
  range(n, m, s)    #n부터 m-1까지 +s만큼 증가
  ```

- **Set**

  ```
  {}, set()    # set 생성 - 순서 없음
  ```

- **Dictionary**

  ```
  {key1: value1, key2: value2}, dic()    # Dictionary 생성
  dict_name['key1']    # value1 출력
  dict_name.keys()    # key 출력
  dict_name.values()    # value 출력
  dict_name.items()    # key, value 출력
  ```
  
  ```
  - dict_name.get('key_name') : dict_name에서 'key_name'에 할당된 값 가져오기
  
  <Dictionary 생성>
  - new_dict = {'key': dict_name.get('key_name')}
  - new[key] = value 
  ```
  
  

### 4. 연산자(Operator)

- 산술 연산자 (Arithmetic Operator)

  ```
  + : 덧셈
  - : 뺄셈
  * : 곱셈
  / : 나눗셈
  // : 몫
  % : 나머지(modulo)
  ** : 거듭제곱
  ```

- 비교 연산자 (Comparison Operator)

  ```
  < : 미만
  <= : 이하
  > : 초과
  >= : 이상
  == : 같음
  != : 같지않음
  is : 객체 아이덴티티
  is not : 객체 아이덴티티가 아닌경우
  ```

- 논리 연산자

  ```
  a and b : a와 b 모두 True시만 True
  a or b : a 와 b 모두 False시만 False
  not a : True -> False, False -> True
  ```

- 복합 연산자

  ```
  a += b : a = a + b
  a -= b : a = a - b
  a *= b : a = a * b
  a /= b : a = a / b
  a //= b : a = a // b
  a %= b : a = a % b
  a **= b : a = a ** b
  ```

- 멤버십 연산자(Membership Operator)

  ```
  in 연산자
  not in 연산자
  ```





## 01_02. 제어문(Control Statement)

### 1. 조건문(Conditional Statement)

- **if**

```
if <조건식>:
	<코드 블럭>
elif <조건식>:
	<코드 블럭>
else:
	<코드 블럭>
```

```
<조건 표현식>
(ture_value) if <조건식> else (false_value)
```



### 2. 반복문(Loop Statement)

- **while**

```
while <조건식>:
	<코드 블럭>
```

- **for**

```
for <임시변수> in <순회가능한 데이터>:
	<코드 블럭>
```

```
# 0. dictionary 순회 (key 활용)
for key in dict:
    print(key)
    print(dict[key])

# 1. `.keys()` 활용
for key in dict.keys():
    print(key)
    print(dict[key])

# 2. `.values()` 활용
# 이 경우 key는 출력할 수 없음
for val in dict.values():
    print(val)

# 3. `.items()` 활용
for key, val in dict.items():
    print(key, val)
```

- 반복제어
  - **break** : 반복문에서 빠져나가기
  - **continue** : continue 이후 코드를 수행하지 않고, 다음 요소부터 계속하여 반복
  - **pass** : 아무것도 하지 않음





## 02_01. 함수(Function)

### 1. 함수

```:
def <함수이름>(parameter1, parameter2):
	<코드 블럭>
	return value
```

- **map(function, iterable)** : 순회가능한 데이터 구조(iterable)의 모든 요소에 function을 적용
  - function => str, int etc.
- **filter(function, iterable)** : iterable에서 function의 반환된 결과가 `True` 인 것들만 구성하여 반환

- **zip(*iterables)** : 복수의 iterable 객체를 tuple 형태로 모아줌

- **lambda [parameter] : 표현식** : 표현식을 계산한 결과 값을 반환하는 함수로, 익명함수





## 02_02. 모듈(MOdule)

### 1. 모듈과 패키지 불러오기

- **import** *module*
- **from** *module* **import** *var, function, Class*
- **from** *module* **import ** *



- **from** *package* **import** *module*
- **from** *package.module* **import** *var, function, Class*



## JSON 파일

1. 파일 읽어오기
   - **open**(*file*, mode = '*r*', encoding = utf-8)
   - **json.load**(*json_name*) : json 파일을 dict 형태로 변환







