# 2일차

## bulit in type

### 변수 정의 및 생성
#블럭 단위 런 단축키 (shift + alt + e)

- intValue    = 123

- floatValue  = 3.14

- boolValue   = True

- strValue    = 'COFFEE'

  #네 가지는 스칼라 데이터 타입: 단일 데이터 값만 저장
```python
print()
print( type(intValue), type(floatValue), type(strValue))
<class 'int'> 				 <class 'float'>   <class 'str'>
```

### type casting
```python
numStr = "720"
numNum = 100
print( int(numStr) + numNum)			820
print(numStr + str(numNum))				720100

year = "2021"
print(int(year) -1)								2020
```
### list [ ]
```python
listAry = ['python', 'anaconda']
print(type(listAry))								<class 'list'>
```
### dict { }    key:value 형식
```python
dictValue = {
    "name"    : "machin Learning",
    'version' : 2.0
}
print(type(dictValue))						<class 'dict'>
```
### tuple ( )
```python
tupleValue = (3,)
print(type(tupleValue))						<class 'tuple'>
```
### set { }
```python
setValue = {3,5,7}
print(type(setValue))							<class 'set'>
```
#keyboard input
#function syntax

'''
접근지정자 리턴타입 함수명(매개변수){

}
python function
def sum():
    statement
'''

### input( )
```python
inputNumber = input('숫자를 입력하시오 : ')
```
### print(inputNumber)
```python
print(type(inputNumber))          <class 'str'> # 문자열로 나옴, 숫자로 나오게 할려면 int(input())하면 됨
```

### 문자형(str)
```python
str01 = 'I am Python'
str02 = "Python"
str03 = '''this is a
multiline
sample text'''
str03 = """this is a
multiline
sample text"""
```

#ex)

```python
query = '''
select *
from emp
where deptno = {no}
order by eno desc
'''
```
```python
seqText = 'Talk is cheap. Show me the code'
print(seqText)																	Talk is cheap. Show me the code
```

### dir( )  
`dir()` 내장 함수는 어떤 객체를 인자로 넣어주면 해당 객체가 어떤 변수와 메소드(method)를 가지고 있는지 나열

```python
print( dir(seqText))
['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isascii', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']
```
### slicing
```python
print(seqText[3])   										k			  			# 하나만 꼭 집는 건 인덱싱
print(seqText[-1])											e
print(seqText[0:4])    									Talk  			  # 범위로 하는 건 슬라이싱
print(seqText[-6:]) 										e code		    # [1: ] 빈칸은 마지막까지라는 뜻 , 1부터 마지막까지
print(seqText[ : : -1])  edoc eht em wohS .paehc si klaT		 # 스텝,   -1은 리버스로
print(seqText[ : : 2])	 Tl scep hwm h oe
print(seqText[ : : -2])  eo h mwh pecs lT

#아래의 문자열에서 '홀'만 출력하세요~~
string = '홀짝홀짝홀짝홀짝홀짝'
print(string[::2])									홀홀홀홀홀
print(string[::-1])									짝홀짝홀짝홀짝홀짝홀
```
### 문자열 조작을 위한 많은 내장 함수를 제공하고 있다.   함수를 이용하고 싶으면 .을 찍고 사용하면된다
```python
string = "python"
print("Capitalize :", string.capitalize())							Capitalize : Python
```
### 문자치환 replace(oldchar, newchar)
```python
phoneNumber = '010-4603-2283'
replacePhoneNumber = phoneNumber.replace('-', ' ')
print(replacePhoneNumber)																010 4603 2283

string = 'abcdefe2a345a56432a'    # 소문자 >> 대문자
print(string.replace('a', 'A'))													Abcdefe2A345A56432A
```

#### 문자열을 쪼개는 함수 : split()
#아래 문자열에서 도메인만 출력하고 싶다면?            print(url.split('.')[2])
```python
url = "http://www.naver.com"
urlSplit = url.split('.')
print(urlSplit, type(urlSplit))										['http://www', 'naver', 'com'] <class 'list'>
print('domain:', urlSplit[-1])										domain: com
```
### 문자열에서 공백 제거 함수: strip(), rstrip(), lstrip()
### 대문자, 소문자 변환 함수: upper(), lower()

### 문자열의 길이: len()

```python
companyName= '     samsung     '
print(companyName.strip(), len(companyName.strip()))					'samsung 7'
print(companyName.rstrip(), len(companyName.rstrip()))				'     samsung 12'
print(companyName.lstrip(), len(companyName.lstrip()))				'samsung      12'
print(companyName.upper())																		'     SAMSUNG     '
```
### endswith()
- 문자열이 특정문자로 끝나는지 여부를 알려준다. 
- true나 false를 반환
```python
fileName = 'report.xls'
isExits = fileName.endswith(('xls', 'xlsx', 'csv'))
print(isExits, type(isExits))																	True <class 'bool'>
```
### in, not in -> True | False
- 특정 값이 있는지/없는지
- true나 false를 반환
- 숫자는 비추
```python
myStr = 'this is a sample Text'
print("sample" in myStr)											True
print("text" not in myStr)										True
print("this" in myStr.lower())								True
```
### 문자의 빈도 count( )
### 문자 찾기 find( )
### 문자의 인덱스 index( )
#find 찾는 문자의 처음 위치의 인덱스 번호

```python
brandName = 'cocacola'
print(len(brandName), brandName.count('c'), brandName.find('a'))    	8, 3, 3
# -1: 의미 없음, 못찾았다
```





## python sequence - list

- 자료구조에서 중요
- 파이썬에는 배열이 존재하지 않는다.
- 1차원 자료구조  : R - Vector
- 순서가 있음(index 부여 0~), 중복 , 수정, 삭제 가능
-  [  ]이용해서 변수를 선언 할 수 있다.
- 리스트끼리 연산도 가능하다.
```python
a =list()
a = []

a = [1,2,3,]
print(a, type(a))									[1, 2, 3] <class 'list'>
print(a[0])												1
a[0] = 5
print(a[0])												5
```
### 요소를 추가하는 함수
- append( )   :  리스트 마지막에 ( )를 추가하는 함수
- insert(a, b) :  리스트의 a번째 위치에 b를 삽입하는 함수
```python
a.append(4)
print(a)													[5, 2, 3, 4]
a.insert(0, 6)
print(a)													[6, 5, 2, 3, 4]
a.sort()           																												 #오름차순 자동정렬
print(a)													[2, 3, 4, 5, 6]
a.reverse()       																											   #내림차순 자동정렬
print(a)													[6, 5, 4, 3, 2]
```
### pop( ) : 
기존 리스트에서 요소를 가져오고 삭제시킨다. 맨 마지막 인덱스를 알려주고 삭제 시킨다.      # pop(): (-1)이 default
```python
print("a - pop():", a.pop())								2
print("a - print:", a)											[6, 5, 4, 3]

### extend() vs append()      expend(): 기존 리스트에 새로운 리스트를 추가할 때
ex = [4,3]
# a.append(ex)
# print('a = append: ',a)     [6, 5, 4, 3, [4, 3]        [1,2,3,[4,3]]
a.extend(ex)
print('a - expend:', a)       [6, 5, 4, 3, 4, 3]       # [1,2,3,4,3]
```



movieRank = ['원더우먼', '해리포터', '겨울왕국2', '가타카', '국제수사', '반도']

#### 1. 해당 리스트에 '배트맨'을 추가한다면?
```python
movieRank.append('배트맨')
print(movieRank)							['원더우먼', '해리포터', '겨울왕국2', '가타카', '국제수사', '반도', '배트맨']
```
#### 2. 원더우먼과 해리포터 사이에 '씽'을 추가한다면?
```python
movieRank.insert(1, '씽')
print(movieRank)					['원더우먼', '씽', '해리포터', '겨울왕국2', '가타카', '국제수사', '반도', '배트맨']
```
#### 3. 리스트에서 반도를 삭제한다면?
```python
movieRank.remove('반도')
print(movieRank)					['원더우먼', '씽', '해리포터', '겨울왕국2', '가타카', '국제수사', '배트맨']
```
#### 최대값, 최소값, 총합, 평균
```python
scoreData = [1,2,3,4,5,6,7]
print("max" , max(scoreData))															max 7
print("min" , min(scoreData))															min 1
print("sum" , sum(scoreData))															sum 28
print("mean" ,sum(scoreData)/len(scoreData))							mean 4.0
```





## python sequence type - tuple
- 순서가 있다. 중복도 된다. 수정과 삭제가 되지 않는다.
- 읽기 전용(불변, immutable)
- ( ) 선언 가능하다.
```python
myTuple = ('반도', '강철비2', '아이언맨')
oneTuple = (1,)                            							 #요소가 하나일 땐 컴마(,)써주기
```
### 사용자의 편의를 위해서 괄호 없이 만들 수 있다.
```python
myTuple = 1,2,3,4,5

multiTuple = (100, 1000, 'Ace', 'Base', 'Captine')
print(multiTuple)																					(100, 1000, 'Ace', 'Base', 'Captine')
```
### indexing
```python
print('index 1 -', multiTuple[1])															1000
print('slicing - ', multiTuple[2:], type(multiTuple[2:]))			
																										('Ace', 'Base', 'Captine') <class 'tuple'>
```
### casting   
- 수정과 삭제가 되지 않기 때문에, 수정과 삭제를 하려면 타입변환이 필요하다.
```python
multilist = list(multiTuple[2:])
castingMultiTuple = tuple(multilist)
```




### python sequence type - range

#### 1~99까지의 정수 중 짝수만 저장된 튜플을 생성한다면?
```python
range01 = range(10)
print(range01)																									range(0, 10)

range02 = range(1, 11, 2)   # 1, 3, 5, 7, 9, 11
print(range02)																									range(1, 11, 2)

even = tuple(range(2, 100, 2))
print(even)																											
(2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24, 26, 28, 30, 32, 34, 36, 38, 40, 42, 44, 46, 48, 50, 52, 54, 56, 58, 60, 62, 64, 66, 68, 70, 72, 74, 76, 78, 80, 82, 84, 86, 88, 90, 92, 94, 96, 98)																					#even[0] = 1 --TypeError  수정이 불가능하기 때문에
print(7 in range02)														True
print(10 in range02)													False
print(range02.index(7))												3									# 1,3,5,7,9,11 중 7의 인덱스 번호
print(range02[2])															5									# 2번 인덱스 번호의 값 
print(range02[2:])														range(5, 11, 2)		# 2번 인덱스 번호부터 마지막 인덱스 
																																#	번호까지 2씩 증가  5, 7,9, 11
```





## python mapping type - dict

- dictionary는 key와 value의 대응관계 type
- Hash 또는 Associative Array와 유사한 구조
- { }
- 순서 X, 키 중복 X, 수정 O, 삭제 O
```python
temp = {}
print(type(temp))															<class 'dict'>

dict01 = {
    'name'    : 'seop',
    'age'     : 49,
    'address' : 'kwangju',
    'birth'   : '730910',
    'gender'  : 'm'
}
print(dict01, type(dict01))

{'name': 'seop', 'age': 49, 'address': 'kwangju', 'birth': '730910', 'gender': 'm'} 
<class 'dict'>
```
### dict 요소를 추가하는 방법
```python
dict01['marriage'] = True
print(dict01, type(dict01))

{'name': 'seop', 'age': 49, 'address': 'kwangju', 'birth': '730910', 'gender': 'm', 
 'marriage': True} <class 'dict'>
```
### 키 유무를 판단
- True / False 로 알려줌
```python
print('marriage' in dict01)												True
```
### 데이터 확인
```python
print(dict01['address'])													kwangju
print(dict01.get('name'))													seop
print(len(dict01))																6
```
### 다양한 dictionary 생성방법
```python
dict02 = dict([('name', 'seop'), ('age',49), ('address', 'kwangju'), ('birth', '730910'), ('gender', 'm')]) 																												  # 리스트 안의 튜플 형식
print(dict02, type(dict02))

{'name': 'seop', 'age': 49, 'address': 'kwangju', 'birth': '730910', 'gender': 'm'}
<class 'dict'>


dict03 = dict(name='seop', age=49, address='kwangju', birth='730910', gender='m')             
print(dict03, type(dict03))																								# 변수에 값을 할당하는 형식

{'name': 'seop', 'age': 49, 'address': 'kwangju', 'birth': '730910', 'gender': 'm'} 
<class 'dict'>

```
### dict_keys, dict_values, dict_items
```python
print('dict_keys -', dict03.keys(), type(dict03.keys()), list(dict03.keys()), type(dict03.keys()))

dict_keys(['name', 'age', 'address', 'birth', 'gender']) 		<class 'dict_keys'> 
['name', 'age', 'address', 'birth', 'gender'] 							<class 'dict_keys'>


print('dict_values -', dict03.values(), type(dict03.values()), list(dict03.values()), type(dict03.values()))

dict_values(['seop', 49, 'kwangju', '730910', 'm']) 				<class 'dict_values'> 
['seop', 49, 'kwangju', '730910', 'm']										  <class 'dict_values'>


print('dict_items -', dict03.items(), type(dict03.items()), list(dict03.items()), type(dict03.items()))

dict_items([('name', 'seop'), ('age', 49), ('address', 'kwangju'), ('birth', '730910'), ('gender', 'm')]) 																					<class 'dict_items'> 
[('name', 'seop'), ('age', 49), ('address', 'kwangju'), ('birth', '730910'), ('gender', 'm')] 																														<class 'dict_items'>
```
### looping
```python
'''
for(초기식; 조건식; 증감식){											# 다른 언어의 경우 

}
for item in collection:
    statement
'''

for key in dict03.keys():
    print('key: {}, value: {}'.format(key, dict03.get(key)))
key: name, value: seop
key: age, value: 49
key: address, value: kwangju
key: birth, value: 730910
key: gender, value: m

    
for value in dict03.values():
    print('value: {}'.format(value))
value: seop
value: 49
value: kwangju
value: 730910
value: m    
 

for (key, value) in dict03.items():
    print('key: {}, value: {}'.format(key, value))
key: name, value: seop
key: age, value: 49
key: address, value: kwangju
key: birth, value: 730910
key: gender, value: m
```
### 삭제 pop( ), del
```python
print(dict03)					
{'name': 'seop', 'age': 49, 'address': 'kwangju', 'birth': '730910', 'gender': 'm'}

del dict03['gender']
print(dict03)							{'name': 'seop', 'age': 49, 'address': 'kwangju', 'birth': '730910'}

dict03.pop('birth')
print(dict03)							{'name': 'seop', 'age': 49, 'address': 'kwangju'}

dict03.clear()
print('dict03 clear - ' , dict03)										dict03 clear -  {}
```
