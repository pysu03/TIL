# control statement
- if (조건문), for(반복문), while(반복문)

### 사용자 입력 함수
- input()
```python
name    = input("Enter your Name : ")									Enter your Name 	 : >? YS
grade   = input("Enter your Grade : ")								Enter your Grade 	 : >? A+
company = input("Enter your Company : ")							Enter your Company : >? EENHASU
print(name, grade, company)														YS A+ EENHASU
```
### if, if ~else, if ~ elif ~ else
- bool True | False
### 짝수인지 홀수인지를 판별?
```python
inputNumber = int(input("Enter your digit(1~100) : "))
if inputNumber%2 == 0:
    print('짝수입니다.')
else:
    print('홀수입니다')
   
Enter your digit(1~100) : >? 29                    								  홀수입니다
```
### 값이 3의 배수인지 5의 배수인지를 판별하고 싶다면?
```python
number = 15
if (number%3 == 0 & number%5 == 0):
    print('{}은 3 과 5의 배수입니다.'.format(number))
else:
    print('{}은 3 과 5의 배수가 아닙니다.'.format(number))
    																																15은 3 과 5의 배수입니다.
```
- if ~ elif
```python
if number%3 == 0:
    print('{}은 3의 배수입니다.'.format(number))
elif number%5 ==0:
    print('{}은 5의 배수입니다.'.format(number))
else :
    print('{}은 3과 5의 배수가 아닙니다.'.format(number))
```
### 윤년의 조건
- 4의 배수이고, 100의 배수가 아니거나
- 400의 배수일 때를 윤년으로 본다면
```python
year = 2021
if (year%4 == 0 and year%100 !=0) or (year%400 == 0) :
    print('{}년은 윤년입니다.'.format(year))
else :
    print('{}년은 윤년이 아닙니다.'.format(year))															2021년은 윤년이 아닙니다.
```
### if구문을 사용하여 년도와 월을 입력받아서 월의 마지막 일을 출력한다면?
```python
year  = int(input('년도를 입력하세요 : '))
month = int(input('달을 입력하세요 : '))
year_month      = [31,28,31,30,31,30,31,31,30,31,30,31]
leap_year_month = [31,29,31,30,31,30,31,31,30,31,30,31]

if (year%4 == 0 and year&100 !=0):
    print('{}년 {}월의 마지막 일은 {}일 입니다.'.format(year, month, leap_year_month[month -1]))
elif (year%400 == 0) :
    print('{}년 {}월의 마지막 일은 {}일 입니다.'.format(year, month, leap_year_month[month -1]))
else:
    print('{}년 {}월의 마지막 일은 {}일 입니다.'.format(year, month, year_month[month -1]))
    
년도를 입력하세요	:  >? 1403
달을 입력하세요	 : >? 3
1403년 3월의 마지막 일은 31일 입니다.
```
### list if ~ in
```python
area = ['서울', '부산', '제주', '광주']
region = '수원'
if region in area :
    pass
else:
    print('{}지역은 포함되지 않습니다.'.format(region))			  							수원지역은 포함되지 않습니다.
```
### dict을 이용한 if ~ in
```python
areaKeyDict = {'서울' : 100, '광주' : 200}
region = '부산'
if region in areaKeyDict:
    pass
else:
    print('{} 값이 존재하지 않습니다.'.format(region))							부산 값이 존재하지 않습니다.

city = ""
if city:
    print('true - ', city)
else:
    print('false - ', 'Please enter your city')								false -  Please enter your city

city = []
if city:
    print('true - ', city)
else:
    print('false - ', 'Please enter your city')								false -  Please enter your city

city = ()
if city:
    print('true - ', city)
else:
    print('false - ', 'Please enter your city')								false -  Please enter your city

city = {}
if city:
    print('true - ', city)
else:
    print('false - ', 'Please enter your city')								false -  Please enter your city

city = 10
if city:
    print('true - ', city)
else:
    print('false - ', 'Please enter your city')								10

city = 'xxx'
if city:
    print('true - ', city)
else:
    print('false - ', 'Please enter your city')								xxx
```
### 삼항 연산자
```python
num    = 7
result = 0

result = num * 2 if num > 5 else num + 2           #  조건 만족 if 조건 else 조건 만족 X
print('삼항 연산자 - ', result)											삼항 연산자 -  14
```