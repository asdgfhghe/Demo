<template>
    <div>
    <Header></Header>

    <!-- nav模块制作start -->
    <div class="nav">
        <div class="w">
            <div class="sk_list">
                <ul>
                    <li><a href="#">品优秒杀</a></li>
                    <li><a href="#">即将售罄</a></li>
                    <li><a href="#">超值低价</a></li>
                </ul>
            </div>
            <div class="sk_con">
                <ul>
                    <li><a href="#">女装</a></li>
                    <li><a href="#" class="style_red">女鞋</a></li>
                    <li><a href="#">男装</a></li>
                    <li><a href="#">男鞋</a></li>
                    <li><a href="#">母婴童装</a></li>
                    <li><a href="#">食品</a></li>
                    <li><a href="#">智能数码</a></li>
                    <li><a href="#">运动户外</a></li>
                    <li><a href="#">更多分类</a></li>
                </ul>
            </div>
        </div>
    </div>
    <!-- nav模块制作end -->
    <!-- 列表页主体部分 -->
    <div class="w sk_container">
        <div class="sk_hd">
            <img src="./../../static/imges/nx.jpg" alt="" >
        </div>
        <div class="sk_bd">
            <ul class="clearfix">
                <li>
                    <img src="./../../static/imges/phone.png" alt="" >
                </li>
                <li>
                    <img src="./../../static/imges/phone.png" alt="" >
                </li>
                <li>
                    <img src="./../../static/imges/phone.png" alt="" >
                </li>
                <li>
                    <img src="./../../static/imges/phone.png" alt="" >
                </li>
                <li>
                    <img src="./../../static/imges/phone.png" alt="" >
                </li>
                <li>
                    <img src="./../../static/imges/phone.png" alt="" >
                </li>
                <li>
                    <img src="./../../static/imges/phone.png" alt="" >
                </li>
                <li>
                    <img src="./../../static/imges/phone.png" alt="" >
                </li>
            </ul>
        </div>
    </div>
   
    <Footer></Footer>
    </div>
</template>
<script>
import Footer from './Footer.vue';
import Header from './Header.vue';
export default ({
    name:'List',
    data(){
        return{}
    },
    components: {Footer,Header},
})
</script>
<style scoped>

@import './../../static/css/list.css';
@import './../../static/css/common.css';
</style>