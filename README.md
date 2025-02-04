# *Vue Cli*
## *Install & Run*
<details>
<summary>펼치기/접기</summary>
<br>

- **Vue Cli 설치**
    
    ```bash
    npm install -g @vue/cli
    ```
    
- **Vue Version**
    
    ```bash
    vue -V
    ```
    
- **Vue 프로젝트 생성**
    
    ```bash
    vue create 프로젝트명
    ```
    
- **Vue3 선택 및 NPM/YARN중 택1**
    
    ```bash
    ? Please pick a preset
    > Default ([Vue 3] babel, eslint)
      Default ([Vue 3] babel, eslint)
    Manually select features
    ```
    ```bash
    ? Pick the pacage manager to user when installing dependencies:
    > NPM
    YARN
    Manually select features
    ```
- **vetur 플러그인 설치**  
  - VSCode IDE 좌측 extentions 탭에서 vetur 검색 후 설치

  - `jsconfig.json`  
    reference : https://vuejs.github.io/vetur/guide/
    ```json
    {
      "compilerOptions": {
        "target": "es2015",
        "module": "esnext",
        "baseUrl": "./",
        "paths": {
          "@/*": ["components/*"]
        }
      },
      "include": [
        "src/**/*.vue",
        "src/**/*.js"
      ]
    }
    ```
- **실행**
    ```bash
    npm run serve
    ```
</details>

<br>

- ### `package.json`

  - **dependencies**  
  개발 하는 동안과 이후 Production 즉 배포후에도 필요한 패키지 모음
  - **devDependencies**   
  개발 하는 동안 도움을 주는 유용한 패키지 모음

  두 속성에 선언된 패키지 요소 값들은 `npm install` 명령어에 의해 node_modules라는 디렉토리에 설치된다.

- ### publc > `index.html`
  프로젝트 실행시 웹 브라우저에 열릴때, 최초 렌더링 되는 html 파일이다.
  ```html
  <div id="app"></div>
  <!-- built files will be auto injected -->
  ```
  id가 app인 div영역에 Vue application이 구동된다.  
  추후 빌드시 주석 영역에 자바스크립트 같은 코드들이 들어가게 된다.

- ### src > `main.js`
  ```js
  import { createApp } from 'vue'
  import App from './App.vue'

  createApp(App).mount('#app')
  ```
  vue 로 부터 createApp 함수를 import한 뒤 최 상위 컴포넌트인 App 컴포넌트를 해당 함수에 인자로 전달한다.  
  mount 함수에 의해 index.html에서 id가 app인 div영역에 mount 한다.
  - mount()의 역할  
    - vue 애플리케이션 초기화 및 시작
    - `App.vue` 파일에서 정의한 루트 컴포넌트를 렌더링하고, 실제 DOM에 삽입
    - 마운트 된 Vue 애플리케이션은 `App.vue` 내부의 컴포넌트 구조를 기반으로 가상 DOM 을 생성하고, 이를 실제 DOM에 반영하여 화면에 출력한다.

- ### src > `App.vue`

  ```js
  <template>
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </template>
  <script>
  import HelloWorld from './components/HelloWorld.vue'

  export default {
    name: 'App',
    components: {
      HelloWorld
    }
  }
  </script>
  ```  
  - \<template>  
  mount 역할에서 설명한 루트 컴포넌트가 바로 template 태그 영역이다.    
  - \<script>  
    - HelloWorld컴포넌트를 import하고 components 옵션을 사용하여 등록한다.
    - `export default`를 통해 App이라는 name속성으로 Vue컴포넌트 객체를 내보낸다.

<br>

# *`setup()` Function*
**CompositionAPI** 방식의 초기화 함수  
해당 컴포넌트 객체 내부에서 사용할 변수/함수 들을 setup 함수 내부에 선언하고, 반환한다.  
반환된 데이터(변수/함수)는 template에서 사용이 가하다.  
export default 영역에 선언하여 사용한다.  
(Vue 내부적으로 setup function을 호출하는것 같다)  

<br>

# *Element의 Event 바인딩*
element에 `v-on:{이벤트명}="{함수명}"` 와 같이 속성을 지정해준다  
({중괄호는 생략})

```html
<template>
  <button 
    class="btn btn-primary"
    v-on:click="consoleLog"
  >
      console-log
  </button>
</template>
<script>
  const consoleLog = () => {
    console.log('hello world');
  }
</script>
```


<br>

# *반응형 변수 ref 와 reactive*

- *ref*
일반적으로 ref 변수는 String, Object, Array에 대한 자료형 사용이 가능하다.  
단, ref 내부 value에 접근하기 위해서는 변수명.value 를 통해 접근할 수 있다.  
수정할 경우에 꼭 value를 통해 접근하고, 기본 자료형인 number 혹은 string의 경우 value에만 접근해서 바로 값을 변경할 수 있지만,  
object 혹은 array의 경우 value에서 1depth 더 들어가야 한다.  

- *reactive*
배열 혹은 Object 자료형에 대해서만 사용이 가능하다.
Object는 Key로 접근하고, 배열의 경우 변수명[index] 와 같이 index 를 통해 접근하여 수정이 가능하다.

```html
<script>
import {reactive, ref} from 'vue';
export default {
  setup() {
    const nameRef = ref('YooHyeok School');
    const nameRefObj = ref({id: 1});
    const nameReactive = reactive({
      id : 1
    });
    const nameReactivePri = reactive(["hi","bye"]);

    const updateNameRef = () => {
      nameRef.value = 'Codeaholic';
    }

    const updateNameRefObj = () => {
      nameRefObj.value.id = 'Codeaholic';
    }
    const updateNameReactive = () => {
      nameReactive.id = 'Codeaholic';
    }
    const updateNameReactivePri = () => {
      nameReactivePri[0] = 'Hello';
    }
    return {
      nameRef,
      nameRefObj,
      nameReactive,
      nameReactivePri,
      updateNameRef,
      updateNameRefObj,
      updateNameReactive,
      updateNameReactivePri
    }
  }
}
</script>
```