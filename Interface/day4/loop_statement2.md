### 단어의 빈도수 구하기
```python
wordVec = ["love", "word", "cat", "love","love", "word"]
print(len(wordVec))															6

wordCnt = {}
for word in wordVec:
    wordCnt[word] = wordCnt.get(word, 0) + 1
# get() : 해당 key의 value값을 가져오는 함수
print(wordCnt, type(wordCnt))										{'love': 3, 'word': 2, 'cat': 1} <class 'dict'>

wordCnt02 = {}
for word in wordVec:
    if word in wordCnt02:
        wordCnt02[word] += 1
    else:
        wordCnt02[word] = 1
print(wordCnt, type(wordCnt))	   								{'love': 3, 'word': 2, 'cat': 1} <class 'dict'>
# [], (), {}, {key:value}
```
### 1~ 1000 합
```python
rangeSum = 0
for value in range(1, 1001):
    rangeSum += value
print('1~1000의 합은 {}입니다.'.format(rangeSum))													1~1000의 합은 500500입니다.
```
### 2000 ~ 2050년까지의 올림픽이 개최되는 년도를 출력하라
- 단, 한 줄에 5개의 년도를 출력하고 개행
```python
for year in range(2000, 2051, 4):
    print(year, end="\t")
    
2000	2004	2008	2012	2016	2020	2024	2028	2032	2036	2040	2044	2048	

cnt = 0
for year in range(2000, 2051, 4):
    cnt+= 1
    print(year, end="\t")
    if cnt % 5 == 0:
        print()

2000	2004	2008	2012	2016	
2020	2024	2028	2032	2036	
2040	2044	2048
```
### 아래 리스트에서 세 글자 이상의 단어만 출력하라..
```python
wordList = ['I', 'am', 'study', 'python', 'language', '!']
for word in wordList:
    #print(len(word))
    if len(word) >= 3:
        print(word)
        
study
python
language      
```
### 대문자만 출력
```python
wordList = ['I', 'am', 'study', 'PYTHON', 'language', 'IF', 'for']
for word in wordList:
    if word .isupper() :                                       #.is-() 보통 is-는 -를 판별할 때 사용
        print(word)
        
I
PYTHON
IF
```
### 첫 글자를 대문자로
```python
wordList = ['dog', 'cat', 'pig', 'carrot', 'horse']
for word in wordList:
    print(word.capitalize())
    
Dog
Cat
Pig
Carrot
Horse
```
### 해당 파일의 확장자를 제거하고 파일 이름만 출력한다면?
- hint - split('.')
```python
fileList = ['greeting.py', 'bool.py', 'intro.hwp', 'bigdata.doc', 'ai.doc']
for file in fileList:
    print(file.split('.')[0])

    
greeting
bool
intro
bigdata
ai

#
word = 'HandSome Boy'
for w in word:
    if w.isupper():
        print(w, end=',')

H,S,B,
```
### 주어진 문장에서 모든 문자를 대문자로 출력한다면?
```python
dumySen = 'FasdfAdsfAsFDSerwdARfdsf'
#내가 생각해본 것
for D in dumySen:
    print(D.capitalize(), end='')															FASDFADSFASFDSERWDARFDSF
# 문장 전체를 대문자로
for D in dumySen:
    print(D.upper(), end='' )																	FASDFADSFASFDSERWDARFDSF
# 문장 안에서 소문자인것만 대문자로
for D in dumySen:
    if D.isupper():
        print(D, end='')
    else:
        print(D.upper(), end='')															FASDFADSFASFDSERWDARFDSF
```
### 역순
```python
wordList = ['가', '나', '다', '라']
for word in wordList[::-1]:
    print(word)

라
다
나
가

# 내가 생각해본 것
wordList = ['가', '나', '다', '라']
#wordList.reverse()
print(wordList.reverse())
```
### break		특정 조건을 만족 하면 스탑
### continue	특정 조건을 만족키시면 만족하는 조건을 스킵하고 루핑을 돔

```python
search =17
numbers = [14, 3, 4, 7, 10, 24, 17, 2, 33, 15, 34, 36, 38]
for num in numbers:
    if num == search:
        #continue
        print('Found - ', num)
        break
    else:
        print('Not Found - ', num)

Not Found -  14
Not Found -  3
Not Found -  4
Not Found -  7
Not Found -  10
Not Found -  24
Found -  17        
        
        
# for ~ else
search =5
numbers = [14, 3, 4, 7, 10, 24, 17, 2, 33, 15, 34, 36, 38]
for num in numbers:
    if num == search:
        print('Found - ', num)
        break
else:
    print('Not Found - ', search)
    
Not Found -  5
```

### 이중 루핑
```python
for i in range(1, 6):
    for j in range(1, 4):
        print('i - {}, j - {}'.format(i,j))

i - 1, j - 1
i - 1, j - 2
i - 1, j - 3
i - 2, j - 1
i - 2, j - 2
i - 2, j - 3
i - 3, j - 1
i - 3, j - 2
i - 3, j - 3
i - 4, j - 1
i - 4, j - 2
i - 4, j - 3
i - 5, j - 1
i - 5, j - 2
i - 5, j - 3

# 구구단
for i in range(2, 10):
    for j in range(1,10):
        print('{} X {} = {}'.format(i,j,(i*j)), end='\t')
    print()
    if i == 5:
        break
        
2 X 1 = 2	2 X 2 = 4	2 X 3 = 6	2 X 4 = 8	2 X 5 = 10	2 X 6 = 12	2 X 7 = 14	2 X 8 = 16	2 X 9 = 18	
3 X 1 = 3	3 X 2 = 6	3 X 3 = 9	3 X 4 = 12	3 X 5 = 15	3 X 6 = 18	3 X 7 = 21	3 X 8 = 24	3 X 9 = 27	
4 X 1 = 4	4 X 2 = 8	4 X 3 = 12	4 X 4 = 16	4 X 5 = 20	4 X 6 = 24	4 X 7 = 28	4 X 8 = 32	4 X 9 = 36	
5 X 1 = 5	5 X 2 = 10	5 X 3 = 15	5 X 4 = 20	5 X 5 = 25	5 X 6 = 30	5 X 7 = 35	5 X 8 = 40	5 X 9 = 45
```
### 단어 구분
```python
string ='''저는 여러분과 함께 파이썬 강의중에 있는 섭섭해님 입니다. ^*^
어려운 시기에 함께하게되어서 반갑습니다.
나이는 숫자에 불과하지만 성인병이 있네요.~~~'''
sentences = []
words     = []
# append(), insert(), extend()
for s in string.split('\n'):
    sentences.append(s)
    for w in s.split():
        words.append(w)
print(sentences, len(sentences))
print(words, len(words))

['저는 여러분과 함께 파이썬 강의중에 있는 섭섭해님 입니다. ^*^', '어려운 시기에 함께하게되어서 반갑습니다.', '나이는 숫자에 불과하지만 성인병이 있네요.~~~'] 3
['저는', '여러분과', '함께', '파이썬', '강의중에', '있는', '섭섭해님', '입니다.', '^*^', '어려운', '시기에', '함께하게되어서', '반갑습니다.', '나이는', '숫자에', '불과하지만', '성인병이', '있네요.~~~'] 18
```
### 분류정확도
```python
answer  = [1,0,2,1,0]
predict = [1,0,2,0,0]
acc = 0
for idx in range(len(answer)):
    fit = answer[idx] == predict[idx]
    #print(fit, end='\t)
   # print(int(fit), end='\t')
    acc += int(fit) * 20

print('classification accuracy - ', acc,'%')										classification accuracy -  80 %
```
### enumerate
- 반복문 사용시 몇 번째 반복문인지 확인이 필요하다면
- 인덱스 번호와 컬레션 요소를 확인 할 수 있다.
```python
bookList = ['SQL', 'R', 'TEXT-MINING', 'NLP', 'DATA-MINIG', 'PYTHON', 'DJANGO']
for idx, book in enumerate(bookList):
    print('index - {}, value - {}'.format(idx+1, book))
    
index - 1, value - SQL
index - 2, value - R
index - 3, value - TEXT-MINING
index - 4, value - NLP
index - 5, value - DATA-MINIG
index - 6, value - PYTHON
index - 7, value - DJANGO
```
### while
```python
syntax)
while <expression>:
  statement
  증감식             # 증감식이 없으면 무한루프됨 
	
cnt = 5
while cnt > 0:
    print(cnt)
    cnt = cnt -1
    print('cnt - ',cnt)
    
5
cnt -  4
4
cnt -  3
3
cnt -  2
2
cnt -  1
1
cnt -  0    
```
### list - pop()
```python
whileList = ['foo', 'bar', 'baz']
while whileList:
    print(whileList.pop())
    print('whileList - ', whileList)
print('while - end')

baz
whileList -  ['foo', 'bar']
bar
whileList -  ['foo']
foo
whileList -  []
while - end
```
### 난수를 발생시켜서 횟수내에 맞추는 게임
```python
import random

ran = random.random()						 # 0~1 사이의 난수를 발생시키는데 (실수형)
print('random - ', ran)																						random -  0.6369072158493362

ran = random.randint(0,2)				 # 정수형
print('random - ', ran)																						random -  1

숫자 범위 : 1 ~ 10
내가 입력한 숫자 > 난수 : 더 작은 수를 입력
내가 입력한 숫자 < 난수 : 더 큰 수를 입력

randNum = random.randint(1,10)
while True:
    guessNum = int(input('예상 숫자를 입력하세요 : '))
    if randNum == guessNum:
        print('succes!!')
        break
    elif randNum > guessNum:
        print('더 큰 수를 입력하세요.')
    else:
        print('더 작은 수를 입력하세요.')
        
        
예상 숫자를 입력하세요 : >? 4
더 큰 수를 입력하세요.
예상 숫자를 입력하세요 : >? 10
더 작은 수를 입력하세요.
예상 숫자를 입력하세요 : >? 9
더 작은 수를 입력하세요.
예상 숫자를 입력하세요 : >? 8
더 작은 수를 입력하세요.
예상 숫자를 입력하세요 : >? 7
더 작은 수를 입력하세요.
예상 숫자를 입력하세요 : >? 6
succes!!
```
### GUESS GAME
- 1 ~ 100 사이의 난수를 발생시킨다
- 도전 횟수는 20회 제한
- 출력 결과로는 
- ->정답 시도횟수
- ->정답
```python
from random import randint

randNum = randint(1,100)
tries = 1
while tries <= 20:
    guessNum = int(input('예상 숫자를 입력하세요 : '))
    if randNum == guessNum:
        print('succes!!')
        break
    elif randNum > guessNum:
        print('더 큰 수를 입력하세요.')
    else:
        print('더 작은 수를 입력하세요.')
    tries += 1
if guessNum == randNum:
    print('정답 시도횟수 {}'.format(tries))
    print('정답 {}'.format(randNum))
else:
    print('정답 {}'.format(randNum))
    
예상 숫자를 입력하세요 : >? 50
더 작은 수를 입력하세요.
예상 숫자를 입력하세요 : >? 25
더 큰 수를 입력하세요.
예상 숫자를 입력하세요 : >? 37
더 큰 수를 입력하세요.
예상 숫자를 입력하세요 : >? 45
더 작은 수를 입력하세요.
예상 숫자를 입력하세요 : >? 50
더 작은 수를 입력하세요.
예상 숫자를 입력하세요 : >? 38
더 큰 수를 입력하세요.
예상 숫자를 입력하세요 : >? 39
더 큰 수를 입력하세요.
예상 숫자를 입력하세요 : >? 40
더 큰 수를 입력하세요.
예상 숫자를 입력하세요 : >? 42
더 작은 수를 입력하세요.
예상 숫자를 입력하세요 : >? 41
succes!!
정답 시도횟수 10
정답 41
```
### choices()
```python
dataSet = list(range(1,1001))
print(dataSet)
# 모집단 dataser에서 k개의 데이터를 샘플링하고 싶다면?
train = random.choices(dataSet, k=10)
print('sample dataser - ', train)

sample dataser -  [208, 262, 120, 846, 314, 121, 69, 59, 257, 148]
```