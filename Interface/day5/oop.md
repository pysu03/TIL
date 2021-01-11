# python 객체지향 프로그래밍 (oop)
- 패키지(package) >모듈(module) > 클래스(class) - 함수를 담을 수 있는 개념 > 함수
- Object Oriented Programing (OOP)

Real World         추상화(템플릿)         Programing World
Object    ---------- class ------------>  instance
명사적 특징      ----   변수
동사적 특징      ----   함수
                                                         *클래스에 정의 되어진 변수나 함수는 instance의 소유*

```python
# 학색의 정보를 저장할려고 합니다.
stuName  = 'ys'
stuMajor = 'computer'
stuID    = '6666'
stuGrade = 4.5

# 추천하지 않는다
list = [ ]
dict = { }
```
#### class를 이용해서 한 학생의 데이터를 논리적인 하나의 단위로 묶어서 사용
- class vs instance
- namespace : 객체를 인스턴스화할 때 저장된 공간
- class variable : 직접 접근가능 및 공유
- instance variable : 객체소유로 별도 존재
- self : instance 소유의 멤버라는 걸 명시한다
- cls : class  소유의 멤버라는 걸 명시한다
#### class
- 함수의 모임

- 역할 : 여러개의 함수와 데이터를 묶어서 객체 생성할 수 있는 뎀플릿

- 구성 : 멤버 = 변수(데이터) + 매서드(함수), 생성자(초기화)

- 형식 : class 클래스이름 :
                             변수                    - 자료저장
                             초기화                 - 객체생성시 호출되는 함수          
                                        
          ​                   def 함수이름( ) :   - 자료처리 

- class 의 첫 문자는 대문자로

```python
일반적인 형식)
class Calc :
    x = 0                                                                         # 변수
    y = 0                                                                         # 변수

    def __init__(self):                                                           # 초기화함수
        print('객체 생성시 호출되는 함수이고 난 초기화라고 불리죠.')

    def plus(self):                                                               # 사용자정의 함수
        print('사용자 정의 함수이고 전 이스턴스의 소유가 됩니다.')

# instance 생성하는 문법
obj = Calc()
obj.plus()
     
 ex) 1단계
class Student :

    def __init__(self, name, major, num, grade):
        self.name  = name
        self.major = major
        self.num   = num
        self.grade = grade


stu01 = Student('ys','management', 2012, 4.5)
print(stu01)															<__main__.Student object at 0x7fcd8553a070>
print(stu01.name)													이렇게 출력되지 않게 하기 위해서 'def __repr__(self):' 사용
print(stu01.major)
print(stu01.num)
print(stu01.grade)

-------------------------------------------------------------------------------------------
2단계)
class Student:

    def __init__(self, name, major, num, grade):
        self.name = name
        self.major = major
        self.num = num
        self.grade = grade

    def __repr__(self):
        return self.name + "\t" + self.major + "\t" + self.num + "\t" + str(self.grade)

stu01 = Student('ys','management', '2012', 4.5)
print(stu01)																											ys	management	2012	4.5
-------------------------------------------------------------------------------------------
# 함수 정의시 팁
user define function
- setXXXX		 속성을 설정
- getXXXX		 속성을 가져오기
- isXXXXX		 T/F 판정

3단계)
class Student:

    def __init__(self, name, major, num, grade):
        self.name = name
        self.major = major
        self.num = num
        self.grade = grade

    def __repr__(self):
        return self.name + "\t" + self.major + "\t" + self.num + "\t" + str(self.grade)

    def getInfo(self):
        return '이름 : {} \t 전공 : {}'.format(self.name, self.major)

stuList = []
stu01 = Student('xxx', 'xx', '0000', 1.0)
stu02 = Student('yyy', 'yy', '1111', 2.0)
stu03 = Student('zzz', 'zz', '2222', 3.0)

stuList.append(stu01)
stuList.append(stu02)
stuList.append(stu03)
for stu in stuList:
    print(stu.getInfo())
                                   		                 이름 : xxx 	 전공 : xx
                                                       이름 : yyy 	 전공 : yy
                                                       이름 : zzz 	 전공 : zz
# print(id(stu01), id(stu02), id(stu03))							id 값 확인 가능?
```

### 인스턴스 소유의 변수가 아닌 클래스 소유의 변수
```python
class Student:

    scholarshipRate = 3.5 															# class variable(클래스 소유)

    def __init__(self, name, major, num, grade):
        self.name = name
        self.major = major
        self.num = num
        self.grade = grade

    def __repr__(self):
        return self.name + "\t" + self.major + "\t" + self.num + "\t" + str(self.grade)

    def getInfo(self):
        return '이름 : {} \t 전공 : {}'.format(self.name, self.major)

    def isScholarShip(self):
        if self.grade >= Student.scholarshipRate:				#
            return True
        else:
            return False


stu01 = Student('이중헌', '기계공학', '2010', 4.0)
print('장학금 여부 - ', stu01.isScholarShip(), Student.scholarshipRate)	     장학금 여부 -  True 3.5

# namespace( instance -> class -> super class)
Student.scholarshipRate >> self.scholarshipRate 써도 작동되는 이유는 namespace에 남아 있 데이터 때문?
권장은 Student.scholarshipRate 요렇게 쓰자
```

### 인스턴스 소유가 아닌 class method
```python
# self로 표현 되지 않음
# 클래스함수 cls인 인자를 받고 모든 인스턴스가 공유하는 클래스 변수와 같은 데이터를 생성, 변경 또는 참조하기 위해서 사용
기본)
class Employee :
    def __init__(self, name, salary):
        self.name   = name
        self.salary = salary
    def getSalary(self):
        return '현재 {}님의 급여는 {}입니다.'.format(self.name, self.salary)

emp01 = Employee('name', 1000)
print('인상 전 급여 - ', emp01.getSalary())							인상 전 급여 -  현재 name님의 급여는 1000입니다.
```
```python
cls 사용)
# @classmethod 이거 써줘야함

class Employee :

    raiseRate = 1.1  # 급여인상률 class variable (클래스 소유라는 뜻 )
    
    def __init__(self, name, salary):
        self.name   = name
        self.salary = salary
    def getSalary(self):
        return '현재 {}님의 급여는 {}입니다.'.format(self.name, self.salary)
    
    @classmethod																															#
    def updateRate(cls, rate):
        cls.raiseRate = rate
        print('인상률이 {}로 변경되었습니다.'.format(rate))
    
    def applyRaise(self):
        self.salary = int(self.salary * Employee.raiseRate)

emp01 = Employee('name', 1000)
print('인상 전 급여 - ', emp01.getSalary())							인상 전 급여 -  현재 name님의 급여는 1000입니다.

Employee.updateRate(1.5)															인상률이 1.5로 변경되었습니다.
emp01.applyRaise()

print('인상 후 급여 - ', emp01.getSalary())							인상 후 급여 -  현재 name님의 급여는 1500입니다.
```
### @staticmethod
```python
class Employee :

    raiseRate = 1.1  # 급여인상률 class variable (클래스 소유라는 뜻 )

    def __init__(self, name, salary):
        self.name   = name
        self.salary = salary
    def getSalary(self):
        return '현재 {}님의 급여는 {}입니다.'.format(self.name, self.salary)

    @classmethod
    def updateRate(cls, rate):
        cls.raiseRate = rate
        print('인상률이 {}로 변경되었습니다.'.format(rate))

    def applyRaise(self):
        self.salary = int(self.salary * Employee.raiseRate)

    # static 함수
    @staticmethod
    def isValid(salary):
        if salary < 0 :
            print('음수가 될 수 없습니다.')

emp01 = Employee('name', 1000)
print('인상 전 급여 - ', emp01.getSalary())

Employee.updateRate(1.5)
emp01.applyRaise()

print('인상 후 급여 - ', emp01.getSalary())

Employee.isValid()
```