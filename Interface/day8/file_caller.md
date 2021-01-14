```
from ai.file.file_proc import *
# try:
#     fileStream('hello.txt', 'asd')
# except Exception as e :
#     print(e)
#
# print('end')

# single line text inout
fileStream('./ai/file/hello.txt', 'r')

# multi line text out
withMultiWriter('multiline.txt')
print('end')


lines = ['안녕하세요.',
         '혹시 졸리우시면 ㅇㅇㅅㅋㄹ 콜?',
         '그럼 졸지말고 집중',
         '강사의 주옥같은 말을 한 귀로 흘리면 안돼요.']
withListFileWriter('listline.txt', lines)

# multi line text read
withListFileRead('listline.txt', 'r')
```

