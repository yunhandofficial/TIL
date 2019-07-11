# startcamp-day4

Flask 다운받기

http://127.0.0.1:5000/ 주소

입력하면 원하는 페이지 만들어서 들어갈수 있음.

1. 페이지 만드는법 1단계(주소에 들어가면 글씨가뜸)

```python
@app.route("/")  
def hello():
   return "Hello World!"

@app.route("/hi") #주소 뒤에 /hi를 붙여주면 이 부분이 출력된다.
def hi():
   return "안녕하세요"
```

> 주소뒤에 /hi를 붙여주면 " 안녕하세요"  가 출력된다

2. 페이지 만드는법 2단계(글씨 꾸미기 가능)

```python
@app.route("/html_tags")
def html_tags():
   return """
   <h1>안녕하세요</h1>
   <h2>안녕하세요.</h2>
   """
```

> h1 태그와 h2 태그는 글씨크기와 두께 차이! w3school 에서 더많은 태그 확인가능

3. 1,2단계의 간단한 응용

```python
@app.route("/dday")
def dday():
   today = datetime.datetime.now()
   endday = datetime.datetime(2019,11,29)
   d = endday-today
   return f"1학기 종료까지 {d.days}일 남음" #f는 string으로 변환함

@app.route("/html_file")
def html_file():
   return render_template('index.html')

@app.route("/greeting/<string:name>") # greeting 안에 name이라는 변수 이름을 string으로 저장해줌
def greeting(name):
   return f"안녕하세요 {name}님"
```

> 각각 간단한 응용들이다

4. 이미지가 나오게하기

```python
import random
@app.route("/lunch")
def lunch():
    menu ={
        "짜장면":"https://dispatch.cdnser.be/wp-content/uploads/2017/04/20170427213340_1q1q.jpg",
        "사천탕수육":"https://www.simbata.co.kr/img_src/s600/a220/a2200048.jpg",
        "처갓집 슈프림양념":"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT1JR0W0xX-RvgmzLRh0OtoUbn8xmRIUzENNJLv59bMqN_Vwi_g"
    }

    menu_list = list(menu.keys()) #["짜장면"]
    pick = random.choice(menu_list)
    img = menu[pick] 

    return render_template("lunch.html", pick=pick, img=img)
```

>

 