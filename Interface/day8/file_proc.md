```
'''
텍스트파일 입출력
open(file = '파일경로/파일명' , mode = 'r | w | a | wb')

# 쓰기모드
file = open(file= 'hello.txt' , mode= 'w')
file.write('Hi, YS')
file.close()

# 읽기모드
file = open(file= 'hello.txt' , mode= 'r')
print(file.read())
file.close()

# 자동 클로즈
with open() as file:
with open(file='hello.txt', mode='r') as file :
    print(file.read())
'''

# def fileStream(fileName, mode):
#     if mode == 'w' :
#         pass
#     elif mode == 'r' :
#         with open(file=fileName, mode=mode) as file :
#             line = file.read()
#             print('result read - ', line)
#     elif mode == 'a' :
#         pass
#     else :
#         raise Exception('모드를 확인하세요')
#

def fileStream(fileName, mode):
   file = None
   try:
        if mode == 'w' :
            file = open(file=fileName, mode=mode)
            file.write('sample txt')
        elif mode == 'r' :
            file = open(file=fileName, mode=mode)
            line = file.read()
            print('result read - ', line)
        elif mode == 'a' :
            file = open(file=fileName, mode=mode)
            file.write('\nappend')
        else :
            raise Exception('모드를 확인하세요')
   except Exception as e :
        print('error - ', e)
   finally:
        if file != None:
            file.close()



# multiline test
def withMultiWriter(fileName) :
    with open(fileName, 'w', encoding='utf-8') as file :    # 인코딩 옵션도 추가 가능
        for idx in range(3) :
            print('idx - ', idx)
            text = input('문자열 입력하세요.')
            file.write('{} - {}\n'.format(idx, text))

# [실습] Writing
def withListFileWriter(fileName, dataSet):
   with open(fileName, 'w', encoding='utf-8') as file :
       for idx in range(len(dataSet)):
           print('idx - ', idx)
           file.write('{} - {}\n'.format(idx, dataSet[idx]))

# [실습2] Reading
def withListFileRead(fileName, mode) :
    with open(fileName, mode, encoding='utf-8') as file :
        # line = None
        # while line != '':
        #     line = file.readline()    # 한줄씩 텍스트로
        #     print(line.strip('\n'))

        # # print(file.readlines())       # 전체 문장을 리스트로
        # for line in file.readlines():
        #     print(line.strip('\n'))

        # print(file, type(file))
        for line in file :
            print(line.strip('\n'))
```