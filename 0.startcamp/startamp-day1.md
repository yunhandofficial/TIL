# startamp-day1

## 파이썬의 기초1

1. 숫자 글자 참거짓

   > 글자는 "" 참거짓은 대문자 유의 True False

2. 저장하는법 :  **변수**, 리스트 딕셔너리

```python
greeting = "할룽"

for i in range(15):
  print(greeting)
```
> '='은 지정의 의미(박스이름지정 dust=)

3. 저장하는법 : 변수, **리스트** 딕셔너리

```python
import random

# 원하는 메뉴를 []안에 넣어주세요
menu = ["마라샹궈", "탕수육", "황금코다리"]

choice = random.choice(menu)
print(f"오늘 점심은 {choice} 어떤가요?")
```

>dust[40,50,80]여기에서 dust[0]은 40
>
>내장함수**print** 외장함수**random**


> **import random** 꼭 기억하기

4. 저장하는법 : 변수, 리스트, **딕셔너리**

   ```python
   import random
   
   # 원하는 식당과 전화번호를 {}안에 넣어주세요
   phonebook = {
     "우리집" : "062-574-5555",
     "마피아떡볶이 용봉점" :"0507-1489-2225",
     "꼬치양 탕슈군" : "062-574-9288",
     "민수정장작구이" : "062-575-5392",
   }
   choice = random.choice(list(phonebook.keys()))
   print(f"{choice} : {phonebook[choice]}")
   ```

   

5. if elif else

```python
if (dust>150):
      print("매우나쁨")
elif (dust>80):
      print("나쁨")
elif (dust>30):
      print("보통")
else:
      print("좋음")
```



6. 0번째가 항상 있다.

```python
import random
numbers = list(range(1,46)) 
pick = random.sample(numbers, 6)
print(sorted(pick))
```

> range(46)은 0부터 45까지 46개의 수를 의미함
>
> range(1,46)는 1부터 45까지 45개의 수를 의미함

7. random.sample 사용법

```python
import random
lotto= random.sample(range(1,46),6)
print(lotto)
```

> 리스트를 만들어서 사용하는 방법도 있음.
>
> ```python
> import random
> numbers = list(range(1,46))
> pick = random.sample(numbers, 6)
> print(sorted(pick))
> ```