<template>
<div class="reg-login-box">
  <h2>{{title}}</h2>
  <div class="form-wrap">
    <form action="" method="post" :id="formid">
      <div class="user-input-box">
        <input type="text" name="userName" placeholder="用户名" v-model="userName"/>
        <input type="password" name="password" placeholder="密码" v-model="password"/>
        <input type="password" name="comfimePassword" placeholder="确认密码" v-if="showComfimeInput" v-model="confirmPsd">
      </div>
      <div class="option-toggle">
        <!-- 注册 -->
        <p v-if="showComfimeInput">
          <span>已有账号，<a href="javascript:void(0)" v-on:click="fnLogToggleReg">立即登录</a></span>
        </p>
        <!-- 登录 -->
        <p v-else>
          <input type="checkbox" name="autoLogin" v-model="checked"/>
          <label for="autoLog">下次自动登录</label>
          <span><a href="javascript:void(0)" v-on:click="fnLogToggleReg">立即注册</a></span>
        </p>
      </div>
      <p class="error-tips">{{errorMsg}}</p>
      <input type="submit" name="submit" :value="submitText" :class="submitColor">
    </form>
  </div>
</div>
</template>

<script>
export default {
  name: 'reglogin',
  data () {
    return {
      title: '用户登录',
      formid: 'loginForm',
      showComfimeInput: false,
      errorMsg: '',
      submitText: '立即登录',
      submitColor: {
        isUse: false,
        class: 'blue-btn'
      },
      userName: '',
      password: '',
      confirmPsd: '',
      checked: true
    }
  },
  watch: {
    userName (cur, old) {
      if (cur.length === '0') this.errorMsg = '请输入用户名'
    }
  },
  methods: {
    fnLogToggleReg () {
      this.title = this.title === '用户登录' ? '用户注册' : '用户登录'
      this.formid = this.formid === 'loginForm' ? 'regForm' : 'loginForm'
      this.showComfimeInput = !this.showComfimeInput
      this.submitText = this.submitText === '立即登录' ? '立即注册' : '立即登录'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.background-img {
  position: absolute;
  z-index: -1;
}
.reg-login-box {
  width: 400px;
  height: 410px;
  background-color: #fff;
  border-radius: 10px;
  position: absolute;
  top: 50%;
  left: 50%;
  margin-top: -205px;
  margin-left: -200px;
  text-align: center;
  border: 1px solid #fff;
}
.reg-login-box h2{
font-size: 20px;text-align: center; margin-bottom :24px; margin-top :30px; font-weight :400;
}
.reg-login-box .user-input-box input{
  width: 342px;line-height: 56px;border:none;border-bottom: 1px solid #d7d7d7;outline: none;
  	text-indent: 27px;text-align: left;
}
.user-input-box input:focus{
  border-bottom: 1px solid #167dcc;color:#515151;
}

input[name=userName]{
  background :url(./happyuser.png) no-repeat;background-position: 0 15px;
}
input[name=userName]:focus{
  background-position: 0 -45px;
}
input[type=password]{
  background :url(./happyuser.png) no-repeat;background-position: 0 -96px;
}
input[type=password]:focus{
  background-position: 0 -148px
}

.reg-login-box .option-toggle p{
  color: #999;overflow: hidden;font-size: 12px;width: 342px;margin: auto;margin-top: 15px;text-align: left;
}

.reg-login-box .option-toggle p span{
  float:right;
}
.reg-login-box .option-toggle p a{
  text-decoration: none;
  color: #167dcc;
}

.reg-login-box .error-tips{
  color:#ee5c5d; font-size :12px; margin-top :15px;
}
.reg-login-box [type=submit]{
    box-shadow: 0px 0px 2px 2px #e8e8e8 ;
    color: #fff;line-height:46px;border-radius: 23px;font-size:
   15px;border:none;width: 280px;text-align: center;
  	display: block;
  	position: absolute;bottom: 40px;left: 60px;cursor: pointer;outline: none;
}
.blue-btn{
  background-color: #2b85d3;
  box-shadow: 0px 0px 2px 2px #b2eeff ;
}


</style>
