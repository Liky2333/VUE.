<template>
    <div class="content">
        <div class="header">
            <img :src="imgUrl" />
        </div>
        <div>
            <h3> {{title}}</h3>
        </div>
        <div class="actions">
            <button @click="onLogOut">退出登陆</button>
            <button @click="onChangeLoginName">修改密码</button>
        </div>

    </div>
</template>

<script setup>
import { ref, onMounted} from "vue"


import { ToolsMounted }  from '../tools/index'

import img1 from "../assets/img/head.jpeg"

// vue-router 相关
import { useRouter, useRoute } from 'vue-router'
// useRouter  - >  this.$Router
const router = useRouter()
// useRoute    -> this.$route
const route = useRoute()

// 定义属性
const imgUrl = ref("")
const title = ref('')

// 定义方法
function onLogOut(){
    console.log("退出登陆")
    // 页面的跳转
    // this.$router.push({
    //     path: "/login"
    // })
    // 因为 this 指针不起作用。所以我们需要导入 vue-router 提供的函数接口

    router.push({
        path: '/login'
    })

}
function onChangeLoginName(){
    console.log("修改密码")
    // 与后台做交互 实现密码修改
    let newpass = prompt("请输入新密码" )
}

// 生命周期函数：
// onMounted(ToolsMounted)

onMounted(()=>{
    imgUrl.value = img1
    title.value = "如花"
})


</script>

<style lang="scss">

.content {
    margin-top: 50px;

    .header{
        padding: 20px;
        img{
            height: 400px;
            weight: 400px;
            border-radius: 50%;
        }
    }

    .actions {
        
        button {
            font-size: 30px;
            border: none;
            padding: 10px 20px;
            margin: 0 10px;
            border-radius: 30px;
            background-color: aquamarine;
        }
    }
}
</style>