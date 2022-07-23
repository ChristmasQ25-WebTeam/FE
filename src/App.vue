<template>
<!--비밀번호 재설정 링크 발송 모달창 -->
<div class="black-bg" v-if="ClickButton == true">
  <div class="white-bg">
    <div class="password_represent">
     <span class="title">비밀번호 재설정 링크를</span>
      <span class="title"> 발송하였습니다</span>
      <span class="mail">메일함을 확인해주세요</span>
      <hr width="220px">
      <span @click="ClickButton= false" class="ok">확인</span>
    </div>
   </div>
  </div>


<!--비밀번호 재설정 링크 발송 모달창 (API 적용할때 추가예정)
  <div class="black-bg" v-if="ClickButton == true">
  <div class="white-bg">
    <div class=  "password_represent">
      <span class="title">등록되지 않은</span>
      <span class="title">이메일입니다</span>
      <hr width="200px">
      <span @click="ClickButton= false" class="ok">확인</span>
    </div>
   </div>
  </div>-->


  <div class="key_icon">
  <img alt="Vue logo" src="./assets/key.png">
  </div>

  <div class="password_guide">
    <div class="info1">이메일을 입력해주세요!</div>
    <div class="info1">비밀번호 재설정 링크가 </div>
    <div class="info1">발송됩니다</div>
  </div>

  <div class="bottom_input">
    <input type="text" name="" placeholder="이메일 입력해주세요 !">
  </div>

  <button @click="ClickButton =true" class="next_button">완료</button>

</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      ClickButton:false
    }
  },
  components: {
  }
}
</script>

<style>

body{
  margin: 0;
  display: flex;
  background-color: #920000;
  align-items:  center;
  justify-content: center;
}

div{
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 100px;
  display: flex;
  flex-direction: column;
  align-items:  center;
  /* justify-content: center; */

  background-color: white;
  border-radius: 5px;
  padding-top: 70px;
  width: 360px;
  height: 640px;
}

.key_icon img{
  width:150px;
}

.password_guide{
  display: flex;
  flex-direction: column;
  margin-top:60px;
  font-size:23px;
  font-weight: bold;
}

.bottom_input{
  margin-top:70px;
}

.bottom_input input{
  width:220px;
  height: 30px;
}

.next_button{
  margin-top:50px;
  width:100px;
  height: 25px;
}

/*모달창 css*/

.password_represent{
  display: flex;
  flex-direction: column;
  padding:15px;
}

.password_represent .title{
  font-size: 20px;
  font-weight: bold;
}

.password_represent .mail{
 padding-top:20px;
 font-size:15px;
}

.password_represent .ok{
  padding-top: 27px;
  font-size:13px;
  font-weight: bold;
  color:#920000;
}

  .black-bg{
    position: absolute;
    top: 0;
    left: 0;
    height: 1000px; /*100%*/
    width: 1000px; /*100%*/
}
  hr{
    height: 2px;
    margin-top:40px;
    background-color: rgb(8, 8, 8);
    border: 0;
  }

  .white-bg{
    position: fixed;
    top: 55px;
    bottom: 0;
    left: 0;
    right: 0;
    margin: auto;
    background:#F4E7B6;
    border-radius: 8px;
    width: 300px;
    height: 220px;

  }
</style>
