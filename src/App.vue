<!-- 루트 컴포넌트 -->
<template>
  <!-- YooHyeok School -->
  <div class="name">
    {{name}} <!-- Composition API 데이터 바인딩-->
  </div>
  <div>Vue3에서는 복수개의 엘리멘트를 하나의 빈 엘리먼트(태그)로 감싸지 않아도 된다.</div>
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
    const name = 'YooHyeok School1';

    return {
      name
    }
  }
}
</script>

<style>
.name {
  color: red;
}
</style>