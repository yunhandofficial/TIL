# startcamp-day2

### 코딩을위한 준비
 python, visual studio code, git bash 깔기

 >gitbash 는 cmd 같은거
 >visual studio code는 코딩 가틍거

### git bash 활용하기

1. ls 
> 현재 있는것들 나열
2. cd
> chand directory
> cd ~, cd ..(상위) , cd
3. rm
> 파일지우기
4. mkdir
> 새로운 디렉토리 생성

### visual studio code 활용하기

1. 자료 요청하기
```python
import requests
from bs4 import BeautifulSoup

response = requests.get("https://naver.com").text
soup = BeautifulSoup(response, "html.parser")
naver = soup.select_one("#PM_ID_ct > div.header > div.section_navbar > div.area_hotkeyword.PM_CL_realtimeKeyword_base > div.ah_list.PM_CL_realtimeKeyword_list_base > ul:nth-child(5) > li:nth-child(1) > a.ah_a > span.ah_k")
print(naver.text)
```

> 실시간 검색어 가져오기
>
> 1. url 가져오기
> 2. select 가 리스트 select_one이 하나만 
> 3.  원하는 자료에서 오른쪽마우스 검색을 이용하여( 혹은 f11인가를 눌러서) 코드를 확인, 원하는 줄에서 오른쪽 마우스  copy copy select뭐시기
> 4. beautifulsoup 은 파이썬이 이해하도록 자료를 이쁘게



2. 파일 100개 만들기

   ```python
   from faker import Faker
   import os
   
   f= Faker('ko_KR')
   
   for i in range(100):
       filename = f"{i}_{f.name()}.txt"
       cmd = f"touch {filename}"
       os.system(cmd)
   ```

   > 1. faker 는 랜덤으로 이름 생성
   > 2. 100개 이름 만들고 touch는 파일 생성하는거

3. 파일 이름 바꾸기

   ```python
   import os
   
   os.chdir(r"C:\Users\student\startcamp\students")
   for filename in os.listdir("."):
       os.rename(filename, filename.replace("SAMSUNG_", "SSAFY_"))
   ```

   > 1. 그냥 이름으로만 된 파일에 "SAMSUNG_" + filename 을해서 바꾸고
   > 2. 위의 코딩은 SAMSUNG_땡떙땡 이라는 파일들을 다 SSAFY_땡땡떙으로 바꾸는것

4. 브라우저 열기

   ```python
   import webbrowser
   
   url = "https://search.naver.com/search.naver?sm=top_hty&fbm=1&ie=utf8&query="
   my_keywords = ["iu", "bts", "winner", "itzy"]
   for my_keyword in my_keywords:
       webbrowser.open(url+ my_keyword)
   ```

   > 웹브라우저 여는 단어 webbrowser.open(주소) 기억하기

5. 코스피 지수 크롤링

   ```python
   import requests
   from bs4 import BeautifulSoup
   
   response = requests.get("https://finance.naver.com/sise/").text
   soup = BeautifulSoup(response, "html.parser")
   kospi = soup.select_one("#KOSPI_now")
   print(kospi.text)
   ```

   > 실시간 검색어 방법과 매우 유사하니 참고

6. 여러나라 환율 가져오기

   ```python
   import requests
   from bs4 import BeautifulSoup
   
   url ="https://finance.naver.com/marketindex/exchangeList.nhn"
   res = requests.get(url).text
   soup = BeautifulSoup(res,"html.parser")
   
   tbody = soup.select_one('tbody')
   tr = tbody.select('tbody > tr')
   for r in tr:
       print(r.select_one('.tit').text.strip())
       print(r.select_one('.sale').text)
   ```

   > 어려우니 대충 한번 봐보기 뭔소린지만 알아먹으면 됨!



### GitHub 활용하기

1. 파일 업로드 하는법

   > git into
   >
   > git add .
   >
   > git commit -m "메모"
   >
   > 디렉토리 추가 (제일긴거 가져와서 그대로 붙여넣기)
   >
   > git push origin master

2. 협업하기

   > clone 도 있었는데 기억안남
   >
   > pull도 있었음~~~~