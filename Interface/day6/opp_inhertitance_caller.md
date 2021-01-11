### 상속
```python
from ai.oop.opp_inheritance import *													# from ai.oop import opp_inheritance as oop

# car01 = oop.Car
# car01 = Car('GV70', 4, 2400)
# car01.carInfo()

# parent = Parent('부모', '공무원')
# print('parent - ', parent.display())

# child01 = Child01('자식', '강사', 49)
# child01.childInfo()
# print(child01.childInfo())

stu01 = StudentVO('ys', 31, 'seoul', 2012)
print('student info - ', stu01.stuInfo())

tea01 = TeacherVO('Sr.ys', 51, 'seoul', 'python')
print('teacher info - ', tea01.teaInfo())

emp01 = ManagerVO('장호연', 29, 'seoul', 'HRD')
print('manager info - ', emp01.empInfo())

userDate = MyDate()
# userDate.Year() = -2012
userDate.setYear(-2012)
print(userDate.getYear())

hiding = HidingClass('라이언', '교육팀', 100)
print('utype - ', hiding.utype)
print('name - ', hiding.name)
# print('dept - ', hiding.__dept)
print('num - ', hiding.num)

print('call getDept - ', hiding.getDept())
print('call __getInfo - ', hiding.__getInfo())
```
### 다형성
```python
stu01 = StudentVO('ys   ', 31, 'seoul', 2012)
tea01 = TeacherVO('Sr.ys', 51, 'seoul', 'python')
emp01 = ManagerVO('장호연', 29, 'seoul', 'HRD')

perList = []
perList.append(stu01)
perList.append(tea01)
perList.append(emp01)
print('perList - ', perList)

for obj in perList :
    # if isinstance(obj, StudentVO) :
    #     print(obj.stuInfo())
    # elif isinstance(obj, TeacherVO) :
    #     print(obj.teaInfo())
    # else :
    #     print(obj.empInfo())
    print(obj.perInfo())
```
### [실습]
```python
## Account Caller
# account = Account('441-23-1234567', 500000, 0.073)
# account.accountInfo()
# account.withDraw(600000)
# account.deposit(200000)
# account.accountInfo()
# account.withDraw(600000)
# account.accountInfo()
# print('현재 잔액의 이자를 포함한 금액')
# account.printInterestRate()


account = FundAccount('441-23-1234567', 500000, 0.073, 'F')

account.accountInfo()
account.withDraw(600000)
account.deposit(200000)
account.accountInfo()
account.withDraw(600000)
account.accountInfo()
print('현재 잔액의 이자를 포함한 금액')
account.printInterestRate()
```