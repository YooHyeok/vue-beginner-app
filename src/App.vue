<!-- 루트 컴포넌트 -->
<template>

  <div class="name">YooHyeok School</div> <!-- 문자열로 출력 -->

  <div class="name">
    {{ name }} <!-- Composition API 데이터 바인딩-->
  </div>

  <button 
    class="btn btn-primary"
    v-on:click="consoleLog"
  >
      console-log
  </button>
  <button 
    class="btn btn-primary"
    v-on:click="updateName"
  >
      update-name
  </button>
  <div>Vue3에서는 복수개의 엘리멘트를 하나의 빈 엘리먼트(태그)로 감싸지 않아도 된다.</div>

  <div class="name">
    {{ greeting(name) }} <!-- Composition API 함수 호출 및 바인딩-->
  </div>

  <div class="name">
    {{ greet }} <!-- Composition API 바인딩-->
  </div>

    <div class="name">
    {{ nameRef }} <!-- ref 데이터 바인딩-->
  </div>
  
</template>

<script>
import {ref} from 'vue';
export default {
 
  /**
   * setup function
   * Composition API 방식
   * Object 형태로 반환한다.
   * 반환되는 변수들은 template 에서 접근이 가능해진다.
   * {{ name }}
   */
  setup() {
    let name = 'YooHyeok School';
    const nameRef = ref('YooHyeok School');

    /**
     * name 문자열 조합 반환 함수 정의
     */
    const greeting = (name) => {
      return 'Hello, ' + name;
    };

    /**
     * 함수 호출 및 반환값 변수 저장
     */
    const greet = greeting(name);

    /**
     * Click 이벤트 console출력 함수
     */
    const consoleLog = () => {
      console.log('hello world');
    }
    /**
     * Click 이벤트 name 변경 함수
     */
    const updateName = () => {
      nameRef.value = 'Codeaholic';
    }

    return {
      name,
      nameRef,
      greeting,
      greet,
      consoleLog,
      updateName
    }
  }
}
</script>

<style>
.name {
  color: red;
}
</style>