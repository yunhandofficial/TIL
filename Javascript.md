# Javascript

## 1. 변수 - var, let, const

Javascript에서는 파이썬과 달리 기본적으로 `변수를 선언`하여야 한다.

ES6이전에는 var 를 이용하였으나 우리는 `const` 를 중심으로 사용하고, `let` 이 필 요한 경우만 사용할 것이다.



### `var` - function scope, 재선언 가능

```javascript
function testA(){
    for (var a=0; a<5; a++){
        console.log(a)  // 01234
    }
    console.log(a)  // 5
}
testA()
```

```javascript
var a = 0
function testA(){
    for (var a=0; a<5; a++){
        console.log(a)  // 01234
    }
    console.log(a)  // 5
}
testA()
console.log(a)  // 0
```



### `let` - block scope, 재선언 불가능, 재할당 가능

```javascript
for (let a=0; a<5; a++){
    console.log(a)  // 01234
}
```

```javascript
for (let a=0; a<5; a++){
    console.log(a)  // 01234
}
console.log(a)  // error
```

```javascript
let a = 0
for (let a=0; a<5; a++){
    console.log(a)  // 01234
}
console.log(a)  // 0
```

```javascript
for (a=0; a<5; a++){
    console.log(a)  // 01234
}
console.log(a)  //5
```

변수 선언 키워드를 사용하지 않으면 전역변수로 모든 공간에서 사용할 수 있다.

for문에서는 항상 `let`을 사용하자.(for문 두번째 인자부터는 에러나옴) 그 외에서는 `const`사용하기

```javascript
let user2 = {
    name: 'change',
    phone: 'samsung',
}
user2 = {} // 재할당 >> 데이터나 자료형을 바꿈
console.log(user2)  // >> {}
```





### `const` - block scope, 재선언 불가능, 재할당 불가능

```javascript
const user = {
    name: 'change',
    phone: 'samsung',
}
// user = {} // 재할당 >> 데이터나 자료형을 바꿈 >> error
user.name = '오창희'  // 이건 재할당이 아니다.(데이터 값을 바꾼다.)
console.log(user)  // >> { name: '오창희', phone: 'samsung' }
```







## 2. 자료형

모든 구조 다 타입 찍어보기`typeof`(파이썬과 결과가 다른거 찾기)

- Boolean (true/false)

  논리적인 요소를 나타내고, `true` 와 `false` 의 두 가지 값을 가질 수 있다.

- null

  Null 타입은 딱 한 가지 값, `null` 을 가질 수 있다.

- undefined

  값을 할당하지 않은 변수는 `undefined` 값을 가진다.

- number ( Infinity , 양수, 음수 등)

  숫자의 자료형은 배정밀도 64비트 형식 IEEE 754 값 (-(2^53 -1) 와 2^53 -1 사이의 숫자값) 단 하나만 존재한다. **정수만을 표현하기 위한 특별한 자료형은 없다.**

  이 값에는  `+무한대`, `-무한대`, and `NaN` (숫자가 아님)이 있다.

- string

  텍스트 데이터를 나타내는데 사용한다.

```javascript
console.log(typeof '123')      // string
console.log(typeof 123)        // number
console.log(typeof true)       // boolean

console.log(typeof null)       // object
console.log(typeof undefined)  // undefined
console.log(null + 1)          // 1 : null을 숫자로 인식
console.log(undefined + 1)     // NaN
console.log(typeof NaN)        // number (숫자로 표기되지만 숫자는 아니다. 문자열과 숫자를 더할때 나오는 에러)

console.log(typeof {})             // object
console.log(typeof [])             // object
console.log(typeof function(){})   // function

console.log(null == undefined)    // true
console.log(null === undefined)   // false
```







## 3. 조건/반복

### if문

```javascript
const userName = prompt('who are you?')  // 팝업창

let message = ""

if (userName === "change") {
    message = "hi admin"
} else if (userName === "happy") {
    message = "happy coding"
} else {
    message = `hello ${userName}`
}
console.log(message)
```



### while문

```javascript
let i = 0

while (i < 5) {
    console.log(i)
    i++
}
```



### for문 

```javascript
let colors = ['red', 'green', 'blue']
```

```javascript
for (let color of colors) {
    console.log(color)
}
```

```javascript
for (let i = 0; i < colors.length; i++){
    console.log(colors[i])
}
```

```javascript
colors.forEach(function(color){
    console.log(color)
})
```



### == vs ===

`==(느슨한 비교)` : 값을 비교

`===(엄격한 비교)` : 타입까지비교





## 4. 배열 - Objects

```javascript
const myarray = [0, 1, 2, 3, 4, 5]
```

```javascript
console.log(myarray[3])   // 음수 인덱스 접근은 안된다. 3
console.log(myarray.length)  // 6
```

```javascript
// 원본 파괴
myarray.reverse()
console.log(myarray)   // [ 5, 4, 3, 2, 1, 0 ]

console.log(myarray.push(6))  // 7(길이) //  문자열도 들어갈 수 있다.
console.log(myarray)   // [5, 4, 3, 2, 1, 0, 6]

console.log(myarray.pop())  // 6
console.log(myarray)   // [ 5, 4, 3, 2, 1, 0 ]

console.log(myarray.unshift(-1))  // 7  : 맨 첫번째 요소를 삽입
console.log(myarray)   // [-1, 5, 4, 3, 2, 1, 0 ]
console.log(myarray.shift())     // -1  : 맨 첫번째 요소를 삭제
console.log(myarray)   // [ 5, 4, 3, 2, 1, 0 ]
```

```javascript
// 원본이 바뀌지 않는다.
console.log(myarray)  // [ 5, 4, 3, 2, 1, 0 ]
console.log(myarray.includes(100))  >> false
console.log(myarray.includes(1))    >> true

console.log(myarray.indexOf(3))  // 3이 위치한 인덱스값 >> 2
console.log(myarray.indexOf(7))  // 데이터를 찾을 수 없다 >> -1

console.log(myarray.join('-'))  // 5-4-3-2-1-0 >> 원본을 바꾸는건 아니고 리턴해주는 것
console.log(myarray)  // [ 5, 4, 3, 2, 1, 0 ]
```







## 5. Object

key-value로 이루어진 데이터 구조



키값을 이용해 어떻게 VALUE값에 접근하는지

```javascript
const endGame1 = {     
    title: '어벤져스: 엔드게임',      
    'my-lovers': [          // 띄어쓰기 할 때는 '' 해줘야한다.
        {name: '아이언맨', actor: '로다주'},         
        {name: '헐크', actor: '마크 러팔로'}     
    ] } 
console.log(endGame1)
```

```
{
  title: '어벤져스: 엔드게임',
  'my-lovers': [ { name: '아이언맨', actor: '로다주' }, { name: '헐크', actor: '마크 러팔로' } ]
}
```



```javascript
const endGame2 = {     
    title: '어벤져스: 엔드게임',      
    MyLovers: [          // 케말케이스
        {name: '아이언맨', actor: '로다주'},         
        {name: '헐크', actor: '마크 러팔로'}     
    ] } 
console.log(endGame2)
```

```
{
  title: '어벤져스: 엔드게임',
  MyLovers: [ { name: '아이언맨', actor: '로다주' }, { name: '헐크', actor: '마크 러팔로' } ]
}
```



```javascript
const endGame = {     
    title: '어벤져스: 엔드게임',      
    'my-lovers': [          // 띄어쓰기 할 때는 '' 해줘야한다.
        {name: '아이언맨', actor: '로다주'},         
        {name: '헐크', actor: '마크 러팔로'}     
    ] } 
console.log(endGame['my-lovers'])   // 이렇게 적은경우엔 이렇게 해야함
console.log(endGame['my-lovers'][1].actor)   
```

```
[ { name: '아이언맨', actor: '로다주' }, { name: '헐크', actor: '마크 러팔로' } ]
마크 러팔로
```



```javascript
const welcome = function(){   // 함수를 변수에 저장, 변수는 인자로 전달할 수 있다.
    console.log('책방에 오신걸 환영합니다.')  // 책방에 오신걸 환영합니다.
}
welcome()
```

```
책방에 오신걸 환영합니다.
```



EMTHOD의 OBECT안에 함수를 넣는 방법 잘 보기, 함수 실행법도 보기

```javascript
const welcome = function(e){   // 함수를 변수에 저장, 변수는 인자로 전달할 수 있다.
    console.log(`${e}책방에 오신걸 환영합니다.`)  // 책방에 오신걸 환영합니다.
}
welcome('13')


const comics = {    
    'DC': ['Aquaman', 'SHAZAM'],    
    'Marvel': ['Captain Marvel', 'Avengers'] 
} 
const magazines = null 
 
const bookShop = {  // key와 value가 같으면 아래처럼 써도 됨
    comics,         // comics:comics
    magazines,      // magazines:magazines
    greeting: welcome
}
bookShop.greeting('11')  // 책방에 오신걸 환영합니다.
```

```
13책방에 오신걸 환영합니다.
11책방에 오신걸 환영합니다.
```

키와 VAULE값이 같으면 하나만 써도 된다.(ES6+)



```javascript
const phone = {
    number: 123456789,
    model: 'samsung',
    app: [
        'camera app', 
        'game app'
    ], 
    test: function(message) {
        return message
    }
}

console.log(phone.number)  >> 123456789
console.log(phone.model)   >> samsung

console.log(phone.test('hh'))   >> hh

phone.app.push('new app')
console.log(phone.app)  >> [ 'camera app', 'game app', 'new app' ]
```



```javascript
const phone = {
  call: ()=>{
      console.log('ringring')
  },
  status: true,
  powerOFF: function(){
      this.status = false
      //console.log(`전원상태 ${this.status}`)
  },
  powerON: function(){
      this.status = true
      //onsole.log(`전원상태 ${this.status}`)
  },
}

phone.call()  // ringring

phone.powerOFF()
console.log(phone.status)  // false

phone.powerON()
console.log(phone.status)  // true
```



```javascript
const phone = {
  arrow: ()=>{             // arrow function    
      console.log(this)
  },
  keyword: function(){    // 이 방식으로 사용하기
      console.log(this)
  },
  numberchange(change){
      this.number = change
  }
}
```

```
phone.arrow()   >> {}   
this : 내가 어디에 있든지 부모의 최상단을 가리킴(브라우저 = window)
(브라우저의 this는 항상 최상위 객체를 가리킨다. = chrome 브로우저 = window)
```

```
phone.keyword()   
>>
{
  arrow: [Function: arrow],
  keyword: [Function: keyword],
  numberchange: [Function: numberchange]
}
this : 애가 존재하는 객체 (phone)
```

```
phone.numberchange(1234)
console.log(phone.number)  // 1234
```







## 6. JSON(javascript object notation)

### Json 정의

key-value 형태의 자료구조를 js object와 유사한 모습으로 표현하는 표기법

Javascript 객체 문법을 따르는 문자 기반의 데이터 포맷

모습만 비슷할 뿐이고 실제로 object처럼 사용하려면 다른 언어들처럼 js에서도 parsing(구문분석)작업이 필요하다.(규격이 정해져 있다.)

```javascript
["name":"xxxx"]
```

```javascript
const me = {
    name: 'change',
    'phone number': '12341234',
    product: {
        phone: 'iphone',
        notebook: 'me',
    }
}
```

mbn문서 보기

```
https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/JSON#%EC%95%84%EB%8B%88_%EB%8C%80%EC%B2%B4_JSON%EC%9D%B4_%EB%AD%90%EC%A3%A0
```





### stringify()

object(json) 객체를 => String 객체로 변환

저장하고 빼올때 Object => JOSN(문자열형태) 으로바꿔서 로컬스토리지로 

```javascript
const jsonData = JSON.stringify(me)  // string
console.log(me)
```

```
{"name":"change","phone number":"12341234","product":{"phone":"iphone","notebook":"me"}}
```

데이타로 전송할 때 한 줄의 파람 형태나 문자열로 보낼 수 있어서 사용



### parse()

 string 객체를 => object(json) 객체로 변환(로컬스토리지에서 JSON으로 변환) 

OBJECT구조로 사용하기 때문

```javascript
const perseData = JSON.parse(me)  // object
console.log(me)
```

```
{
  name: 'change',
  'phone number': '12341234',
  product: { phone: 'iphone', notebook: 'me' }
}
```

화면에서 접근/사용하는데 적합



아니면 ㅈㅅ







## 7. 함수

### 함수 선언식

```javascript
function add(num1, num2) {
    return num1 + num2
}
console.log(add(2, 10))
```



### 함수 표현식

```javascript
const ssafy1 = function (name) {
    console.log(`hello ${name}`)
}
ssafy1('change')
```



### 화살표 함수 & syntactic sugar

```javascript
const ssafy2 = (name) => {
    console.log(`hello ${name}`)
}
ssafy2('change')
```

```javascript
// 소괄호 생략 => 매개변수(인자) 하나일 때
const ssafy3 = name => {
    console.log(`hello ${name}`)
}
ssafy3('change')
```

```javascript
// 중괄호 생략 => 표현식(return문이 한 줄일 때)이 하나일 때
const ssafy4 = name => `hello ${name}`
console.log(ssafy4('change'))
```



### 함수선언 후 바로 실행

```javascript
const p = function(){return 'hello'}()
undefined
```

```
p
"hello"
```

함수가 선언이 되고 뒤에 `()`함수를 바로 실행한다.(연속적으로 일어남)



```javascript
const b = (()=>{return '123'})()
undefined
```

```javascript
b
"123"
```

에로우 함수도 마찬가지









## 8. Array helper methods

공식문서 보면서 직접써보기

### forEach

주어진 함수를 배열 요소 각각에 대해 실행합니다.

```javascript
function handelPosts(){
    const posts = [
        {id:50, title:"javascript"},
        {id:100, title:"python"},
        {id:123, title:"css"}
    ]
    // for문
    for (let i = 0; i < posts.length; i++){
        console.log(posts[i])
        console.log(posts[i].id)
        console.log(posts[i].title)
    }
    
    // forEach문
    posts.forEach(function(post){
        console.log(post)
        console.log(post.id)
        console.log(post.title)
    })
    
    // forEach문
    posts.forEach((post)=>{
        console.log(post)
        console.log(post.id) 
        console.log(post.title)
    })
}
handelPosts()
```



### map

배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환합니다.

```javascript
const images = [
    {height:10, width:20},
    {height:14, width:25},
    {height:50, width:15},
]

// map
const areas = images.map(function(image){
    return image.height*image.width
})
console.log(areas)  >> [ 200, 350, 750 ]

// map(arrow function)
const double = images.map(image => image.height*image.width)
console.log(double)  >> [ 200, 350, 750 ]
```





### filter

주어진 함수의 테스트를 통과하는 모든 요소를 모아 새로운 배열로 반환합니다.

```javascript
const numbers = [1,2,3,4,5]
const evenNumber = numbers.filter(function(number){
    return number % 2 === 0
})
console.log(evenNumber)  >> [ 2, 4 ]
```





### find

주어진 판별 함수를 만족하는 **첫 번째 요소**의 **값**을 반환합니다. 그런 요소가 없다면 `undefined`를 반환합니다.

```javascript
const users = [
    {name:'change', location:'gj'},
    {name:'justin', location:'gm'},
    {name:'tak', location:'dj'},
    {name:'junho', location:'dj'},
    {name:'neo', location:'so'},
]

const user1 = users.find(function(user){
    return user.location === 'dj'
})
console.log(user1) >> { name: 'tak', location: 'dj' }
```



### every

 배열 안의 `모든` 요소가 주어진 판별 함수를 통과하는지 테스트합니다.

빈 배열에서 호출하면 무조건 `true`를 반환합니다.

```javascript
function isBigEnough(element, index, array) {
  return element >= 10;
}
[12, 5, 8, 130, 44].every(isBigEnough);   // false
[12, 54, 18, 130, 44].every(isBigEnough); // true

[12, 5, 8, 130, 44].every(elem => elem >= 10); // false
[12, 54, 18, 130, 44].every(elem => elem >= 10); // true
```





### some

배열 안의 `어떤` 요소라도 주어진 판별 함수를 통과하는지 테스트합니다.

```javascript
function isBiggerThan10(element, index, array) {
  return element > 10;
}
[2, 5, 8, 1, 4].some(isBiggerThan10);  // false
[12, 5, 8, 1, 4].some(isBiggerThan10); // true

[2, 5, 8, 1, 4].some(elem => elem > 10);  // false
[12, 5, 8, 1, 4].some(elem => elem > 10); // true
```

```javascript
// 값이 존재하는지 확인
var fruits = ['apple', 'banana', 'mango', 'guava'];

function checkAvailability(arr, val) {
    return arr.some(function(arrVal) {
        return val === arrVal;
    });
}

checkAvailability(fruits, 'kela'); //false
checkAvailability(fruits, 'banana'); //true


var fruits = ['apple', 'banana', 'mango', 'guava'];

function checkAvailability(arr, val) {
    return arr.some(arrVal => val === arrVal);
}

checkAvailability(fruits, 'kela'); //false
checkAvailability(fruits, 'banana'); //true
```





### reduce

 배열의 각 요소에 대해 주어진 **리듀서**(reducer) 함수를 실행하고, 하나의 결과값을 반환합니다.

```javascript
const scores = [100,80,88,92,95,70]
const total = scores.reduce((total, score)=>{
    return total += score
}, 0)  // 뒤에 초기값 설정하지 않으면 배열의 첫번째 요소를 사용
console.log(total)
```







# 2. dom

## 1. Event Listener 구분

- `click` – 마우스버튼을 클릭하고 버튼에서 손가락을 떼면 발생한다.
- `mouseover` – 마우스를 HTML요소 위에 올리면 발생한다.
- `mouseout` – 마우스가 HTML요소 밖으로 벗어날 때 발생한다.
- `mousemove` – 마우스가 움직일때마다 발생한다. 마우스커서의 현재 위치를 계속 기 록하는 것에 사용할 수 있다.
- `keypress` – 키를 누르는 순간에 발생하고 키를 누르고 있는 동안 계속해서 발생한다.
- `keydown` – 키를 누를 때 발생한다.
- `keyup` – 키를 눌렀다가 떼는 순간에 발생한다.
- `load` – 웹페이지에서 사용할 모든 파일의 다운로드가 완료되었을때 발생한다.
- `scroll` – 스크롤바를 드래그하거나 키보드(up, down)를 사용하거나 마우스 휠을 사용 해서 웹페이지를 스크롤할 때 발생한다. 페이지에 스크롤바가 없다면 이벤트는 발생하 지 않다.
- `change` – 폼 필드의 상태가 변경되었을 때 발생한다. 라디오 버튼을 클릭하거나 셀렉 트 박스에서 값을 선택하는 경우를 예로 들수 있다.
- `input` - input 또는 textarea 요소의 값이 변경되었을 때
- `submit` - form을 submit 할 때



## 2. DOM selector

```
(#sections) -> sections 아이디를 가진 요소를 찾습니다
(.section) -> section 클래스명을 가진 요소를 찾습니다
```



- querySelector() :   특정 name 이나 id 를 제한하지않고 css선택자를 사용하여 요소를 찾습니다.

    반환객체는 `한개의 요소`만 찾을수있으며 동일한 클래스명 을 가진 객체가 있을경우 html문서내의 `첫번째`를 나타나는 요소를 반환합니다.

  

- querySelectorAll() :   지정된 셀렉터 그룹에 일치하는 다큐먼트의 엘리먼트 리스트를 나타내는 정적(살아 있지 않은) `NodeList` 를 반환. (for문 또는 foreach 문을 사용)

  또한 (',') 을 사용하면  여러요소를 한번에 가져올수있다.





## 3. event listener 예시

특정한 DOM element(무엇을) 를 어떠한 행동을 했을 때(언제) , 어떻게 한다.

```javascript
// 1. 무엇을 
const button = document.querySelector('#some-button') 
 
// 2. 언제 => 버튼을 '클릭' 하면 
button.addEventListener('click', function (event) {     
    const area = document.querySelector('#my')     

	// 3. 어떻게 => 뿅     
    area.innerHTML = '<h1>뿅</h1>' 
})
```

이벤트 리스너에서의 콜백함수에는 arrow function 을 사용하지 않는다.











# 3. 비동기 처리 및 axios

### 비동기 처리

특정 코드의 연산이 끝날 때까지 코드의 실행을 멈추지 않고 다음 코드를 먼저 실행하는 자바스크립트의 특성

화면에서 서버로 데이터를 요청했을 때 서버가 언제 그 요청에 대한 응답을 줄지도 모르는데 마냥 다른 코드를 실행 안 하고 기다릴 순 없기 때문

이는 파이썬(blocking)과 자바스크립트(non-blocking)의 가장 큰 차이점이다.



### axios 

브라우저에서 XHR(XMLHttpRequest)를 보내주고 그 결과를 promise 객체로 반환해주는 라이브러리이다(Promise : 자바스크립트 비동기 처리에 사용되는 객체)

```html
<-- cdn -->
<body>     
    <script src="https://unpkg.com/axios/dist/axios.min.js"></script> 
</body> 
```

```javascript
axios.get('/posts/')   
    .then(function(response) {     
    	console.log(response)   
}          

const data = {title: '제목', content: '내용'} 
axios.post('/posts/', data)     
    .then(function(response) {      
    	console.log(response)  
}
```

`axios`는 `promise객체`를 반환하여 `.then`을 통해 해당하는 작업이(axios 요청작업) 완료된(`resolve`) 경우 실행 도리 로직을 구현할 수 있다.

`.catch`에서는 `reject`된 결과를 받아서 처리 할 수 있다.(콜백지옥을 해결하기 위한 약속)



비동기 처리 axios : url로 요청함 > promise객체로 포장해서 준다.(약속) > 이걸 then이나 catch로 풀어줘야한다. 

성공 then(resolve), 실패 catch(reject)





- 브라우저는 싱글쓰레드에서 이벤트 기반(event driven) 방식으로 실행된다.
- call stack : 함수가 호출되면 순차적으로 call stack에 쌓이고 순차적으로 실행된다. task가 종료하기 전까지는 다른 task를 수행할 수 없다.
- callback queue : 비동기처리 함수의 콜백, 타이머(setTimeout), 이벤트헨들러 등이 기록되는 곳으로 이벤트 루프에 의해 특정시점에 콜 스택으로 이동되어 실행 됨.
- event loop : 콜 스택과 콜백 큐에 작업이 (실행될 함수) 있는지 확인하며 작업을 실행 한다.





## 4. Ajax 및 django

### Ajax(Asynchronous JavaScript and XML, 에이잭스)

비동기적인 웹 애플 리케이션의 제작을 위해 아래와 같은 조합을 이용하는 웹 개발 기법이다

새로고침 없이 페이지의 일부만을 위한 데이터 로드 기법(서버와 데이터를 주고 받을 수 있다.)

비동기적 정보 교환 기법

XML이라고 명시되어있긴 하지만, JSON이나 일반 텍스트 파일과 같은 다른 데이터 오브젝트들도 사용 가능

```
동기처리모델 (synchronouse processing model) 의 경우,
브라우저는 스크립트가 서버로부터 데이터를 수집하고 이를 처리한 후 페이지의 나머지 부분이 모두 로드될 때 까지 대기한다.

반면에 비동기 처리 모델 (asynchronouse processing model) 의 경우,
브라우저가 서버에 데이터를 요청하면, 작업이 완료되는 것을 기다리지 않고 나머지 페이지를 계속해서 로드하고 사용자와의 상호작용을 처리한다.
```



![캡처](assets/캡처-1573366661039.PNG)

- 조합

  - 표현 정보를 위한 HTML/CSS

  - 동적인 화면 출력 및 표시 정보와의 상호작용을 위한 DOM, JS

  - 웹 서버와 비동기적으로 데이터를 교환하고 조작하기 위한 데이터 - JSONXML

- Ajax 애플리케이션은 필요한 데이터만을 웹서버에 요청해서 받은 후 클라이언트에서 데이터에 대한 처리를 할 수 있다.
- 이것은 이미 존재하던 기술이었지만 2000년도 중반 이후로 인기를 끌기 시작했다. 구 글은 2004년에 G메일, 2005년에 구글 지도 등의 웹 애플리케이션을 만들기 위해 비동기식 통신을 사용했다.
- 웹 서버의 응답을 처리하기 위해 클라이언트 쪽에서는 자바스크립트를 쓴다. 웹 서버에 서 전적으로 처리되던 데이터 처리의 일부분이 클라이언트 쪽에서 처리 되므로 웹 브라 우저와 웹 서버 사이에 교환되는 데이터량과 웹서버의 데이터 처리량도 줄어들기 때문 에 애플리케이션의 응답성이 좋아진다
- 한편, 웹 개발자들은 때때로 Ajax를 단순히 웹 페이지의 일부분을 대체하기 위해 사용 한다. 비 AJAX 사용자가 전체 페이지를 불러오는 것에 비해 Ajax 사용자는 페이지의 일부분만을 불러올 수가 있다. 이것으로 개발자들이 비 AJAX 환경에 있는 사용자의 접 근성을 포함한 경험을 보호할 수 있으며, 적절한 브라우저를 이용하는 경우에 전체 페 이지를 불러오는 일 없이 응답성을 향상시킬 수 있다.
