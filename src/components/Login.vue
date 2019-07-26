<template>
  <div id="login">
    <div id="bigbox">
        <div id="header">
               Vue简历编辑器
        </div>
        <div id="main">
            <div>
                <span>用户名</span>
              <el-input v-model="input" placeholder="请输入用户名"></el-input>
            </div>
            <div>
                <span>密 码 </span>
                <el-input  style="margin-left:10px;" v-model="input1" placeholder="请输入用户密码"></el-input>
            </div>      
        </div>
        <div id="footer">
                <el-button type="primary" round  @click="register">注册</el-button>
                <el-button type="success" round @click="login">登录</el-button>
        </div>
    </div>
  </div>
</template>
<script>
export default {
    data() {
        return {
            input:'',
            input1: ''
        }
    },
  methods: {
    register() {
      this.$router.push({ name: "register" });
    },
    login() {
        alert("恭喜登录成功")
      this.$router.push({ name: "app" });
    }
  }
};
</script>
<style lang="less" scoped>
#login {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: white;
  z-index: 3;
  display: flex;
  justify-content: center;
  align-items: center;
}
#bigbox{
    // border:1px solid red;
    width: 40%;
    height: 50%;
    min-width: 537px;
    box-shadow: 0 0 15px gray;

}
#header{
    width: 100%;
    height: 30%;
    text-align: center;
    line-height: 98px;
    font-size: 24px;
    font-weight: bold;
    background:lightgray;
}
#main{
        width: 100%;
    height: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    div{
        width: 75%;
        margin-top: 6px;
    }
}

#footer{
        width: 100%;
        height: 20%;
        display: flex;
        justify-content: center;
        align-items: center;
}
</style>


