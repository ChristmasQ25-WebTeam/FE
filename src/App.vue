<template>
  <div class="black-bg check-password" v-if="pwOpen == true">
    <div class="white-bg">
      <h4>비밀번호를 입력해주세요</h4>
      <button @click="check">확인</button>
    </div>
  </div>
  <div class="black-bg check-email" v-if="emailOpen == true">
    <div class="white-bg">
      <h4>이메일 중복확인을 완료해주세요</h4>
      <button @click="check">확인</button>
    </div>
  </div>
  <div class="black-bg check-nickname" v-if="nickOpen == true">
    <div class="white-bg">
      <h4>닉네임을 입력해주세요</h4>
      <button @click="check">확인</button>
    </div>
  </div>
  

  <div id="start">
    <div class="content">
      <ul>
        <li>
          <div class="label-box">
            <span>페이지에 표기될 닉네임을<br>입력해주세요!</span>
          </div>
          <div class="input-box">
            <input type="text" class="inputText" v-model="nickName" placeholder="닉네임을 입력해주세요!">
          </div>
        </li>
        <li>
          <div class="label-box">
            <span>링크를 전달받으실 이메일을<br>입력해주세요!</span>
          </div>
          <div class="input-box">
            <input type="email" class="inputText" v-model="email" placeholder="이메일을 입력해주세요!">
            <br>
            <button class="overlap-btn" @click="chkOverlap">중복확인</button>
            <i class="fa fa-check" v-if="chkEmail == true"></i>

          </div>
        </li>
        <li>
          <div class="label-box">
            <span>아무나 작성할 수 없도록!<br>비밀번호를 입력해주세요</span>
          </div>
          <div class="input-box">
            <input type="password" class="inputText" id="inputPW" v-model="password" placeholder="비밀번호를 입력해주세요!" @change="chkInput">
            <p :class="[chkPw === false ? 'unchk' : 'chk']">*영문/숫자 포함 6자 이상</p>
          </div>
        </li>
      </ul>
    </div>
    <div class="finish">
      <button class="finish-btn" @click="submit">완료</button>
    </div>
  </div>


</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      nickName: '',
      nickOpen: false,
      password: '',
      pwOpen: false,
      chkPw: true,
      chkNum: /[0-9]/,
      chkEng: /[a-zA-Z]/,
      chkEmail: false,
      emailOpen: false
    }
  },
  methods: {
    submit(e){
      e.preventDefault();
      if (this.nickName == ''){
        this.nickOpen = true;
      }
      if (this.password == ''){
        this.pwOpen = true;
      }
      if (this.chkEmail == false){
        this.emailOpen = true;
      }
    },
    check(){
      this.nickOpen = false;
      this.pwOpen = false;
      this.emailOpen = false;
    },
    chkInput(){
      if (this.password.length < 6){
        this.chkPw = false;
      }
      if(!this.chkNum.test(this.password)){
        this.chkPw = false;
      }
      if(!this.chkEng.test(this.password)){
        this.chkPw = false;
      }
      if(this.password.length > 5 && this.chkNum.test(this.password) && this.chkEng.test(this.password))
        this.chkPw = true;
    },
    chkOverlap(){
      this.chkEmail = true;
    }
  },
  components: {
    
  }
}
</script>

<style>
@import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
* {margin: 0; padding: 0; box-sizing: border-box;}
html, body {width: 100%; height: 100%; background: green;}
ul, li {list-style: none;}
span {vertical-align: baseline;}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  
}
.black-bg .white-bg {
  width: 180px;
  background: #fff;
  border-radius: 10px;
  padding: 20px;
  margin: 150px auto;
}
.black-bg .white-bg h4 {
  padding: 0 0 10px 0;
  border-bottom: 1px solid;
  font-size: 11px;
}
.black-bg .white-bg button {
  padding: 10px 0 0 0;
  border: none;
  background: #fff;
}

#start {
  width: 200px;
  margin: 0 auto;
  background: #fff;
}

#start .content {
  text-align: center;
  padding: 10px 0;
}
#start .content ul {

}
#start .content li {
  padding: 10px 0;
}
#start .content li .label-box {
  padding: 5px 0;
}
#start .content li .label-box span {

}
#start .content li .input-box {
  
}
#start .content li .input-box .inputText {

}
#start .content li .input-box .overlap-btn {
  margin: 5px 0 0 0;
}
#start .content li .input-box i {
  padding: 0 0 0 5px;

}
#start .content li .input-box .chk {
  margin: 5px 0 0 0;
}
#start .content li .input-box .unchk {
  margin: 5px 0 0 0;
  color: #f00;
}

#start .finish {
  border-top: 1px solid ;
  text-align: center;
  padding: 10px 0;
}
#start .finish .finish-btn {

}


</style>
