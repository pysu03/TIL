```
'''
***학습목표***
다중상속
추상화
데코레이션
제너레이터
이터레이터
'''
# 다중상속
class Animal(object) :
    def cry(self):
        pass
class Tiger(Animal) :
    def jump(self):
        print('호랑이가 점프를 한다.')
    def cry(self):
        print('어흥')
class Lion(Animal) :
    def bite(self):
        print('한 입에 꿀꺽한다.')
    def cry(self):
        print('그르렁')
class Liger(Lion, Tiger) :
    def play(self):
        print('라이거가 사육사와 재미있게 놀고 있다.')

# 추상클래스
'''
- 클래스를 만드는 이유 -> 객체를 생성하기 위해
- 추상클래스 -> 객체생성 X
- 추상메서드(함수)를 하나라도 가지면 추상클래스
- 추상함수가 부모클래스에 있으면 자식클래스는 반드시 추상함수를 오버라이딩을 해야한다.
- 함수 구현을 강제하기 위해서 사용
- 마킹해야함 @abstractmethod
'''
from abc import *   # @abstractmethod을 쓸려면 임포트해야함

class Base(metaclass=ABCMeta) :
    @abstractmethod
    def study(self):
        pass

    def goToSchool(self):
        print('hard study')

class Student(Base) :
    def study(self):
        print('공부하자~~')


# 특수문법 - 데코레이션
'''
Decorator는 함수의 인자로 다른 함수를 전달하는 과정에서 적용 할 수 있는 기법
패턴

'''
def outerFunc(func) :
    def innerFunc() :
        func()
    return innerFunc

def userFunc() :
    print('userFucn 함수가 수행되었습니다.')
# userFunc()

decoratorFunc = outerFunc(userFunc)
decoratorFunc()

import time
def userOuterFunc(func) :
    def userInnerFunc() :
        print('{} 함수수행 시간을 계산합니다.'.format(func.__name__))
        start = time.time()
        func()
        end = time.time() - start
        print('{} 함수수행 시간은 {} 입니다.'.format(func.__name__, end))
    return userInnerFunc()

decoratorUserFunc = userOuterFunc(userFunc)
decoratorUserFunc()


def loggerLogin() :
    print("YS's login")
loggerLogin()


import datetime
def loggerLoginYS() :
    print(datetime.datetime.now())
    print("YS's login")
    print(datetime.datetime.now())

def loggerLoginYH() :
    print(datetime.datetime.now())
    print("YH's login")
    print(datetime.datetime.now())



def datetimeDecorator(func) :
    def wrapper() :
        print(datetime.datetime.now())
        func()
        print(datetime.datetime.now())
    return wrapper





def loggerLoginYS() :
    print("YS's login")

def loggerLoginYH() :
    print("YH's login")


def datetimeDecorator(func):
    def wrapper():
        print(datetime.datetime.now())
        func()
        print(datetime.datetime.now())
    return wrapper

# YS = datetimeDecorator(loggerLoginYS)
# YS()
#
# YH = datetimeDecorator(loggerLoginYH)
# YH()


@datetimeDecorator
def dumpFunc():
    print('함수 실행')

dumpFunc()



# 데코레이터 [실습]
'''
1. typeChecker Decorator 만들기(인자의 유효성 검사)
- digit01, digit02 를 곱한 값을 출력하는 함수
- typeChecker Decorator로 digit01, digit02 가 정수가 아니면
- 'only integer support' 출력
'''

def typeChecker(func) :
    def innerFunc(digit01, digit02):
        # 유효성 검사
        if  type(digit01) != int or type(digit02) != int :
            print('only integer support')
            return                             # 조건처리에서 리턴 쓰고 아무것도 안쓰면 함수실행을 종료하라는 뜻
        return func(digit01, digit02)
    return innerFunc

# 사용
@typeChecker
def div(digit01, digit02) :
    return digit01 * digit02

msg = div(3 , 1)
print(msg)


# 파라미터(매개변)와 관계없이 모든 함수에 적용 가능한 Decorator를 만들고 싶다면?
# *args, **args

def generalDeco(func):
    def wrapper(*args, **kwargs) :
        print('this is decorated')
        return func(*args, **kwargs)
    return wrapper

@generalDeco
def userSquare(digit) :
    return digit * digit
print(userSquare(2))

@generalDeco
def userPlus(digit01, digit02) :
    return digit01 + digit02
print(userPlus(2,3))

@generalDeco
def userQuad(digit01, digit02, digit03, digit04) :
    return digit01 * digit02 * digit03 * digit04
print(userQuad(2,3,4,5))




def makeBold(func):
    def wrapper(string) :
        return '<b>' + func(string) +'</b>'
    return wrapper

def makeFont(func) :
    def wrapper(string) :
        return '<i>' + func(string) +'</i>'
    return wrapper

@makeBold
@makeFont       # 순서는 가장 가까운 데코레이터부터 실행됨
def makeBoldFont(string):
    return string

print(makeBoldFont('두개의 데코레이터를 활용하고 있습니다.'))


# class - function 데코레이터 적용이 가능할까??     >>  가능함
# 클래스 밖에 데코레이터 만들고 클래스 내부에서 가져다 쓰는 방식

def tagH1(func):
    def wrapper(self, *args, **kwargs ):              # 클래스에서 데코를 쓸려면  self를 꼭 써줘야함
        return '<h1>{}</h1>'.format(func(self, *args, **kwargs))
    return wrapper

class Per(object) :
    def __init__(self, name):
        self.name = name
    @tagH1
    def getName(self):
        return self.name

per = Per('YSP')
print('YSP - ', per.getName())


# Iterator
# 실행의 속도가 빨라짐
'''
- iterable 객체(iterable Object)
list, set, dict tuple - collection
Text Sequence

for ~ in collection:
    pass
    
- iterator -> 파이썬 모듈이 가지고 있는 내장함수 iter()
-> 순차적으로 다음 데이터를 리턴할 수 있는 객체
-> 내장함수 next() 사용해서, 순환하는 다음 값을 반환함    
'''
for num in [1,2,3,4,5]:
    print(num)

for char in 'text sequence' :
    print(char)

userList = [1,2,3,4,5]
print(next(userList))

userIterator = iter(userList)
print('type - ', type(userIterator), type(userList))
print(next(userIterator))


# 사용자 정의 iterator 클래스를 만들어 보자
class Counter:
    def __init__(self, stop):
        self.stop = stop
    def __iter__(self):
        return CounterIterator(self.stop)

class CounterIterator:
    def __init__(self, stop):
        self.current = 0
        self.stop = stop
    def __next__(self):
        if self.current < self.stop :
            rtnValue = self.current
            self.current += 1
            return rtnValue
        else:
            pass

cntIterator = iter(Counter(10))
print(next(cntIterator))


# Comprehension
'''
[ 출력표현식 for 요소 in sequence [if 조건식] ] 
{ 출력표현식 for 요소 in sequence [if 조건식] }    # python 3.0 over
{ key:value for 요소 in sequence [if 조건식] }    # python 3.0 over
'''
dataset = [ 4, True, 'YSP', 3.1, 10]
# 위 데이터 셋에서 정수값만 출력을 원한다면?
intType = [value ** 2 for value in dataset if type(value) == int]
print('int type - ', type(intType), intType)

dataset = [1,1,2,2,3,3,4,4]
setType = {value * value for value in dataset}
print('set type - ', type(setType), setType)

dataset = {1:'YSP', 2:'VICTORIA', 3:'LEMON'}
# print('dict keys - ', dataset.keys())
# print('dict values - ', dataset.values())
# print('dict items - ', dataset.items())

# key값이 1 이상인 데이터를 값:키 형식으로 새로운 set 만든다면?
new_style = { key for key, value in dataset if dataset.keys() >= 1 }
print(new_style)

keySet = { value:key for key, value in dataset.items() if key >1 }
print(keySet, type(keySet))

# key값을 10단위로 한번에 바꿔본다면?
keySet = { key*10:value for key, value in dataset.items() }
print(keySet, type(keySet))



# python Generator
# 루프의 작업을 컨트롤 하기 위해
# 코드 때문보다는 메모리의 성능 때문에 루프를 컨롤하기 위해 쓰여지는 루틴
# 적은 양의 메모리에서 대용량의 데이터를 핸들링 해야될 때
'''
iterator 를 만들어 주는 기능
yield 키워드의 이해가 필요
'''

def textSeqenceFunc():
    msg = 'hi python'
    for txt in msg:
        return txt
# print(textSeqenceFunc)
textSeqenceFunc()

charIte = iter(textSeqenceFunc())
print(type(charIte))
print(next(charIte))
'''
yield - 잠시 함수의 실행을 멈추고 호출한 곳에 값을 전달
- 현재 실행된 상태를 계속 유지할 수 있다
- 그러므로, 다시 해당 함수를 호출하면 현재 실행된 상태를 기반으로 다음코드를 실행
'''
def textSeqenceFunc():
    msg = 'hi python'
    for txt in msg:
        yield txt
# print(textSeqenceFunc)
print(textSeqenceFunc())

charIte = iter(textSeqenceFunc())
next(charIte)



def userGeneratorFunc(data) :
    result = []
    for tmp in data :
        result.append(tmp*2)
    return result

twiceList = userGeneratorFunc([1,2,3,4,5])
print('처리된 결과 - {}'.format(twiceList))



# generator 사용
def userGeneratorFunc(data) :
    for tmp in data :
        yield tmp*2

twiceList = userGeneratorFunc([1,2,3,4,5])
print(type(twiceList))
# print('next - {}'.format(next(twiceList)))
for t in twiceList:
    print(t)


# Generator Comprehension ()
# (Lazy Operation)
'''
syntax)
(출력형식 for 요소 in collection )
'''
squareDate = (num **2 for num in range(5))
print(type(squareDate))
print(squareDate)
# print(sum(squareDate))
for data in squareDate:
    print(data, end='\t')
```