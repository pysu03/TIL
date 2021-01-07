# python bool 타입의 특징
- bool
- True(T), False(F)
- not, and, or			 -> 논리연산
- &, |, ~      				-> 비교연산
### 파이썬이 다른 언어에 비해 갖는 특징
#### False로 간주
- ""(비어있는 문자열), [](비어있는 리스트), ()(비어 있는 튜플), {}(비어있는 딕션너리) ,None
- 숫자(0 이외의 숫자는 True)
```python
xValue = 5   																									  #  0101
yValue = 0   																									  #  0000

print( xValue & yValue)   																		0 # 0101 & 0000  -> 0000 -> 0
print( bool ( xValue & yValue ) )															False

print( xValue | yValue)																				5 # 0101 & 0000  -> 1010 -> 5
print( bool ( xValue | yValue ) )															True

trueValue  = True																							
falseValue = False																						

print(int(trueValue))																					1
print(int(falseValue))																				0

print(trueValue & falseValue)																	False
print(trueValue | falseValue)																	True

print('and - ', trueValue and falseValue)											and -  False
print('or - ' , trueValue or falseValue)											or -  True
print('not - ', not trueValue)																not -  False
```