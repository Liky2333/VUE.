<template>
    <div >登陆界面</div>
    <div>
        <label>用户</label>
        <Input v-model="user" ></Input>
        <br>
        <label>密码</label>
        <Input v-model="pass"></Input>


        <hr>
        <h3>路由参参方法一 路由的查询  (path +query)</h3>
        <p>
            {{$route.query}}
        </p>

        <h3>路由参参方法二 路由的参数 (name + params)</h3>
        <p>
            {{$route.params}}
        </p>
    </div>
</template>

<script>
export default{
    data(){
        return {
            user:"",
            pass:""
        }
    }
}
</script>

<style lang="scss">
    
</style>