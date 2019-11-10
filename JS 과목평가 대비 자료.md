# JS 과목평가 대비 자료

## 1. 기본 문법

![1573299356553](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573299356553.png)

(1) for 문 돌릴떄

`var`

![1573299697857](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573299697857.png)

>```bash
>0
>1
>```
>
>var는 for 문 밖에서 존재

`let`, `const`

![1573299786428](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573299786428.png)

>```bash
>0
>C:\Users\pors3\SSAFY\javascript\test.js:4
>console.log(i)
>            ^
>
>ReferenceError: i is not defined
>```
>
>블록안에서만 존재하고 밖에서는 오류남

(2) 함수에서

`var`

![1573300389681](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573300389681.png)

>```bash
>0
>1
>C:\Users\pors3\SSAFY\javascript\test.js:8
>console.log(k)
>            ^
>
>ReferenceError: k is not defined
>```
>
>함수안에서는 블록 안과 밖에서 둘다 존재하지만,
>
>함수 밖에서는 존재하지 않음

![1573300558208](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573300558208.png)

`var`

![1573300588097](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573300588097.png)

> 오류 안남

`const`, `let`

![1573300646981](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573300646981.png)

> 오류남

* `var`,`let`,`const`  를 사용하지 않고 선언되었다면?

![1573300923950](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573300923950.png)

> ```bash
> 0
> 1
> 1
> C:\Users\pors3\SSAFY\javascript\test.js:9
> console.log(window.p)
>             ^
> 
> ReferenceError: window is not defined
> ```
>
> 전역 변수로 취급되어서 어디서든 console 찍으면 나옴 (windows는 제외)

### 2. 자료형

`typeof` 를 문자열, 숫자 등 모두 찍어보기

>console.log(typeof '123')      // string
>console.log(typeof 123)        // number
>console.log(typeof true)       // boolean
>console.log(typeof null)       // object
>console.log(typeof undefined)  // undefined
>console.log(typeof NaN)        // number (숫자로 표기되지만 숫자는 아니다. 문자열과 숫자를 더할때 나오는 에러)
>console.log(typeof {})          // object
>console.log(typeof function(){})   // function
>console.log(typeof [])          // object
>
>요게 type의 전부 ! => **undefined, object, boolean, number,string, function,symbol**



### 3. 조건/반복

`while`

```js
var i = 0;
while ( i < 10 ) {
  // do something
  i++;
}
```

`for`

```js
for ( var i = 0; i < 10; i++ ) {
  // do something
}
```

`if`, `else if`, `else`

```js
if ( condition1 ) {
  statement1
} else if ( condition2 ) {
  statement2
} else {
  statement3
}
```

`==`: 느슨한 비교

> 0 == "0" //true
>
> 0 == [] //true
>
> "0" == []  //false

 `===`: 엄격한 비교



### 4. 배열

![1573303148200](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573303148200.png)

![1573303164346](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573303164346.png)

![1573303190484](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573303190484.png)

> **.reverse()** 는 numbers를 바꾼다

![1573303415793](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573303415793.png)

> **.push(원소) **: 뒤로 넣어주기, 넣어준 후의 길이 반환
>
> **.pop()** :  가장 뒤에있는 원소 반환
>
> **.unshift('a')** : 'a'를 맨 앞으로 넣어주기 , 넣어준 후의 길이 반환
>
> **.shift()** :  맨 앞의 원소 반환

![1573303752390](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573303752390.png)

>**.includes(원소)** : 있는지 없는지 확인해서 true 와 false 반환
>
>**.push(원소), .unshift(원소)** : 둘다 넣은후의 길이 반환
>
>**indexof(원소)** : 처음찾은 요소의 index, 없으면 -1
>
>**.join()** : 위에 참고

### 5. Object

object에 접근할 때 어떻게 접근하는지 알아야 한다.

`.`을 사용한 접근, `[키값]`을 이용한 접근

key와 value가 같으면 생략 가능하다.

```js
const bookShop = {
comics,
magazines,
}
```

object 안에 함수를 넣을 수 있다는 것도 알아야 한다.

```js
const me = {
name: 'Kim',
greeting: function(message) {
return `${this.name} : ${message}`
}
}
```

> key값으로 함수를 실행

### 6. JSON

기본 형태는 String으로 되어있다.



### 7. 함수

```js
//방법1
function add(a, b){
    return a+b
}
//방법2
const add = function (a,b){
    return a+b
}
//방법3 화살표 함수
const plus = (a, b) => {
    return a+b
}

(function(){console.log("하이")})() // "하이"

const p = function(){return 'hello'}() // p 호출시 "hello" 출력

const asdf = (() => {return '123'})() // asdf 호출시 "123" 출력
```

맨 뒤에 소괄호가 붙어있으면 함수가 바로 실행된다.

`const p = function(){return 'hello'}()`의 경우를 보면 `function(){return 'hello'}`를 뒤에 붙은 `()`가 실행을 시키고 `const p`에 저장한다.

`p`를 호출하면 hello가 호출된다.



### 8. Array Helper Methods

각각 한번씩 다 써보기. 직접 함수에 넣어 실행시키면 좋다.

* forEach

```js
var array1 = ['a', 'b', 'c'];

array1.forEach(function(element) {
  console.log(element);
});
// expected output: "a"
// expected output: "b"
// expected output: "c"
```

* map

```js
var array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1);
// expected output: Array [2, 8, 18, 32]
```

* filter

```js
var words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);

console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
```

> array를 리턴

* find

```js
var array1 = [5, 12, 8, 130, 44];

var found = array1.find(function(element) {
  return element > 10;
});

console.log(found);
// expected output: 12
```

> 맨처음으로 발견한 하나만 리턴

* every

```js
function isBelowThreshold(currentValue) {
  return currentValue < 40;
}

var array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));
// expected output: true
```

> 모든 원소들이 만족하면 true
>
> 하나라도 만족안하는게 있으면 false

* some

```js
var array = [1, 2, 3, 4, 5];

var even = function(element) {
  // checks whether an element is even
  return element % 2 === 0;
};

console.log(array.some(even));
// expected output: true
```

> 하나라도 만족하는게 있으면 true
>
> 아니면 false



## 2. DOM

![1573375527976](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573375527976.png)

### 2. DOM selector

* `querySeletor()` : 오직 첫번째 요소만 선택해줌
* `querySeletorAll()` : array로 전체 요소 선택 

### 3. Event Listener

![1573376336655](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573376336655.png)

> arrow function을 사용하지 않음!!(**this**가 다르기 때문이다.)
>
> *style바꾸려면*  *selector로선택한것.style.color="red"* 라고 하면 글씨가 빨개짐

* `.createElement()`

![1573377970378](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573377970378.png)

* `.appendChild()`

![1573378065179](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573378065179.png)

> body의 자식요소로 jbBtn을 넣는다

## 3. Axios

### 1. cdn 넣기

### 2. 기본 활용법

axios는 promise라는 덩어리로 요청을 보내주고, then과 catch를 사용해 그 덩어리를 풀어준다.

![1573378156990](C:\Users\pors3\AppData\Roaming\Typora\typora-user-images\1573378156990.png)

프로젝트에서  axios이용해서 데이터 가져오기

```js
const MOVIE_URL = 'https://gist.githubusercontent.com/eunji-j/3c2b5e9142de6c4cfd7cfe9e1e172141/raw/d7f6ae88b04a67c8f3069c3d73de253f659321df'
    axios.get(MOVIE_URL)
      .then(response=>{
        console.log(response)
        this.movies = response.data
      })
      .catch(error=>{
        console.log(error)
      })
```





### 3. 개념 확인하기

promise 함수는 resolve와 reject라는 객체를 들고있고, then은 resolve의 결과를 가져오고, catch는 reject의 결과를 가져온다.



#### **비동기**

코드가 순차적으로 돌아가는데 외부 서버에 요청을 보내야하는 경우가 있다.

만약 javascript에서 axios를 만나면 django에 요청을 보내게 된다.

javascript에서는 계속 코드를 실행하게 되고, 만약 django에서 요청이 온다면 다시 그 요청을 받아 처리하게 된다.

스레드를 효율적으로 사용하기 위해 비동기 방식을 사용한다.

> javascript 는 **비동기**, **non-blocking**, 
>
> 브라우저는 싱글쓰레드, 이벤트기반, 
>
> call stack(순차적으로, task가 종료하기 전까지는 다른 task를 수행할 수 없다.) 
>
> callback queue(비동기처리함수의 뭐시기들이 기록, eventloop에 의해)
>
> eventloop 왠지 필요 없을듯
>
> 파이썬은 동기, blocking

## 4. Ajax

ajax를 사용하기 위해 axios를 사용한다.



## 5. Javascript에서 구현한 좋아요 코드 다시 보기!!!

```javascript
{% extends 'base.html' %}
{% block body %}
  <h1>인덱스</h1>
  {% for post in posts %}
    <p>{{post.user.username}}</p>
    <p>{{post.title}}</p>
    <p><span id="post{{post.id}}">{{post.like_users.count}}</span>명이 좋아요를 눌렀습니다.</p>
    {% if user in post.like_users.all %}
      <i class="fas fa-heart" data-id="{{post.id}}"></i>
    {% else %}
      <i class="far fa-heart" data-id="{{post.id}}"></i>
    {% endif %}
    <hr>
  {% endfor %}

  <script>
    const likeBtns = document.querySelectorAll('.fa-heart')
    // console.log(likeBtns)
    likeBtns.forEach((btn)=>{
      // console.log(btn)
      btn.addEventListener('click', (e)=>{
        // console.log(e.target.classList)
        const postId = e.target.dataset.id
        // e.target.classList.remove('far')
        // e.target.classList.add('fas')
        console.log(postId)
        // 장고에게 좋아요 요청을 보낸다.
        axios.defaults.headers.common['X-Requested-With'] = 'XMLHttpRequest'
        axios.defaults.xsrfCookieName = 'csrftoken'
        axios.defaults.xsrfHeaderName = 'X-CSRFToken'
        
        axios.post(`/posts/${postId}/like/`)
          .then((response)=>{
            console.log(response.data)
            document.querySelector(`#post${postId}`).innerText = response.data.likes_count
            if(response.data.is_like){
              e.target.classList.remove('far')
              e.target.classList.add('fas')
            }else {
              e.target.classList.remove('fas')
              e.target.classList.add('far')
            }
          })
          .catch((error)=>{console.log(error)})
        
        // get요청으로 좋아요 버튼 구성하기
        // axios.get(`/posts/${postId}/like/`)
        // .then((response)=>{
        //   console.log(response.data)
        //   document.querySelector(`#post${postId}`).innerText = response.data.likes_count
        //   if(response.data.is_like){
        //     e.target.classList.remove('far')
        //     e.target.classList.add('fas')
        //   }else {
        //     e.target.classList.remove('fas')
        //     e.target.classList.add('far')
        //   }
        // })
        // .catch((error)=>{console.log(error)})
      })
    })
  </script>
{% endblock %}
```

```python
def like(request, id):
    if request.is_ajax():
        post = get_object_or_404(Post, id=id)
        user = request.user

        # if user in post.like_users.all(): 
        if post.like_users.filter(id=user.id):
            post.like_users.remove(user)
            is_like = False
        else:
            post.like_users.add(user)
            is_like = True

        context = {
            'is_like': is_like,
            'likes_count': post.like_users.all().count() 
        }
        return JsonResponse(context)
        # return redirect('posts:index')
    else:
        return JsonResponse({'message': '잘못된 요청입니다.'})
```

<은지꺼 퍼온거>

## 4) 예제_facebook 좋아요

- Python 코드의 좋아요기능을 비동기처리방식으로 바꿔보기

> views.py

```
from django.http import JsonResponse

def like(request, id):
    if request.is_ajax():
        post = get_object_or_404(Post, id=id)
        user = request.user
        # if user in post.like_users.all():
        if post.like_users.filter(id=user.id):
            post.like_users.remove(user)
            is_like = False
        else:
            post.like_users.add(user)
            is_like = True

        # context에 담아서 넘겨준다.
        context = {
            'is_like': is_like, # 좋아요여부
            'likes_cnt': post.like_users.all().count() # 좋아요수
            }
        # Json 구조로 반환
        return JsonResponse(context)
        # return redirect('posts:index')
    else:
        return JsonResponse({'message': '잘못된 요청입니다.'})
```

> index.html

```
{% block body %}
  <h1>인덱스</h1>
  {% for post in posts %}
    <p>{{post.user.username}}</p>
    <p>{{post.title}}</p>
    <!-- 어떤 게시물인지 알기위해 id를 지정 -->
    <p><span id="count{{post.id}}">{{post.like_users.count}}</span>명이 좋아요를 눌렀습니다.</p>
    
    {% if user in post.like_users.all %}
      <!-- 어떤 data인지 알기위해 data-id를 지정 => e.target안에 dataset이 생긴다. -->
      <i class="far fa-thumbs-up" data-id="{{post.id}}"></i>
    {% else %}
      <i class="far fa-thumbs-down" data-id="{{post.id}}"></i>
    {% endif %}
    <hr>
    {% endfor %}
    <script>
      const likeBtns = document.querySelectorAll('i')
      likeBtns.forEach(btn=>{
        btn.addEventListener('click', (e)=>{
          // console.log(e.target.classList)
          const postId = e.target.dataset.id
          console.log(postId)

          // 장고에게 좋아요 요청을 보낸다.(post)
          axios.defaults.headers.common['X-Requested-With'] = 'XMLHttpRequest' // XHR요청
          axios.defaults.xsrfCookieName = 'csrftoken' // 쿠키안의 csrftoken
          axios.defaults.xsrfHeaderName = 'X-CSRFToken' // 헤더 설정
          axios
            .post(`/posts/${postId}/like/`)
            .then(response=>{
              console.log(response.data)

              // 해당게시물의 좋아요수를 바꾼다.
              const likes_cnt = document.querySelector(`#count${postId}`)
              likes_cnt.innerText = response.data.likes_cnt
              
              // 해당게시물의 아이콘을 바꾼다.
              if (response.data.is_like) {
                e.target.classList.remove('fa-thumbs-down')
                e.target.classList.add('fa-thumbs-up')
              }else {
                e.target.classList.remove('fa-thumbs-up')
                e.target.classList.add('fa-thumbs-down')
              }
            })
            .catch(error=>{
              console.log(error)
            })
        })
      })
    </script>
{% endblock %}
```