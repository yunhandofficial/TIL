# startcamp-day5

1. 일단 플라스크(영어로는 Flaskㅎ)를 가져온다

2. Telegram 들어가서 가입하고

3. 봇을 만들어 본다

4. 파더봇인가 뭐신가 영어로 치면 나옴

5. 거기에 기능을 추가하기 위해서 API에 들어가서 주소를 알았어야 했던듯..

6. 그리고 나의 token을 알아낸다..

   ```python
   @app.route(f"/{token}", methods=['POST'])
   def telegram():
       print(request.get_json())
       data = request.get_json()
       user_id = data.get('message').get('from').get('id')
       user_msg = data.get('message').get('text')
   #원하는 정보를 저렇게 타고 들어가서 얻어와양함
       if data.get('message').get('photo') is None:
               if user_msg =="점심메뉴":
                   menu_list = ["삼계탕", "철판낙지볶음밥", "물냉면"]
                   result = random.choice(menu_list)
               elif user_msg == "로또":
                   numbers = sorted(random.sample(range(1,46), 6))
                   result = numbers
               elif user_msg == "날씨":
                   response = requests.get("https://search.naver.com/search.naver?where=nexearch&query=%EC%98%A4%EB%8A%98%EC%9D%98+%EB%82%A0%EC%94%A8+%EA%B4%91%EC%A3%BC").text
                   soup = BeautifulSoup(response, "html.parser")
                   weather = soup.select_one("#main_pack > div.sc.cs_weather._weather > div:nth-child(2) > div.weather_box > div.weather_area._mainArea > div.today_area._mainTabContent > div.main_info > div > ul")
                   result = weather.text
               elif user_msg[0:2] =="번역": 
                   raw_text = user_msg[3:]
                   papago_url = "https://openapi.naver.com/v1/papago/n2mt"
                   data = {
                       "source":"ko",
                       "target":"en",
                       "text":raw_text
                   }
                   header = {
                       "X-Naver-Client-Id" : naver_id,
                       "X-Naver-Client-Secret" : naver_secret
                   }
                   res = requests.post(papago_url, data=data, headers=header)
                   translate_res = res.json()
                   translate_result = translate_res.get('message').get("result").get('translatedText')
                   result = translate_result
   
               else:
                   result =user_msg
       else:
           #사용자가 보낸 사진을 찾는 과정
           result="asdf"
           file_id = data.get('message').get('photo')[-1].get('file_id')
           file_url = f"{api_url}/bot{token}/getFile?file_id={file_id}"
           file_res = requests.get(file_url)
           file_path = file_res.json().get('result').get('file_path')
           file = f"{api_url}/file/bot{token}/{file_path}"
           print(file)
   
           #사용자가 보낸 사진을 클로버로 전송
           res = requests.get(file, stream=True)
           clova_url = "https://openapi.naver.com/v1/vision/celebrity"
           header = {
                       "X-Naver-Client-Id" : naver_id,
                       "X-Naver-Client-Secret" : naver_secret
                   }
   
           clova_res = requests.post(clova_url, headers=header, files={'image':res.raw.read()})
           if clova_res.json().get('info').get('faceCount'):
               #누구랑 닮았는지 출력
               celebrity = clova_res.json().get('faces')[0].get('celebrity')
               name = celebrity.get('value')
               confidence = celebrity.get('confidence')
               result = f"{name}일 확률이 {confidence} 입니다."
           else:
               #사람이 없음
               result = "사람이 없습니다."
           print(clova_res.text)
   
   
       res_url = f"{api_url}/bot{token}/sendMessage?chat_id={user_id}&text={result}"
       requests.get(res_url)
   
       return '', 200
   ```

   ### 개인정보는 .env 파일에 넣고

   ### gitignore에 들어가서 복사 붙여넣기

7. 번역과 클로바는 넘 어려워서 잘 생각이... 거의 받아쓰기 수준~~!!~!~!~!

8. json 으로 해야 했는데 그부분도 잘..ㅎㅎㅎ