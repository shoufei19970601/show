<template>
    <div class="body">
      <mt-swipe :show-indicators="false">
    <mt-swipe-item v-for="item in lunbotuList" :key="item.url">
        <img src="item.imag" alt="" >

    </mt-swipe-item>
    </mt-swipe>

     <ul class="mui-table-view mui-grid-view mui-grid-9">
		            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		                    <img src="/src/images/menu1.png" alt="">
		                    <div class="mui-media-body">新闻资讯</div></a></li>
		            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		                    <img src="/src/images/menu2.png" alt="">
		                    <div class="mui-media-body">图片分享</div></a></li>
		            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		                    <img src="/src/images/menu3.png" alt="">
		                    <div class="mui-media-body">商品购买</div></a></li>
		            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		                    <img src="/src/images/menu4.png" alt="">
		                    <div class="mui-media-body">留言反馈</div></a></li>
		            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		                   <img src="/src/images/menu5.png" alt="">
		                    <div class="mui-media-body">视频专区</div></a></li>
		            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		                   <img src="/src/images/menu6.png" alt="">
		                    <div class="mui-media-body">联系我们</div></a></li>
		        </ul> 
    </div>
</template>
<script>
import { Toast} from 'mint-ui'

    export default {
        data(){
            return{
               lunbotuList:[]
            };
        },
        created(){
            this.getLunbotu();
        },
        methods:{
            getLunbotu(){
                this.$http.get("http://www.xiaoyaoji.cn/test/image/test.jpg").then(result=>{
                    // console.log(result.body);
                    if(result.body.status ===0){
                        //成功
                        this.getLunbotu = result.body.message;
                    }else{
                        //失败
                        Toast("加载轮播图失败")
                    }
                })
            }
            }
    }

</script>

<style lang="less" scoped>
body{
    background-color: #fff;
}
.mint-swipe{
    height: 200px;

    .mint-swipe-item{
        &:nth-child(1){
            background-color: yellow;
        }
          &:nth-child(2){
            background-color: red;
        }
          &:nth-child(3){
            background-color: green;
        }
        img{
            width: 100%;
            height: 100%;
            background-color: aqua
        }
    }
}
.mui-grid-view.mui-grid-9{
    background-color: #fff;
    border:0;
    img{
        width: 60px;
    }

}
.mui-grid-view.mui-grid-9 .mui-table-view-cell{
    border:0;
}
.mui-media-body{
    font-size: 13px
}
</style>

