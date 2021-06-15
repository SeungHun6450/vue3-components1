<!-- Components 기초 -->
<!-- slot을 사용하면 App.vue에 MyBtn의 content가 대체되서 들어가게 된다, <span>도 대체 가능 -->
<!-- 
<template>
  <div 
    :class="{ large }"
    :style="{ backgroundColor: color }"
    class="btn">
    <slot></slot>
  </div>
</template>

<script>
export default {
  // 속성처럼 받아줄 수 있는 옵션
  props: {
    color: {
      type: String,
      default: 'gray' // 기본 색상
    },
    large: {
      type: Boolean,
      default: false
    }
  }
}
</script>


<style scoped lang="scss">
  .btn {
    display: inline-block;
    margin: 4px;
    padding: 6px 12px;
    border-radius: 4px;
    background-color: gray;
    color: white;
    cursor: pointer;
    &.large {
      font-size: 20px;
      padding: 10px 20px;
    }
  }
</style> 
-->

<!-- Components 속성, 상속 -->

<!-- <h1 
    :class="$attrs.class"
    :style="$attrs.style"></h1> -->
  
  <!-- 밑에는 한번에 작성 시 v-bind 사용 -->

<!--
<template>
  <div class="btn">
    <slot></slot>
  </div>

  
  <h1 v-bind="$attrs"></h1>
</template>

<script>
export default {
  // inheritAttrs : 속성들의 상속, html속성들을 상속할 것인지의 여부
  inheritAttrs: false,
  created() {
    console.log('attrs : ', this.$attrs)
  }
}
</script>


<style scoped>
  .btn {
    display: inline-block;
    margin: 4px;
    padding: 6px 12px;
    border-radius: 4px;
    background-color: gray;
    color: white;
    cursor: pointer;
  }
</style>
-->


<!-- Components Emit -->
<!-- @dblclick : 더블 클릭 시 이벤트 발생 -->
<!-- $event : 이벤트 객체를 출력 -->
<template>
  <div class="btn">
    <slot></slot>
  </div>
  <h1 @dblclick="$emit('heropy', $event)">
    ABC
  </h1>
  <h1>
    <input 
      type="text"
      v-model="msg" />
  </h1>
</template>

<script>
export default {
  // App.vue에서 <Mybtn @"" (컴포넌트가 emit으로 넘어가서 사용되기 때문) 일치시키면 된다 
  emits: [  
    'heropy',
    'changeMsg'
  ],
  data() {
    return {
      msg: ''
    }
  },
  watch: {
    msg() {
      this.$emit('changeMsg', this.msg)
    }
  }
}
</script>


<style scoped>
  .btn {
    display: inline-block;
    margin: 4px;
    padding: 6px 12px;
    border-radius: 4px;
    background-color: gray;
    color: white;
    cursor: pointer;
  }
</style>