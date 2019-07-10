# startcamp-day3

### 텍스트파일 만들기

```python
# f = open("student.txt", 'w')
# f.write("안녕하슈")
# f.close()

with open("ssafy.txt", 'a') as f:
    f.write("화싸")
```

> a 랑 w 랑 뭐 여러가지 있었음






### 크롤링하기

#### 비트코인 시세 크롤링

```python
import requests
from bs4 import BeautifulSoup

url = "http://www.bithumb.com"
reponse = requests.get(url).text
bitcoin_rate = BeautifulSoup(reponse, "html.parser")

tbody = bitcoin_rate.select_one('tbody')
tr = tbody.select('tbody > tr')
# td = tr.select('tr > td')
for r in tr:
    print(r.select_one("a").text)
    print(r.select_one(".sort_real").text)
```

> 넘 어렵... class 로 찾으려면 "sort_real" 말고 ".sort_real" 



### CSV

#### Table 만들기

​```python
import csv

lunch = {
    "bbq" : "1",
    "천안문" : "2",
    "오늘부터 애간장"  : "3"
}

with open("lunch.csv", 'w', encoding="utf-8", newline="") as f:
    csv_writer = csv.writer(f)
    
    for item in lunch.items():
        csv_writer.writerow(item)
```

> 그냥 표로 데이터 정리 할때 필요 한둣...!
>
> 중간에 뭐 쉼표인가 뭐신가 해주는 프로그램 까라뜜



### HTML&CSS

```python
<h1>hello</h1>>
<h1>HyperText Markup Language</h1>
```

> 여는태그 닫는태그 필요
>
> CSS는 디자인 관련~~
>
> id가 더 잘먹음 그다음으로 class 스타일은 젤 마지막

##### 템플릿 다운받아서 꾸미는것도 함ㅎㅎㅎ

