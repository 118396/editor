<template>
    <div id="topbar">
        <div class="logo">
            VueResume
        </div>
        <div class="actions">
            <el-button type="primary" @click="register">注册</el-button>
            <el-button @click="login">登录</el-button>
            <el-button v-on:click="preview">预览</el-button>
        </div>
    </div>
</template>



<script>
export default {
    methods:{
        preview(){
            this.$emit('preview')
        },
        login(){
            this.$router.push({name:"login"})
        },
        register(){
            this.$router.push({name:'register'})
        }

    }
}
</script>
<style lang= "less" scope>
#topbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 16px;
    font-size: 20px;
}
</style>

