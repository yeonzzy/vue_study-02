<template>
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="useName">id: </label>
      <input type="text" name="" id="userName" v-model="userName">
    </div>
    <div>
      <label for="password">pw: </label>
      <input type="password" name="" id="password" v-model="password">
    </div>
    <button type="submit">login</button>
  </form>
</template>

<script>
// npm install axios 명령어를 통해 설치.
import axios from 'axios';

  export default {
    data: function(){
      return {
        userName: '',
        password: '',
      }
    },
    methods: {
      // login시 새로고침을 막는 법
                  //submit 이벤트를 인자로 받음. function(event)
      submitForm: function() {
        // event.preventDefault();
        // vue에서는 v-on:submit.prevent로 대체가능
        console.log(this.userName, this.password);
        // axios : http 프로토콜을 이용한 통신라이브러리
        // 브라우저와 서버간 데이터를 주고받는 라이브러리
        // post : 데이터 생성 및 조작, http 메소드
        var url = 'https://jsonplaceholder.typicode.com/users';
        var data = {
          userName: this.userName,
          password: this.password
        }
        axios.post(url, data)
        // 데이터가 정상적으로 넘어갈 때 (성공)
        .then(function(response){
          console.log(response);
        })
        // 데이터가 넘어가지 않을 때 (실패)
        .catch(function(error){
          console.log(error);
        })
      }
    }
  }
</script>

<style>

</style>