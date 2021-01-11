### default parameter 사용
```python
# worker function
def defaultParam(x, y, z = True):
    paramSum = x + y
    if paramSum > 10 and z:
        return paramSum
    else:
        return 0

# caller function
defaultParam(10, 20)
=defaultParam(10, 20,True)

result = defaultParam(10, 20)
print('caller defaultParm() - ', result) 														caller defaultParm() -  30
```
### 함수의 입력인자가 ' list, dict ' -> mutable( 변경이 가능한 형식 )
```python
tmpList = [10]

def mutableFunc(argList):
    argList.append(100)

mutableFunc(tmpList)
print('tmpList - ', tmpList)																			 	tmpList -  [10, 100]
```
### 함수의 입력인자가 ' 숫자, 문자열, tuple ' -> immutable( 변경 불가 )
```python
tmpList = [10]
tmpX = 10
def mutableFunc(argX, argList):
    argX = argX+100
    argList.append(100)

mutableFunc(tmpX, tmpList)
print('tmpList - ', tmpList)																				tmpList -  [10, 100]
print('tmpX   - ', tmpX)																						tmpX    -  10
```
### variable(변수) - 선언위치에 따라서 (local, global)
```python
tmp = 100 			# global변수

def myFunc(x):
    tmp = 0		  # locla 변수     local변수 사용시 반드시 선언해야된다.
    tmp += x
    return tmp

print('call myFunc - ', myFunc(100))																call myFunc -  100


# grobal변수를 local변수에서 사용하려면 local변수 앞에 'global'을 붙여주면 된다.
tmp = 100 				# global변수

def myFunc(x):
    global tmp		#
    tmp += x
    return tmp

print('call myFunc - ', myFunc(100))																call myFunc -  200
```
###
```python
def personInfo(weight, height, **other):
    print('weight - ', weight)
    print('height - ', height)
    print('extra - ', other, type(other)) 						# dict  xxx=' ' 형식으로 사용해야함
personInfo(69, 174, name='YS', address='seoul')

weight -  69
height -  174
extre -  {'name': 'YS', 'address': 'seoul'} <class 'dict'>
```
###

```python
def overroll(args01, args02, *args03, **args04):
    print(args01, args02, args03, args04)
overroll(19, 29, 'lee', 'kim', 'park', 'cho', age01=20, age02=30, age03=40)

9 29 ('lee', 'kim', 'park', 'cho') {'age01': 20, 'age02': 30, 'age03': 40}
```
### nested function (중첩함수)
```python
def outerFunc(num):
    def innerfunc(num):
        print('innerFunc - ', num)
    innerfunc(num + 100)

outerFunc(100)																											innerFunc -  200
# innerFunc(100) - 실행불가 즉, 호출 불가합니다.

중첩합수 활용 예)
outer함수 : 자료(data)생성, inner함수 포함
inner함수 : 자료 연산/처리(합계,평균)

  
ex)
def calcFunc(data):
    dataset = data
    def sumFunc():
        total = sum(dataset)
        return total
    def avgFunc(total):
        avg = total/len(dataset)
        return avg
    return sumFunc, avgFunc

data = list(range(1,100))
# print('range data - ', data)								range data -  [1, 2, 3, 4, ... ,96, 97, 98, 99]

rtnSumFunc, rtnAvgFunc = calcFunc(data)
tot = rtnSumFunc()
print(tot)																																				4950
avg = rtnAvgFunc(tot)
print(avg)																																				50.0

# outer함수가 inner함수를 리턴하면 외부에서도 inner함수를 사용 할 수 있다
```
### 재귀함수
```python
재귀함수(self-recursive function)
- 함수 내부에서 자신의 함수를 반복 호출하는 기법
- 사용의 용도: 반복적으로 변수를 변경해서 연산 할 때 ex)누적, 팩토리얼
- 종료식이 필요함

def countFunc(n): 							 # n = 5 -> 1, 2, 3, 4, 5
    if n == 0:
        return 0
    else:
        countFunc(n-1) 					 # stack [5, 4, 3, 2, 1] >> 출력될땐 후입선출로 인해 역순으로 출력
        print(n, end=" ")

countFunc(5) 																				  1 2 3 4 5
countFunc(0) 																				  0
```
### 누적 : (n) = 1 +2 + 3 + ...... + n
```python
def addSum(n):
    if n == 1:
        return 1
    else :
        result = n + addSum(n-1)
        # print('debug - ', result)
        return result

print('n=5 - ', addSum(5))														n=5	  -  15
print('n=100 - ', addSum(100))												n=100 -  5050
```
### 익명의 함수(lambda 식)를 만드는 방법
람다식(가독성 향상, 코드 간결, 메모리 절약 - 즉시 실행 함수이기 때문에)
함수의 문장이 1문장일때 유용
```python
일반적인 경우)
def mulitFunc(x,y):
    return x * y
print(mulitFunc(10,50))																													500

lambda를 이용한 경우)
# syntax : lambda arg : body

lambdaVar = lambda x,y : x * y
print(lambdaVar(10,50))																													500


def lambdaFunc(x,y, func):
    print('lambdaFunc - ', x * y * func(100, 100))
< 여러가지 표현 방법 > 
lambdaFunc(10, 20, lambda x, y : x * y)																lambdaFunc -  2000000
lambdaFunc(10, 20, lambdaVar)																					lambdaFunc -  2000000
lambdaFunc(10, 20, mulitFunc)																					lambdaFunc -  2000000
```
### hint
```python
def totalLengthFunc(word : str, num : int) :
    return len(word) * num

print('hint - ', totalLengthFunc('i love you', 10))										hint -  100

매개 변수값에 타입을 지정해주는 힌트를 넣어줌
```

