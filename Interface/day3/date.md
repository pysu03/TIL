# python date type
```python
from datetime import date, datetime

today =date.today()
print('date - ', type(today), today, today.year, today.month, today.day)
	date -  <class 'datetime.date'> 2021-01-07 2021 1 7
print('년도 {}, 월 {}, 일 {}'.format(today.year, today.month, today.day))
	년도 2021, 월 1, 일 7
print(' {}년도, {}월, {}일'.format(today.year, today.month, today.day))
	 2021년도, 1월, 7일
```
### 시간
```python
todatDateTime = datetime.today()
print('datetime - ', todatDateTime)										datetime -  2021-01-07 16:41:16.023453
print('{}시, {}분, {}초'.format(todatDateTime.hour, todatDateTime.minute, todatDateTime.second))
																											16시, 41분, 16초
```
### <pip | conda install>
- pip   딱 A만 인스톨
- conda 의존관계에 있는 것까지 인스톨
### dateutil
- 기본패키지가 아니여서 인스톨이 필요함
- 옵션 >> project >> pyrhon interpreter >> + >> 검색 >> install
```python
from datetime import date, datetime, timedelta
from dateutil.relativedelta import relativedelta
```
### timedelta - weeks, days, minutes, seconds
```python
today = date.today()                               # print(today + 1)  날짜형식의 연산이 안됌
days = timedelta(days=-1)                          # timedelta 날찌에 옵션을 줄 수 있는 함수
print('오늘 이전 하루 - {}'.format(today+days))				오늘 이전 하루 - 2021-01-06
```
### relativedelta
- year, month 관련된 옵션을 필요로 하다면
```python
days = relativedelta(months=-2)
print('두달 전 오늘 - {}'.format(today+days))				두달 전 오늘 - 2020-11-07

days = relativedelta(years=-1)
print('일년 전 오늘 - {}'.format(today+days))				일년 전 오늘 - 2020-01-07
```
### 특정한 날짜
```python
from dateutil.parser import parse

userDate = parse("2021-06-04")
print('parse date - ',userDate, type(userDate))
															parse date -  2021-06-04 00:00:00 <class 'datetime.datetime'>
userDate = datetime(2021, 12, 25)
print('datetine date - ',userDate, type(userDate))
															datetine date -  2021-12-25 00:00:00 <class 'datetime.datetime'>
```
### 날짜 객체의 출력형식을 원하는 것으로 변경
```python
today = datetime.today()
```
### 날짜형식 -> 문자열형식의 포맷으로 지정
- strftime( )
```python
print("{}".format(today.strftime('%m-%d-%y')))		 															 01-07-21
print("{}".format(today.strftime('%m-%d-%Y')))  # 소문자y는 2자리 대문자Y는 4자리				01-07-2021
```
### 문자열형식 -> 날짜형식
- strptime()
```python
strDate  = '2021,01,06-11:12:40'
userDate = datetime.strptime(strDate , '%Y,%m,%d-%H:%M:%S')
print(type(userDate), userDate)									<class 'datetime.datetime'> 2021-01-06 11:12:40
```