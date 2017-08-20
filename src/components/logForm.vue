<template>
	  <div class="login-form">
    <div class="g-form">
      <div class="g-form-line">
        <span class="g-form-label">用户名：</span>
        <div class="g-form-input">
          <input type="text" 
          v-model="usernameModel" placeholder="请输入用户名">
        </div>
        <span class="g-form-error">{{ userErrors.errorText }}</span>
      </div>
      <div class="g-form-line">
        <span class="g-form-label">密码：</span>
        <div class="g-form-input">
          <input type="password" 
          v-model="passwordModel" placeholder="请输入密码">
        </div>
        <!-- <span class="g-form-error">{{ passwordErrors.errorText }}</span> -->
      </div>
      <div class="g-form-line">
        <div class="g-form-btn">
          <a class="button" @click="onLogin">登录</a>
        </div>
      </div>
      <p>{{ errorText }}</p>
    </div>
  </div>
</template>
<script>
export default{
	props:{
		isShow:{
			type:Boolean,
			default:false
		}
	},
	data(){
		return{
      usernameModel:'',
      passwordModel:'',
      errorText:''
		}
	},
  computed:{
    userErrors(){
      let status,errorText
      if( !/@/g.test(this.usernameModel)){
         status = false
         errorText = '不包含@'
      }
      else{
        status = true
        errorText = ''
      }
      if(!this.userFlag){
        errorText = ''
        this.userFlag = true
      }
      return {status,errorText}
    },
    passwordErrors(){
      let errorText, status
      if (!/^\w{1,6}$/g.test(this.passwordModel)) {
        status = false
        errorText = '密码不是1-6位'
      }
      else {
        status = true
        errorText = ''
      }
      if (!this.passwordFlag) {
        errorText = ''
        this.passwordFlag = true
      }
      return {status,errorText}
    }
  },
	methods:{
  	onLogin(){
      if( !this.userErrors.status || !this.passwordErrors.status ){
        this.errorText = '验证不通过，请输入符合要求的登陆信息'
      }
      else{
        this.errorText = ''
        this.$http.post('api/login')
        .then((data)=>{
          console.log(data)
          this.$emit('has-login',data.data)
        },(err)=>{
          console.log(err)
        })
        //console.log('logining')
      }
    }
	}
}
</script>
<style scoped>

</style>