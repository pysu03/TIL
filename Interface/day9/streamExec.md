
### binary 형식의 입출력     # binary = 이진값
- 객체 직렬화(Serializable)  >> 객체 자체를 파일로 저장
- pickle : 객체직렬화를 도와주는 모드

### socres 객체 정보를 xxxx.txt파일로 저장
```python
scores = {'kor':90, 'eng':95, 'math':70, 'scien':82}
print(type(scores))

def pickleWriter() :
    with open(file='dict.txt', mode='w', encoding='utf-8' ) as file :
        for (key,value) in scores.items():
            file.write('{} - {}\n'.format(key,value))
        print('저장완료!!')
pickleWriter()
```





### 객체 직렬화

#### 저장
```python
import pickle

def pickleWriter() :
    with open(file='dictPickle.txt', mode='wb' ) as file :
        pickle.dump(scores, file)
    print('객체 직렬화를 통한 파일저장!!')

pickleWriter()
```
#### 로드
```python
def pickleReader() :
    with open(file='dictPickle.txt', mode='rb' ) as file :
        dictScores = pickle.load(file)
        print('파일 로딩 - ' , dictScores, type(dictScores))
    print('객체 직렬화를 통한 파일저장!!')

pickleReader()
```




- 단어가 줄 단위로 저장된 cnt_words.txt 파일에서 10자이하인 단어의 갯수를 카운트하는 함수를 구현하고 호출한다면?

```python
# 나의 풀이
def fileReader():
    with open(file='./word/cnt_words.txt', mode='r', encoding='utf-8') as file:
        for line in file :
            num = 0
            if len(line) <= 10:
                num += 1
            else:
                pass
        print(num)

fileReader()
```
#### 풀이
```python
def wordCntFunc() :
    wordList = []
    with open(file='./word/cnt_words.txt', mode='r', encoding='utf-8') as file:
        for word in file.readlines():
            word = word.strip('\n')
            # print('word - ', word)
            if len(word) <= 10:
                wordList.append(word)
    print('10자 이하의 단어의 갯수는 {}개 입니다.'.format(len(wordList)))

wordCntFunc()
```



- special_words.txt 파일에서 문자가 'c'가 포함된 단어를 출력하는 함수를 만들어서 호출한다면?
- 단, 단어를 출력할 때는 등장한 순서대로 출력하며 ,.은 출력하지 않는다.
```python
# 나의 풀이
def specialWordFunc():
    # wordList = []
    with open(file='./word/special_words.txt', mode='r', encoding='utf-8') as file:
        for word in file.read().split():
            # wordList.append(word)
            if 'c' in word:
                print(word)
        # print(wordList)

specialWordFunc()
```
#### 풀이
```python
# 나의 풀이
def specialWordFunc():
    with open(file='./word/special_words.txt', mode='r', encoding='utf-8') as file:
        words = file.read().split()
        for word in words:
            if 'c' in word:
                print(word.strip(',.'))

specialWordFunc()
```



### zipcode.txt

- input() 이용해서 동 이름을 입력받아 해당하는 주소를 출력하는 함수를 정의하고 호출한다면?
- 입력예시) 개포
- hint) startwith(), endwith() 시작, 끝 문자 확인 하는 함수
```python
# 나의 풀이
# def searchAddrFunc():
#     lines = []
#     #dong = input('찾는 동을 입력하세요: ')
#     with open(file='./word/zipcode.txt', mode='r', encoding='utf-8') as file:
#         lines = file.readlines()
#         for line in lines.():
#         lines.append(line)
#             # if dong =='개포':
#             #     print(address)
#     #print('debug - ', dong)
#     print(addressList)
#
# searchAddrFunc()
```
#### 풀이
```python
def searchAddrFunc():
    dong = input('찾는 동을 입력하세요: ')
    # print('debug - ', dong)
    with open(file='./word/zipcode.txt', mode='r', encoding='utf-8') as file:
        line = file.readline()
        # print('debug - ', line, type(line))
        while line :
            address = line.split('\t')
            # print('debug - ', address, type(address))
            if address[3].startswith(dong) and address[3].endswith('동'):
                print('['+address[0]+']', address[1],address[2],address[3],address[4],address[5])
            line = file.readline()
        # print(line)

searchAddrFunc()
```




### csv, excel 파일의 파일 입출력

- pandas lib 사용

- pip install pandas

- conda install pandas

- DataFrame
  
  
  
- service_bmi.csv
```python
import pandas as pd

bmiDataset = pd.read_csv('./word/service_bmi.csv', encoding='utf-8')
print(bmiDataset.info())
print(bmiDataset.head())     # 앞 5개
print(bmiDataset.tail())     # 뒤 5개
print(bmiDataset.height, type(bmiDataset.height))				# 피쳐에 대한 접근 방법 - Series라는 데이터 타입으로 리턴됨
print(bmiDataset['weight'])
print(bmiDataset['label'])

# 키 / 몸무게 평균
print('키 avg {}, 몸무게 avg {}'.format(sum(bmiDataset.height)/len(bmiDataset.height),
                                    sum(bmiDataset['weight'])/len(bmiDataset['weight']) ))

# 키 최대 / 몸무게 최대
print('max height - ', max(bmiDataset.height))
print('max weight - ', max(bmiDataset.weight))

# label의 빈도수 구한다면?
labelCnt = {}
for label in bmiDataset.label:
    # print(label)
    labelCnt[label] = labelCnt.get(label, 0) + 1
print(labelCnt)
```
- spam_data.csv
```python
spamDataset = pd.read_csv('./word/spam_data.csv', header=None, encoding='ms949')
print(spamDataset)
print(spamDataset.info())
print(spamDataset.head())
target = spamDataset[0]
print('target - ', target, type(target))
text = spamDataset[1]
print('text - ', text, type(text))

# spam = 1, ham = 0 새로운 타겟을 만들고 싶다면?
target = [ 1 if t == 'spam' else 0 for t in target]
print(target)
```





### 코드클린 - 문자열에 대한 정규표현식을 이용해서 문자를 제거하는 작업

### 정규표현식( reguler expression)
```python
import re
```
```python
# 메타문자
'''
ex) . ^ $ * + ? {} [] \ | ()
. -> 무엇이든 한 글자를 의미
^ -> 시작문자 지정

* -> 0 or more
+ -> 1 or more
? -> 0 or 1

ex) 
[abc] -> a or b or c 중 한 문자와 매치
[^0-5] -> 0-5 중 시작하면 안됨             not
^[0-5] -> 0-5 중으로 반드시 시작해야함   	  must

문자클래스
\d -> 숫자의 자릿수
\D -> 숫자가 아닌 문자매칭의 자릿수
\w -> 문자+숫자
\W -> 문자+숫자가 아닌 문자와 매치
\s -> 공백

ex)
010-0000-0000
^\d{3}-\d{4}-\d{4}

많이 쓰이는 함수
- sub()
- match()
- search()
- findall()
- finditer()
'''
```
```python
import re
p = re.compile('[a-z]+')
match = p.match('Python')
print(match)
```
### 텍스트 전처리 - (특수 문자, 숫자, 공백, 영문제거) => 한글 단어만 추출
```python
def cleanText(str) :
    # re.sub(pattern= , repl= , str)
    str = re.sub('[,.?!;:]' , ' ' , str)
    print(str)
    str = re.sub('[0-9a-zA-Z]' , ' ' , str)
    print(str)
    str = ' '.join(str.split())
    print(str)

cleanText('비아그라 500GRAM 정력 최고!')
```
### [실습]
```python
text = spamDataset[1]
print(text)
def cleanText(str) :
    str = re.sub('[,.?!;:]|[0-9a-zA-Z]', ' ', str)
    str = ' '.join(str.split())
    return str

# cleanText(text)

cleanData = [ cleanText(t) for t in text]
print(cleanData)
```




### xls, xlsx 파일의 파일 입출력

```python
kospiDataset = pd.ExcelFile('./word/sam_kospi.xlsx')
kospi = kospiDataset.parse('sam_kospi')
print(kospi.info())

from statistics import *
print('avg - ', mean(kospi.High))
```




### json(java script object notation) 파일 입출력

- json file : 네트워크 상에서 표준으로 사용되는 파일형식
- 구성 : {key:value, key:value}
- encoding : python(dict, list) -> json 문자열(json file) : dumps()
- decoding : json 문자열        -> python(dict, list)     : loads()
- json - 파이썬의 딕션너리와 같음
```python
import json
```
### encoding
- python ->json
```python
import json
user = {'id' : '007', 'name' : 'Bond'}
print(type(user))

jsonStr = json.dumps(user) # object -> json str
print( jsonStr , type(jsonStr))
```
#### decoding
- json ->python
```python
pyObj = json.loads(jsonStr)
print( pyObj, type(pyObj))
print( pyObj['name'])
print( pyObj.get('name'))


# usagov_bitly.txt
with open(file='./word/usagov_bitly.txt', mode='r', encoding='utf-8') as file:
    lines = file.readlines()
    # print(type(lines), len(lines))
    # print(lines[:5])
    # lines[string]
    rows = [json.loads(line) for line in lines]
    # print( type(rows))
    # print( type(rows[0]))
    # for row in rows :
    #     # print(row)
    #     for key, value in row.items() :
    #         print('key - {}, value - {}'.format(key, value))
    # rows -> pd.DataFrame(행렬)
    rowsDF = pd.DataFrame(rows)

print(rowsDF.head)
```