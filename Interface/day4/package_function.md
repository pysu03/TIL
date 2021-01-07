
### 매개변수 X, 리턴값이 X
```python
def printCoins():
    print('bitcoin')
```
### 매개변수 X, 리턴값이 O
```python
def returnFunc():
    return '호출한 쪽으로 값이 전달됩니다.'
```
### 매개변수 O, 리턴값이 O
```python
def sayEcho(name):
    return name+'님, 반갑습니다.'

def calculator(op01, perator, op02):
    pass

def makerUrl(url):
    return "www."+url+".com"
```
### 매개변수 O, 리턴값이 X
```
def badFunc(name):
    pass
```
### 매개변수에 튜플이 들어갈 때

```python
def tupleFunc(*args):                       # *튜플형식

#    result = 0
#
#    return result


def tupleFunc(*args):
    result = 0
    for idx in range(len(args)):
        result += args[idx]
    return result
```
### 매개변수에 딕션너리가 들어갈 때
``` python
def dictFunc(**args):
    for key, value in args.items():
        print('{} = {}'.format(key,value))
```
### 범위내에 있는 값의 홀, 짝의 합을 구해서 리턴
```python
def cntSum(start, end):
    odd = even = 0
    for x in range(start, end+1):
        if x%2 == 0:
            even += x
        else:
            odd += x

    return odd, even
```
### 윤년 찾기
```python
def leapYearFunc(strYear, endYear):
    yearList = []
    for year in range(strYear, endYear+1) :
        if (year%4 == 0 and year%100 != 0) or (year%400 == 0) :
           yearList.append(year)
    return yearList
```
### 

```python
def rtnDictFunc(x):
  y01 = x * 10
  y02 = x * 20
  y03 = x * 30
  return {'cal01' : y01, 'cal02' : y02,'cal03' : y03}
```