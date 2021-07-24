<template>
  <form v-on:submit.prevent="submitForm">
    <div style="padding-top:10%;">
      <h1 class="login_title">COFO</h1>
      <lable for="username"> </lable>
      <input class="textinput" id="username" type="text" v-model="username" placeholder="아이디를 입력하세요">
      <br>
      <lable for="password"> </lable>
      <input class="textinput" id="password" type="password" v-model="password" placeholder="비밀번호를 입력하세요">
      <br>
      <button type="submit" v-on:submit.prevent="submitForm" class="login"> 로그인</button>
      <button type="submit" class="login"> 회원가입</button>
      <button type="submit" class="login"> 계정 찾기</button>
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
  .login_title {
    color: #adc9ff;
    font-weight: 900;
    margin: 2.5rem 0 1.5rem;
    font-size: 100px;
    margin-bottom: 10px;
  }

  body {
    text-align: center;
    background-color: #F6F6F8;
  }

  .textinput {
    background: rgb(208, 241, 255);
    border-radius: 50px;
    height: 0.8cm;
    border-style: groove;
    width: 300px;
    margin-bottom: 12px;
    font-size: 13px;
    border: 0px;
    text-indent:15px;
  }

  button {
    border-style: groove;
    border-radius: 50px;
    margin-top: 5px;
    height: 0.5cm;
    border: 0;
    outline: 0;
    background-color: #f6f6f8;
    font-size: 19px;

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