# python set type - set(집합)
- 순서X, 중복X
- { }
- set( [ ] )
```python
temp = {'jslim', 'teacher'}
print('set - ', temp, type(temp))							set -  {'jslim', 'teacher'} <class 'set'>

temp = set([1,2,3,4,5,5,5,5])             # 중복이 안돼서 프린트하면 5는 1개만 나옴
print('set - ', temp, type(temp))							set -  {1, 2, 3, 4, 5} <class 'set'>

temp = set([1, 3.14, 'pen', False])       # 순서 x : 데이터가 순서데로 쌓이지 않음. 먼저 들어갔어도 나올 땐?!
print('set - ', temp, type(temp))							set -  {'pen', 1, 3.14, False} <class 'set'>
casting = tuple(temp)
print('casting - ', casting, casting[1:3])		casting -  ('pen', 1, 3.14, False) (1, 3.14)
```
### 연산 가능
```pyrhon
set01 = set([1,2,3,4,5])
set02 = set([3,4,5,6,7])
```
- 교집합 &  == intersection()
-  합잡합 |  == union()
-  차집합 -  == difference()
-  파이썬 모든 변수는 객체, 객체.함수()
```python
print('교집합 & - ', set01&set02)															교집합 & -  {3, 4, 5}
print('교집합 .intersection() - ', set01.intersection(set02))	교집합 .intersection() -  {3, 4, 5}

print('합집합 | - ', set01|set02)													합집합 | -  {1, 2, 3, 4, 5, 6, 7}
print('합집합 .union() - ', set01.union(set02))						합집합 .union() -  {1, 2, 3, 4, 5, 6, 7}
	
print('차집합 - ', set01 - set02)													차집합 -  {1, 2}
print('차집합 .difference() ', set01.difference(set02))		차집합 .difference()  {1, 2}
```
### 요소 추가 .add()
```python
set01.add(7)
print('set add - ',set01)																set add -  {1, 2, 3, 4, 5, 7}
```
### 요소 삭제 .remove(), .discard()
```python
set01.remove(9)      					 					 # 존재 하지 않는 요소는 오류를 발생시킴
set01.discard(9)    									  # 존재 하지 않는 요소는 오류를 무시 >> 피드백이 되지 않음 >> 추천X

set01.remove(4)
print('set.revome() - ',set01 )					set.revome() -  {1, 2, 3, 5, 7}
```
### 중복제거용으로 활용할 수 있음
```python
gender = ['홀', '짝', '홀', '짝', '홀', '짝', '홀', '짝']
setGender = set(gender)
print('중복제거 - ',setGender, type(setGender))					    	중복제거 -  {'홀', '짝'} <class 'set'>
listGender = list(setGender)
print('list casting - ',listGender,type(listGender))  list casting -  ['홀', '짝'] <class 'list'>
print('list casting - ', listGender[0])								list casting -  홀
print('list casting - ', listGender[1])								list casting -  짝
```