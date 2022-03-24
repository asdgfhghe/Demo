<template>
    <div>
         <!-- 快捷导航模块 start-->
    <section class="shortcut">
        <div class="w">
            <div class="fl">
                <ul>
                    <li>品优购欢迎您！&nbsp;</li>
                    <li>{{name}}</li>
                    <li>
                        <a href="#/login">请登录</a> &nbsp;<a href="#/register" class="style_red">免费注册</a>
                    </li>
                </ul>
            </div>
            <div class="fr">
                <ul>
                    <li><a href="javascript:;">我的订单</a></li>
                    <li></li>
                    <li><a href="javascript:;">我的品优购</a></li>
                    <li></li>
                    <li><a href="javascript:;">品优购会员</a></li>
                    <li></li>
                    <li><a href="javascript:;">企业采购</a></li>
                    <li></li>
                    <li class="arrow-icon"><a href="javascript:;">关注品优购</a></li>
                    <li></li>
                    <li class="arrow-icon"><a href="javascript:;">客户服务</a></li>
                    <li></li>
                    <li class="arrow-icon"><a href="javascript:;">网站导航</a></li>
                </ul>
            </div>
        </div>
    </section>
    <!-- 快捷导航模块 end-->

    <!-- header头部模块制作 start -->
    <header class="header w">
        <!-- logo模块 -->
        <div class="logo">
            <h1>
                <a href="#/">品优购商城</a>
            </h1>
        </div>
        <!-- search搜索模块 -->
        <div class="search">
            <input type="search" name="" id="" placeholder="办公用品">
            <button>搜索</button>
        </div>
        <div class="hotwords">
            <a href="javascript:;" class="style_red">优惠购首发</a>
            <a href="javascript:;">亿元优惠</a>
            <a href="javascript:;">9.9元团购</a>
            <a href="javascript:;">每满99减30</a>
            <a href="javascript:;">办公用品</a>
            <a href="javascript:;">电脑</a>
            <a href="javascript:;">通信</a>
        </div>
        <!-- 购物车模块
        <div class="shopcar">
            我的购物车
            <i class="count">8</i>
        </div> -->
        <!-- 用户头像模块 -->
        <span class="user">
            <img  src="../../static/imges/user_img.jpg" class="picture">
            <li>{{name}}</li>
            <div class="userlist">
                <div class="empty"></div>
                <li>更换头像</li>
                <li @click="goto_update()">更改密码</li>
                <li>购物车</li>
                <li @click="login_out()">退出登录</li>
            </div>
        </span>

    </header>
    <!-- header头部模块制作 end -->
    </div>
</template>
<script>

export default ({
    name: "Header",
    data(){
        return{
            name:"",
            phone:"",
            password:"",
        }
    },
    methods:{
    //     judge_login:function(){//测试从网页链接中获取登录的用户信息
    //             let data = {};
    //             let src = window.location.href;//获取当前的网址链接

    //             if(src.indexOf("?") == -1)//没有登录
    //             {
    //                 return false;
    //             }

    //             let dataStr = src.substring(src.lastIndexOf("?") + 1);//取出最后一个问号到结束的字符串
    //             let dataArray = dataStr.split("&"); //根据"&"分割不同键值对

    //             for (let i = 0; i < dataArray.length; i++) {//遍历所有键值对
    //                 let param = dataArray[i].split("=");//根据"="分割键和值加入到data对象
    //                 data[param[0]] = param[1];
    //             }
    //             this.name=data['name'];
    //             this.phone=data['phone'];
    //             console.log(this.name,this.phone);

    //             return true;
    //   },
      goto_update(){
          this.$router.push('/update');
      },
      login_out(){   
          let li = document.querySelectorAll(".shortcut .fl li"); 
          let div = document.querySelector(".user");

          li[1].style.display='none';
          li[2].style.display='block';
           div.style.display="none";

          localStorage.setItem("name","");
          localStorage.setItem("phone","");
          localStorage.setItem("password","");
          localStorage.setItem("login",'0');
          
        // console.log(localStorage);
      },
      login_in(){   
          let li = document.querySelectorAll(".shortcut .fl li"); 
          let div = document.querySelector(".user");

          li[1].style.display='block';
          li[2].style.display='none';
          div.style.display="block";
          
          this.name=localStorage.getItem("name");
          this.phone=localStorage.getItem("phone");
          this.password=localStorage.getItem("password");
      },
    },
    created(){
       console.log(localStorage);
    },
    mounted(){
        let temp = localStorage.getItem("num");
        if(temp=='null'||temp=='NaN'||temp==null)
        {
            localStorage.setItem('num',0);
        }
        if(localStorage.getItem('login')=='1')//已经登录
        {
            this.login_in();
            console.log("已登录");
            //在已经登录后选出请登录 免费注册的li，设置为隐藏，并将login的用户的设置为可见
            //将原来的login设置为不可见
        }
        else{
            this.login_out();
            console.log("未登录");
        }
    },
})
</script>
<style scoped>
@import './../../static/css/common.css';
</style>