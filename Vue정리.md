# README

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

<br>

1. `package.json` 에서 no-console 에러 해결

   ```python
   "rules": {
         "no-console": "off"
       },
   ```

   ## `App.vue` 

2. mounted속성에서 데이터 가져오기

   ```js
   data() {
       return {
         // 활용할 데이터를 정의하시오.
         movies : [],
         genres : []
       }
     },
     mounted() {
       // 0. mounted 되었을 때, 
       // 1) 제시된 URL로 요청을 통해 data의 movies 배열에 해당 하는 데이터를 넣으시오. 
       const MOVIE_URL = 'https://gist.githubusercontent.com/eunji-j/3c2b5e9142de6c4cfd7cfe9e1e172141/raw/d7f6ae88b04a67c8f3069c3d73de253f659321df'
       axios.get(MOVIE_URL)
         .then(response=>{
           console.log(response)
           this.movies = response.data
         })
         .catch(error=>{
           console.log(error)
         })
       // 2) 제시된 URL로 요청을 통해 data의 genres 배열에 해당 하는 데이터를 넣으시오.
       const GENRE_URL = 'https://gist.githubusercontent.com/eunji-j/7ad4e77d55cd8b7db705952edb08ecd9/raw/4a1fb82b869e93aafbaca941bc79e2f8e1984d40/'
       axios.get(GENRE_URL)
         .then(response=>{
           console.log(response)
           this.genres = response.data
         })
         .catch(error=>{
           console.log(error)
         })
   
       // axios는 위에 호출되어 있으며, node 설치도 완료되어 있습니다.
     },
   ```

   3. component 불러오고 등록

   ```js
   // 1-1. 저장되어 있는 MovieList 컴포넌트를 불러오고,
   import MovieList from './components/movies/MovieList.vue'
   
   // 
   
   export default {
     name: 'app',
     // 1-2. 아래에 등록 후
     components: {
       MovieList
     },
   ```

   4. component 호출 및 정보내리기

   ```html
   <template>
     <div id="app">
       <div class="container">
         <!-- 1-3. 호출하시오. 
           필요한 경우 props를 데이터를 보내줍니다.
         -->
         <!-- MovieList로 정보내리기 -->
         <MovieList :movies="movies" :genres="genres"/>
       </div>
     </div>
   </template>
   ```

   ## `MovieList.vue`
   
   5. 부모가 내려준 데이터 정의해주기

   ```js
   props : ['movies', 'genres'],
   ```
   
6. component 불러오고 등록
   
   ```js
   // 1-1. 저장되어 있는 MovieListItem 컴포넌트를 불러오고,
   import MovieListItem from './MovieListItem.vue'
   
   export default {
     name: 'MovieList',
     // 1-2. 아래에 등록 후
     components: {
       MovieListItem,
     },
   ```
   
   7. MovieListItem for문으로 불러오기
   
   ```html
   <div class="row">
         <!-- https://kr.vuejs.org/v2/guide/list.html 참고 -->
         <MovieListItem v-for="movie in onselectedGenre" :key="movie.id" :movie="movie"/>
       </div>
   ```
   
   ## `MovieListItem.vue`
   8. 부모가 내려준 데이터 정의해주기
   
   ```js
   props: ['movie'],
   ```
   
   9. component 불러오고 등록
   
   ```js
   import MovieListItemModal from './MovieListItemModal.vue'
   
   export default {
     name: 'MovieListItem',
     // 1-2. 아래에 등록 후
     components: {
       MovieListItemModal
     },
   ```
   
   10. MovieListItemModal 사용법
   
   ```html
   <template>
     <div class="col-3 my-3">
       <!-- img 태그에 src와 alt값(영화제목)을 설정하시오 -->
       <img class="movie--poster my-3" :src="movie.poster_url" >
       <!-- 영화 제목을 출력하시오. -->
       <h3>{{movie.name}}</h3>
       <!-- 모달을 활용하기 위해서는 data-taget에 모달에서 정의된 id값을 넣어야 합니다. -->
       <button class="btn btn-primary" data-toggle="modal" :data-target="'#movie-'+movie.id">영화 정보 상세보기</button>
       <!-- 1-3. 호출하시오.
         필요한 경우 props를 데이터를 보내줍니다.
         -->
       <MovieListItemModal :movie="movie"/>
     </div>
   </template>
   ```
   
   ## `MovieListItemModal.vue`
   11. 부모가 내려준 데이터 정의해주기
   
   ```js
   props: ['movie'],
   ```
   
   12. Modal 페이지 만들기
   
   ```html
   <template>
   <!-- vue 콘솔에서 확인하여, 추가 정보들도 출력하세요. -->
   <!-- 고유한 모달을 위해 id 속성을 정의하시오. 예) movie-1, movie-2, ... -->
   <div class="modal fade" tabindex="-1" role="dialog" :id="'movie-'+movie.id">
     <div class="modal-dialog" role="document">
       <div class="modal-content">
         <div class="modal-header">
           <!-- 영화 제목을 출력하세요. -->
           <h5 class="modal-title">{{movie.name}}</h5>
           <button type="button" class="close" data-dismiss="modal" aria-label="Close">
             <span aria-hidden="true">&times;</span>
           </button>
         </div>
         <div class="modal-body">
           <img :src="movie.poster_url" width="50%">
           <hr>
           <p>{{movie.rating}}</p>
           <!-- 영화 설명을 출력하세요. -->
           <p>{{movie.description}}</p>
         </div>
         <div class="modal-footer">
           <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
         </div>
       </div>
     </div>
   </div>
   </template>
   ```
   
   ## `MovieList.vue`
   
   13. 장르 선택 Select Option 
   
   ```html
   <!-- 2. 장르 선택(제일 마지막에 구현하시오.)
       2-1. App 컴포넌트로 부터 받은 genres를 반복하여 드롭다운을 완성 해주세요.
       2-2. 드롭다운은 selectedGenreId data와 양방향바인딩(v-model)이 됩니다.
       2-3. 값 변경이 되면, 특정한 함수를 실행 해야합니다.
        -->
       <select class="form-control" v-model="selectedGenreId">
         <!-- https://kr.vuejs.org/v2/guide/list.html 참고 -->
         <option value="">전체보기</option>
         <option v-for="genre in genres" :key="genre.id" :value="genre.id" >
           {{genre.name}}
         </option>
       </select>
   ```
   
   14. 장르선택시 그 장르의 영화 불러오기
   
   ```js
   computed: {
       onselectedGenre: function(){
         if (this.selectedGenreId===''){
           return this.movies
         }else{
           return this.movies.filter((movie)=>{
             return movie.genre_id === this.selectedGenreId
           })
         }
       }
     }
   ```

<br>

## 사전정보

### `v-if, v-bind, v-for` 문법

1. 인덱스 값을 for문 돌리고 싶을 때 2번째 인자로 전달 / object의 value와 name, index 모두 이용할 때

```html
<div v-for="(value, name, index) in object">
  {{ index }}. {{ name }}: {{ value }}
</div>
```

2. `in` 대신에 `of`를 구분자로 사용할 수 있습니다. 
3. for문에서 `v-bind:key`를 필수로 지정해야 하는 이유

```
Vue에서 개별 DOM 노드들을 추적하고 기존 엘리먼트를 재사용, 재정렬하기 위해서 v-for의 각 항목들에 고유한 key 속성을 제공해야 합니다. 
```

4. `v-bind:data-target="'#movie-'+movie.id"` 작은따옴표: String



### `v-for`를 이용한 동적 옵션 렌더링

```html
<select v-model="selected"> 
    <!-- 선택하면 data의 selected값이 바뀐다. 양방향 바인딩이기 때문에 data의 selected 기본값과 option의 value값이 같을 때 그 값이 기본값으로 설정된다. -->
  <option v-for="option in options" v-bind:value="option.value">
    {{ option.text }}
  </option>
</select>
<span>Selected: {{ selected }}</span>
<!-- options는 data나 props에 있어야한다. -->
```



### 정보 올리기, 내리기

![image](image.png)

### axios로 정보 받는 법

```js
data() {
    return {
      movies : [],
      genres : []
    }
  },
```

```js
mounted() {
    const MOVIE_URL = 'https://gist.githubusercontent.com/eunji-j/3c2b5e9142de6c4cfd7cfe9e1e172141/raw/d7f6ae88b04a67c8f3069c3d73de253f659321df'
    axios.get(MOVIE_URL)
      .then(response=>{
        console.log(response)
        this.movies = response.data
      })
      .catch(error=>{
        console.log(error)
      })
    const GENRE_URL = 'https://gist.githubusercontent.com/eunji-j/7ad4e77d55cd8b7db705952edb08ecd9/raw/4a1fb82b869e93aafbaca941bc79e2f8e1984d40/'
    axios.get(GENRE_URL)
      .then(response=>{
        console.log(response)
        this.genres = response.data
      })
      .catch(error=>{
        console.log(error)
      })
},
```



### computed / watch 비교

> computed
>
> - 저장가능
> - 첫화면에 전체보기 가능
> - **변경**될 때만 함수를 실행한다.
> - 함수이름을 리턴값으로 사용가능하다.
>
> watch
>
> * 데이터 변경을 관찰하고 이에 반응 하므로 전체보기를 기본값으로 해놓을수 없다.

[https://kr.vuejs.org/v2/guide/computed.html#computed-%EC%86%8D%EC%84%B1-vs-watch-%EC%86%8D%EC%84%B1](https://kr.vuejs.org/v2/guide/computed.html#computed-속성-vs-watch-속성)

