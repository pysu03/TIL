# python control statement for looping
- for ~ in range()
- for ~ in list, dict
- fot ~ in enumerate(list)
```python
userSum = 0
for temp in range(1, 11, 2):
    #print(temp)
    #print(temp, end="\t")
    userSum += temp
print('누적 값은 : {}입니다.'.format(userSum))					 							누적 값은 : 25입니다.


userList = [1,2,3,4,5]
for tmp in userList:
    print(tmp, end='\t')																					1	2	3	4	5
    userSum += tmp
print()
print('누적 값은 : {}입니다.'.format(userSum))												누적 값은 : 40입니다.


userList = [(1,2),(3,4),(5,6)]
for tmp01, tmp02 in userList:
    print(tmp01, tmp02)
    userSum += tmp01 + tmp02
print()			# 루핑에서 연산을 한 싸이클 돌고 줄바꿈을 해주는 기능?! 
print('누적 값은 : {}입니다.'.format(userSum))												누적 값은 : 61입니다.


userDict = {'name' : 'jslim', 'gender' : 'm'}
for (key, value) in userDict.items():
    print("{}, {}".format(key, value))														name, jslim
																																	gender, m
scores = [100, 50, 80, 90, 70, 60]      # 리스트 값에 부여된 인텍스를 통해 인텍스-값을 짝지어 원하는 결과를 출력
for idx in range(len(scores)):
    userSum += scores[idx]
```
- %d, %s, %f
```python
print('scores 합 %d' % userSum)																		scores 합 450
```
### List Comprehension
리스트 안에서 for 구문을 통한 반복적인 표현식을 이용할 수 있다 if까지 가능

```python
userList = [1, 2, 3, 4, 5, 6, 7, 8, 9]

userList02 = [ tmp ** 2 for tmp in userList]
print(userList02)																							[1, 4, 9, 16, 25, 36, 49, 64, 81]

userList03 = [ tmp ** 2 for tmp in userList if tmp%2 == 0]
print(userList03)																							[4, 16, 36, 64]
```
### dict에서도 사용 가능
```python
userDict = {'TEST'+ str(tmp) : tmp ** 2 for tmp in range(1,10) }
print(userDict)																

{'TEST1': 1, 'TEST2': 4, 'TEST3': 9, 'TEST4': 16, 'TEST5': 25, 'TEST6': 36, 'TEST7': 49, 'TEST8': 64, 'TEST9': 81}
```