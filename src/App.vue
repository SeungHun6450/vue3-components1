  <!-- Components 기초  -->
  <!--
<template>
  <MyBtn>Banana</MyBtn>
  <MyBtn 
    :color="color">
    <span style="color: red;">Banana</span>
  </MyBtn>
  <MyBtn 
    large
    color="royalblue">
    Apple
  </MyBtn>
  <MyBtn>Cherry</MyBtn>
</template>

<script>
import MyBtn from '~/components/MyBtn'

export default {
  components: {
    MyBtn
  },
  data() {
    return {
      color: "#000"
    }
  }
}
</script>
-->


<!-- Components 속성, 상속 -->
<!--
<template>
  <MyBtn 
    class="heropy" 
    style="color:red;"
    title="Hello world">
    Banana
  </MyBtn>
</template>

<script>
import MyBtn from '~/components/MyBtn'

export default {
  components: {
    MyBtn
  }
}
</script>
-->

<!-- Components Emit -->
<!-- @change-msg : @changeMsg 대문자를 카멜케이스에서 대시케이스로 변경해줘야함 -->
<template>
  <MyBtn 
    @heropy="log"
    @change-msg="logMsg">
    Banana
  </MyBtn>
</template>

<script>
import MyBtn from '~/components/MyBtn'

export default {
  components: {
    MyBtn
  },
  methods: {
    log(e) {
      // 이벤트 매개변수를 만들어 출력
      console.log('Click!!')
      console.log(e)
    },
    logMsg(msg){
      console.log(msg)
    }
  }
}
</script>