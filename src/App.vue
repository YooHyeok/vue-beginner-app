<!-- 루트 컴포넌트 -->
<template>

  <div class="name">YooHyeok School</div> <!-- 문자열로 출력 -->

  <div class="name">
    {{ name }} <!-- Composition API 데이터 바인딩-->
  </div>

  <div>Vue3에서는 복수개의 엘리멘트를 하나의 빈 엘리먼트(태그)로 감싸지 않아도 된다.</div>

  <div class="name">
    {{ greeting(name) }} <!-- Composition API 함수 호출 및 바인딩-->
  </div>

  <div class="name">
    {{ greet }} <!-- Composition API 바인딩-->
  </div>
  
</template>

<script>

export default {
 
  /**
   * setup function
   * Composition API 방식
   * Object 형태로 반환한다.
   * 반환되는 변수들은 template 에서 접근이 가능해진다.
   * {{ name }}
   */
  setup() {
    const name = 'YooHyeok School';

    const greeting = (name) => {
      return 'Hello, ' + name;
    };

    /**
     * 함수 호출 및 반환값 변수 저장
     */
    const greet = greeting(name);

    return {
      name,
      greeting,
      greet
    }
  }
}
</script>

<style>
.name {
  color: red;
}
</style>