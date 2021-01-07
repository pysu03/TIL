
# python function
함수는 가독성을 높이기 위한 방법으로
하나 이상의 본문을 가지는 코드를 함수로 정의한는 것이 좋다.
내장함수 / 사용자정의함수
함수를 정의할 때 def라는 키워드를 이용해서 함수를 정의

### user define function(사용자정의 함수)
```python
# 일반적인 구조
def functionName():
    print()
    statement
    :return value(bulit-in Type)
```

### 매개변수 X, 리턴값이 X
```python
def userPrint():
    print('userPrint')
```
```python
<아래 3가지로 표현하여 사용 가능>
from digital.python import packageFunction
packageFunction.printCoins()

from digital.python import packageFunction as f 						#(f는 별칭, f.으로 사용가능)
f.printCoins()

from digital.python.packageFuntion import printCoins(*)     # printCoins 대신 ?*을 쓰면 전부 가져옴
printCoins()
```
### 매개변수 X, 리턴값이 O
```python
from digital.python import packageFuntion as f
rtnMsg = f.returnFunc()
print('call returnFunc() - ', rtnMsg)

call returnFunc() -  호출한 쪽으로 값이 전달됩니다.
```

### 매개변수 O, 리턴값이 O
```python
from digital.python import packageFuntion as f
echoMsg = f.sayEcho('Angel')
print('call sayEcho() - ', echoMsg)

call sayEcho() -  Angel님, 반갑습니다.

from digital.python import packageFuntion as f
domain = f.makerUrl('naver')
print('call makeUrl() - ', domain)

call makeUrl() -  www.naver.com
```
### 매개변수 O, 리턴값이 X
```python
f.badFunc('jslim')
```
### 매개변수에 튜플이 들어갈 때
```python
# t = (1,2,3,4,5,6,7,8,9)
tupRtn = f.tupleFunc(1,2,3,4,5,6,7,8,9)
print('call tupleFunc() - ', tupRtn)

call tupleFunc() -  45
```
### 매개변수에 딕션너리가 들어갈 때
```python
f.dictFunc(name='jslim', age = 49)

name = jslim
age = 49
```
### 범위내에 있는 값의 홀, 짝의 합을 구해서 리턴
```python
(oddSum, evenSum) = f.cntSum(100, 500)
print('홀수의 합 {}, 짝수의 합 {}'.format(oddSum,evenSum), type((oddSum, evenSum)))

홀수의 합 60000, 짝수의 합 60300 <class 'tuple'>
```
### 인자로 넘겨받은 년도 사이의 윤년을 찾아 리턴시켜주는 함수를 작성한다면?
```python
# list 타입
leapYearList = f.leapYearFunc(1900, 2021)
print(leapYearList, type(leapYearList))

[1992, 1996, 2000, 2004, 2008, 2012, 2016, 2020] <class 'list'>
```



```python
dictMsg = f.rtnDictFunc(10)
print('dictMsg - ', dictMsg, type(dictMsg))

dictMsg -  {'cal01': 100, 'cal02': 200, 'cal03': 300} <class 'dict'>


for value in dictMsg.values():
    print('dict_values - ', value)
    
dict_values -  100
dict_values -  200
dict_values -  300
```

