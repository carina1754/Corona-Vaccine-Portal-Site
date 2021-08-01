<template>
  <form v-on:submit.prevent="submitForm">
    <div style="padding-top:2%;">
      <h1 class="register_title">COFO</h1>
      <lable for="username"> </lable>
      <div style="margin-right:265px; margin-bottom:5px; padding:0px; font-size:14px;">아이디</div>
      <div><input class="register_textinput" id="username" type="text" v-model="username"></div>
      <lable for="password1"> </lable>
      <div style="margin-right:250px; margin-bottom:5px; padding:0px; font-size:14px;">비밀번호</div>
      <div><input class="register_textinput" id="password1" type="password1" v-model="password1"></div>
      <lable for="password2"> </lable>
      <div style="margin-right:200px; margin-bottom:5px; padding:0px; font-size:14px;">비밀번호 재확인</div>
      <div><input class="register_textinput" id="password2" type="password2" v-model="password2"></div>
      <lable for="name"> </lable>
      <div style="margin-right:275px; margin-bottom:5px; padding:0px; font-size:14px;">이름</div>
      <div><input class="register_textinput" id="name" type="name" v-model="name"></div>
      <div style="margin-right:250px; margin-bottom:5px; padding:0px; font-size:14px;">생년월일</div>
      <div style="margin-left:9px;">
        <input class="birth_textinput" id="year" type="year" v-model="year" style="width:95px; margin-right:10px;" placeholder="년(4자)">
        <select class="month_select" v-model="selected">
            <option disabled value="">월</option>
            <option>1</option>
            <option>2</option>
            <option>3</option>
            <option>4</option>
            <option>5</option>
            <option>6</option>
            <option>7</option>
            <option>8</option>
            <option>9</option>
            <option>10</option>
            <option>11</option>
            <option>12</option>
        </select>
        <input class="birth_textinput" id="year" type="year" v-model="year" style="width:95px; margin-right:10px;" placeholder="일">
      </div>
      <div style="margin-right:280px; margin-bottom:5px; padding:0px; font-size:14px;">성별</div>
      <div>
      <select class="gender_select" v-model="selected">
            <option disabled value="">성별</option>
            <option>남</option>
            <option>여</option>
            <option>선택안함</option>
        </select>
      </div>  
      <lable for="email"> </lable>
      <div style="margin-right:160px; margin-bottom:5px; padding:0px; font-size:14px;">본인 확인 이메일(선택)</div>
      <div><input class="register_textinput" id="email" type="email" v-model="email" placeholder="선택입력"></div>
      <div style="margin-right:250px; margin-bottom:5px; padding:0px; font-size:14px;">휴대전화</div>
      <div>
        <input class="phone_textinput" id="email" type="email" v-model="email" placeholder="전화번호 입력">
        <button class="phone_certification" type="phone_certification" v-on:submit.prevent="submitForm">인증번호 받기</button>
      </div>
      <div><input class="register_textinput" id="email" type="email" v-model="email" placeholder="인증번호를 입력하세요"></div>
      <button class="register_final" type="register" v-on:submit.prevent="submitForm">가입하기</button>
      <div>
      <button class="register_bottom" type="register" v-on:submit.prevent="submitForm">이용약관</button>
      │
      <button class="register_bottom" type="register" v-on:submit.prevent="submitForm">개인정보처리방침</button>
      │
      <button class="register_bottom" type="register" v-on:submit.prevent="submitForm">책임의 한계와 법적고지</button>
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

  .register_textinput {
    height: 1cm;
    border-style: groove;
    width: 300px;
    margin-bottom: 30px;
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

  .phone_certification{
    border-style: groove;
    height: 1.1cm;
    width: 90px;
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