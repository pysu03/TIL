```
'''
학습목표
-Composition == Aggregation
    상속이 다른 클래스의 일부 기능을 가져다 쓰고 싶을 때
    상속을 피하고 클래스의 일부 가능을 그대로 활용하고 싶을 때
-Exception
-File 입출력
'''

class Calc01(object) :
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def add(self):
        return self.x + self.y
    def substract(self):
        return self.x - self.y

class Calc02(object):
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def add(self):
        return self.x + self.y
    def multiply(self):
        return self.x * self.y

# > Calc02 multiply 만 사용하고 싶을 때
class UserCalc :
    def __init__(self, x, y):
        self.x = x
        self.y = y
        self.cal02 = Calc02(x,y)        # 객체를 명시적으로 생성

    def add(self):
        return self.x + self.y

    def substract(self):
        return self.x - self.y

    def multiply(self):
        return self.cal02.multiply()

calc = UserCalc(3,4)
print('calc multiply - ', calc.multiply())


'''
- 예외(Exception) - xxxError ex) SyntaxError, TypeError, NameError, IndexError, ValueError, KeyError ...
- 처리할 수 있는 구문
try     :
    에러가 발생 할 가능성이 있는 코드
    정상코드
    에러가 발생 할 가능성이 있는 코드
    정상코드
except  xxxError  :
    발생 된 에러를 잡기 위한 객체를 정의
        1. 프로그램의 흐름을 정상으로 컨트롤
        2. 예외발생의 디버깅
        3. 로그파일을 만들어서 예외정보를 저장
except  xxxError  : 
    발생 된 에러를 잡기 위한 객체를 정의
else    :
    에러가 발생되지 않을 때 실행되는 블럭
finally :
    예외 발생과 상관없이 무조건 수행 
'''
# print('error)

# a = 10
# b = 20
# print

# print(100/0)

# x = [1,2,3]
# print(x[3])

# dict = {'name':'YSP', 'age':31, 'city':'seoul'}
# print(dict['hobby'])
# print(dict.get('name'))

# import time
# print(time.time2())

# 예외가 없는 것을 가정하고 프로그램 작성 -> 런타임 예외 발생시 예외처리를 권장

def userKeyIn():
    try :
        age = int(input('본인의 나이를 입력하세요.'))
    except Exception as e :            # as 는 별칭 , 에러 종류를 맞춰 줘야 예외처리가 작동함, 근데 Exception 쓰면 다됨
        print('error = ', e)
        # print('문자열이 아닌 정수를 입력해 주세요.')
        # userKeyIN()
    else:
        print('age - ', age)
        print('함수 실행 종료')
    finally:
        print('넌 너무 지조가 없다... 항상 실행되니까')

userKeyIn()



nameList = ['Kim', 'Lee', 'Park', 'Lim']
try :
    name = 'Kim'
    idx = nameList.index(name)
except Exception as e :
    print('{} Not Found it !!'.format(name))
else:
    print('{} Found it !! {}'.format(name, idx + 1))
# finally:
#     print('에외 여부와 상관없이 항상 실행되는 블럭')
print('프로그램 종료')

# 사용자 정의 예외 클래스 작성
class InsufficientError(Exception) :
    def __init__(self, msg):
        self.msg = msg


# 클래스에 정의된 함수에 예외처리 적용 및 강제 예외 발생
class Account:
    def __init__(self, account, balance, interestRate):
        self.account      = account
        self.balance      = balance
        self.interestRate = interestRate

    def withDraw(self, amount):
        try:
            if self.balance  < amount :
                raise InsufficientError('잔액이 부족합니다.')             # raise 예외 강제 발생 키워드
        except Exception as e:
            print('error msg - ', e)
        else :
            self.balance -= amount

    def withDraw02(self, amount):
        if self.balance  < amount :
                raise InsufficientError('잔액이 부족합니다.')             # raise 예외 강제 발생 키워드
        else :
            self.balance -= amount

# account = Account('110-12-1343432', 100000, 0.073)
# account.withDraw(200000)
# print('프로그램 종료')
account = Account('110-12-1343432', 100000, 0.073)
try:
    account.withDraw02(200000)
except:
    print(str(e))
print('프로그램 종료')



'''
# namedtuple
객체생성 - 클래스(변수, 함수)
클래스 없이 객체를 생성하는 방법(변수)
usage)
collections.namedtuple('실제 클래스 이름', (변수) [변수] )
'''
import collections

#Person = collections.namedtuple('Person', ['name', 'id'])    # 리스트 형식
Person = collections.namedtuple('Person', 'name id')          # 튜플로 형식
Person = collections.namedtuple('Person', 'name, id')         # str 형식
per = Person('YSP', '100')
print(per, type(per))

Emp = collections.namedtuple('Person', 'name, id')
per = Emp('YSP', '100')
print(per, type(per))

# 속성에 접근
print('inx 0 - ',per[0])
print('inx 1 - ',per[1])

for idx in range(len(per)) :
    print('idx {} - {} '.format(idx, per[idx]))

# 속성에 접근 2
print(per.name)
print(per.id)

# 속성에 접근 3
name, id = per
print(name, id)

'''
1. 직장인 이름, 나이, 부서 속성으로 갖는 클래스 만들기
2. 직장인 이름, 나이, 부서 속성으로 갖는 클래스를 namedtuple로 만들기
'''
class Emp :
    def __init__(self, name, age, dept):
        self.name = name
        self.age  = age
        self.dept = dept

import collections
Emp = collections.namedtuple('Emp', 'name age dept')
emp = Emp('apple', 31, 'HRD')
print(emp.name, emp.age, emp.dept)
```