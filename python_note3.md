# 문자열(String Type)

- str 타입 (*'str'* / *"str"*) :  변경불가능



- s.**find(x)** : x의 첫 번째 위치를 반환 (없으면 -1 반환)
- s.**index(x)** : x의 첫 번째 위치를 반환 (없으면 오류 발생)
- s.startswitch(x), s.endswitch(x)

```
.isalpha() : 문자열이 (숫자가 아닌)글자로 이루어져 있는가?
.isspace() : 문자열이 공백으로 이루어져 있는가?
.isupper() : 문자열이 대문자로 이루어져 있는가?
.istitle() : 문자열이 타이틀 형식으로 이루어져 있는가?
.islower() : 문자열이 소문자로 이루어져 있는가?
```



- s.**replace(old, new, [count])** : 바꿀 대상 글자를 새로운 글자로 바꿔서 반환
- s.**strip([chars])** : 공백이나 특정 문자 제거
  - strip - 양쪽제거, lstrip : 왼쪽제거, rstrip : 오른쪽제거
- s.**split([chars])** : 공백이나 특정 문자를 기준으로 분리
- *'seperator'*.**join([iterable])** : *구분자*로 iterable(반복가능한 컨테이너)을 합침
- s.capitalize() : 가장 첫번째 글자를 대문자로
- s.title() : '나 공백 이후를 대문자로
- s.uppe() : 모두 대문자
- s.lower() : 모두 소문자
- s.swapcase() : 대소문자 변경





# 리스트(List)

- [] : 가변자료형



- L.**append(x)** : 리스트 마지막에 항목 x를 추가
- L.**extend(iterable)** : 순회형 m의 모든 항목들의 리스트 끝에 추가
- L.**insert(i, x)** : 리스트 인덱스 i에 항목 x를 삽입 
  - 처음 : L.**insert(0, x)**, 마지막 : L.**insert(len(a), x)**

- L.**remove(x)** : 리스트의 첫 번째 x를 제거
- L.**pop(i)** : 리스트 인덱스 i에 있는 항목을 반환 후 제거
  - i가 지정되지 않으면, 마지막 항목 반환 후 제거
- L.**clear()** : 모든 항목 제거



- L.sort() : 원본 리스트를 정렬
- L.reverse() : 순서를 반대로 뒤집음(정령 X)





# 튜플(Tuple)

- 불변자료형





# 셋(Set)

- 가변자료형



- s.**add(x)** : x 추가
- s.**update(*others)** : 여러 값을 추가

- s.**pop()** : 임의의 원소를 제거해 반환

- s.**remove(x)** : x 삭제





# 딕셔너리(Dictionary)

- 순서 없이 키-값(key-value)



- d.**get(k, [default])** : key가 있으면 value 가져옴(없으면 None)
- d.**pop(key, [default])** 
- d.**update([other])** : 





# 복사 :fire:중요!!!

- 할당 : 대입연산자(=)
- 얕은 복사 : Slice 연산자
- 깊은 복사 : copy.deepcopy(a)





값 추가 및 삭제

.extend(iterable)

.remove(x) : 리스트에서 값이 x인 것 삭제

.pop(i) : 정해진 위치 i에 있는 값을 삭제하고 반환 (i가 지정되지 않으면 마지막 항목)

.clear() : 모든항목 삭제

.index(x)

.count(x) : 원하는 값의 개수를 반환



.sort()\

- .sort(a) : 원본 리스트를 정렬시키고, None을 return
- sorted(b) : 원본 리스트를 변경하지 않고, 정렬된 리스트를 return 

.reverse() : 순서를 반대로 뒤집음