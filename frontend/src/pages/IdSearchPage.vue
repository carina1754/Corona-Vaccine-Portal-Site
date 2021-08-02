<template>
  <form v-on:submit.prevent="submitForm">
    <div style="padding-top:2%;">
      <h1 class="register_title">COFO</h1>
      <div style="margin-right:600px; font-size:15px; font-weight: bold;">
          아이디찾기
      </div>
      <hr align="center" width="670px" >
      <div id="width" class="ID_container">
        <lable for="name"> </lable>
        <div style="font-size: 12px; font-weight: 700; margin-bottom: 20px; margin-right: 430px;"><input class="search_checkbox" type="checkbox" value="check">회원정보에 등록한 휴대전화로 인증</div>
        <div style="margin-right:305px; margin-bottom:5px; padding:0px; font-size:14px;">
            이름            
            <input class="search_name_textinput" id="name" type="name" v-model="name">
        </div>
        <div style="margin-right:213px; margin-bottom:5px; font-size:14px;">
            휴대전화
            <input class="search_phone_textinput" id="phone" type="phone" v-model="phone" placeholder="전화번호 입력">
            <button class="search_certification" type="search_certification" v-on:submit.prevent="submitForm">인증번호 받기</button>
            <br>
            <input class="search_phone_textinput" id="phone" type="phone" v-model="phone" placeholder="인증번호를 입력하세요" style= "margin-right: 32px;">
        </div>
        <div style="font-size: 12px; font-weight: 700; margin-bottom: 20px; margin-right: 500px;"><input class="search_checkbox" type="checkbox" value="check">본인확인 이메일로 인증</div>
        <lable for="email"> </lable>
        <div style="margin-right:305px; margin-bottom:5px; padding:0px; font-size:14px;">
            이메일
            <input class="search_mail_textinput" id="email" type="email" v-model="email">
        </div>
        <button class="register_final" type="register" v-on:submit.prevent="submitForm">아이디 찾기</button>
      </div>

      <div style="margin-right:580px; font-size:15px; font-weight: bold;">
          비밀번호 찾기
      </div>
      <hr align="center" width="670px" >
      <div id="width" class="ID_container">
        <lable for="username"> </lable>
        <div style="margin-right:305px; margin-bottom:5px; padding:0px; font-size:14px;">
            아이디            
            <input class="search_username_textinput" id="username" type="username" v-model="username">
        </div>
        <lable for="name"> </lable>
        <div style="margin-right:305px; margin-bottom:5px; padding:0px; font-size:14px;">
            이름            
            <input class="search_name_textinput" id="name" type="name" v-model="name">
        </div>
        <div style="margin-right:213px; margin-bottom:5px; font-size:14px;">
            휴대전화
            <input class="search_phone_textinput" id="phone" type="phone" v-model="phone" placeholder="전화번호 입력">
            <button class="search_certification" type="search_certification" v-on:submit.prevent="submitForm">인증번호 받기</button>
            <br>
            <input class="search_phone_textinput" id="phone" type="phone" v-model="phone" placeholder="인증번호를 입력하세요" style= "margin-right: 32px;">
        </div>
        <button class="register_final" type="register" v-on:submit.prevent="submitForm">비밀번호 찾기</button>
      </div>
    </div>
    <!-- <div>
      <button type="submit"><i class="addBtn fas fa-user-plus" aria-hidden="true"></i>  구글로 로그인</button>
    </div> -->
    <div>
      <!-- <input type="checkbox" id ="login_check" value="로그인 유지" v-model="loginCheck">
      <label for="login_check" style="fontsize:">로그인유지</label> -->
    </div>
  </form>
</template>
<script>
  import axios from 'axios';
  export default {
    components: {},
    name: 'LoginPage',
    data() {
      return {
        username: '',
        password: '',
        loginCheck: '',
      }
    },
    methods: {
      submitForm: function () {
        console.log(this.username, this.password);
        var url = 'https://jsonplaceholder.typicode.com/users';
        var data = {
          username: this.username,
          password: this.password
        }
        axios.post(url, data)
          .then(function (response) {
            console.log(response);
          })
          .catch(function (error) {
            console.log(error);
          })
      }
    },
    created() {}
  }
</script>
<style>
  .register_title {
    color: #adc9ff;
    font-weight: 900;
    margin: 2.5rem 0 1.5rem;
    font-size: 100px;
    margin-top: 0px;
    margin-bottom: 10px;
  }
  body {
    text-align: center;
    background-color: #F6F6F8;
  }
  .ID_container {
    position: relative;
    z-index: 100;
    width: 650px;
    top:50%; left:29%;
    padding: 40px 10px 10px;
    border: 1px solid rgba(117, 117, 117, 0.336);
    margin-bottom: 30px;
    
  }
  .search_checkbox {
      font-size: 15px;
  }
  .search_name_textinput {
    height: 0.6cm;
    border-style: groove;
    width: 200px;
    margin-bottom: 30px;
    margin-left:60px;
    font-size: 13px;
    text-indent:15px;
    border: 1px solid black;
    box-shadow: none;
  }
  .search_username_textinput{
    height: 0.6cm;
    border-style: groove;
    width: 200px;
    margin-bottom: 30px;
    margin-left: 45px;
    font-size: 13px;
    text-indent:15px;
    border: 1px solid black;
    box-shadow: none;
  }
  .search_phone_textinput {
    height: 0.6cm;
    border-style: groove;
    width: 200px;
    margin-bottom: 30px;
    margin-left:32px;
    font-size: 13px;
    text-indent:15px;
    border: 1px solid black;
    box-shadow: none;
  }
  .search_mail_textinput {
    height: 0.6cm;
    border-style: groove;
    width: 200px;
    margin-bottom: 30px;
    margin-left:45px;
    font-size: 13px;
    text-indent:15px;
    border: 1px solid black;
    box-shadow: none;
  }
  .birth_textinput{
    height: 1cm;
    border-style: groove;
    width: 85px;
    margin-bottom: 30px;
    margin-right:10px;
    font-size: 13px;
    text-indent:15px;
    border: 1px solid black;
    box-shadow: none;
  }
  .phone_textinput{
    height: 1cm;
    border-style: groove;
    width: 210px;
    margin-bottom: 5px;
    margin-right: 2px;
    font-size: 13px;
    text-indent:15px;
    border: 1px solid black;
    box-shadow: none;
  }
  .month_select {
    height: 41px;
    border-style: groove;
    width: 85px;
    margin-bottom: 30px;
    margin-right:10px;
    border: 1px solid black;
    box-shadow: none;
  }
  .gender_select {
    height: 1.1cm;
    border-style: groove;
    width: 308px;
    margin-bottom: 30px;
    border: 1px solid black;
    box-shadow: none;
  }
  .search_certification{
    border-style: groove;
    height: 0.7cm;
    width: 90px;
    margin-left: 2px;
    color: white;
    background-color: #adc9ff;
    font-size: 11px;
    }
  .register_final{
    border-style: groove;
    height: 1.1cm;
    width: 300px;
    color: white;
    background-color: #adc9ff;
    font-size: 16px;
    margin-bottom: 5px;
  }
  .register_bottom {
    border-style: groove;
    border-radius: 50px;
    margin-top: 5px;
    height: 0.5cm;
    border: 0;
    outline: 0;
    background-color: #f6f6f8;
    font-size: 13px;
    font-family: "ng", 'BMJUA_ttf';
  }
  .register{
    font-family: "ng", 'BMJUA_ttf';
  }
  .login {
    margin-left: 16px;
    margin-right: 16px;
    font-family: "ng", 'BMJUA_ttf';
  }
  .shadow {
    box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03)
  }
  label {
    text-align: left;
  }
  @font-face {
    font-family: "ng";
    src: url(./BMJUA_ttf.ttf);
  }
  h1 {
    font-family: "ng", 'BMJUA_ttf';
  }
</style>