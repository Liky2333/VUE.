<template>
<div>
    <div></div>
    <div>
        <div v-for="mv in movise" :key="mv.id">
            <card :name="mv.name" :len="mv.len" :type="mv.type" :url="mv.url"></card>
        </div>
    </div>
</div>
</template>

<script>
import img from "../assets/img/01.jpg"
import card from "../components/card.vue"
export default {
    components:{
        card,
    },
    data(){
        return{
            movise:[
                {id:1,type:"混剪",len:'03`14"',name:"电影慢镜头混剪[看见镜头的美]",url:img},
                {id:2,type:"混剪",len:'03`14"',name:"电影慢镜头混剪[看见镜头的美]",url:img},
                {id:3,type:"混剪",len:'03`14"',name:"电影慢镜头混剪[看见镜头的美]",url:img},
                {id:4,type:"混剪",len:'03`14"',name:"电影慢镜头混剪[看见镜头的美]",url:img},
                {id:5,type:"混剪",len:'03`14"',name:"电影慢镜头混剪[看见镜头的美]",url:img},
                {id:6,type:"混剪",len:'03`14"',name:"电影慢镜头混剪[看见镜头的美]",url:img},
            ],
            pageIndex:1,
            pageSize:10,
            totalcount:100,
        }
    },
    methods:{
        loadmore(pageIndex){
            console.log("加载更多。",  pageIndex);
            this.pageIndex = pageIndex

            let newData = [
                {id:1, type:"混剪"+pageIndex, len: `03'14"`, name:"电影慢镜头混剪【看见镜头的美】", url: img},
                {id:2, type:"混剪"+pageIndex, len: `03'14"`, name:"电影慢镜头混剪【看见镜头的美】", url: img},
                {id:3, type:"混剪"+pageIndex, len: `03'14"`, name:"电影慢镜头混剪【看见镜头的美】", url: img},
                {id:4, type:"混剪"+pageIndex, len: `03'14"`, name:"电影慢镜头混剪【看见镜头的美】", url: img},
                {id:5, type:"混剪"+pageIndex, len: `03'14"`, name:"电影慢镜头混剪【看见镜头的美】", url: img},

            ]
            this.movies = this.movies.concat(newData)
        },
        refresh(){
            console.log("下拉刷新")
        }
    }
}
</script>


<style lang="scss">

</style>