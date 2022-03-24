<template>
    <div class="w">

        <header>
            <div class="logo">
                    <img src="./../../static/imges/logo.png" alt="" @click="return_home()">
            </div>
        </header>
        <div class="registerarea">
            <h3>
                用户登录
                <div class="register">没有账号，去<router-link :to="{name:'Register'}">注册</router-link></div>
            </h3>
            <div class="reg_form">
                <form action="">
                    <ul>
                        <li>
                            <label for="">手机号/用户名:</label>
                            <input type="text" class="inp" v-model="phone_name">
                        </li>
                        <li>
                            <label for="">登录密码:</label>
                            <input type="password" class="inp" v-model="password">
                            <i class="iconfont" @click="icon_change()">&#xe6ad;</i>
                        </li>
                        <a href="javascript:;" class="lost">忘记密码？</a>
                        <li><input type="button" value="登录" class="btn" @click="login()"></li>
                    </ul>
                </form>
            </div>
        </div>
        <footer>
            <div class="mod_copyright">
                <div class="links">
                    <a href="#">关于我们</a> | <a href="#">联系我们</a> |<a href="#">联系客服</a> |
                    <a href="#">商家入驻</a> | <a href="#">营销中心</a> | <a href="#">手机品优购</a> |
                    <a href="#">友情链接</a> | <a href="#">销售联盟</a> | <a href="#">品优购社区</a> |
                    <a href="#">品优购公益</a> | <a href="#">English Site</a> | <a href="#">Contact U</a>
                </div>
                <div class="copyright">
                    地址: 北京市昌平区建材城西路金燕龙办公室一层 邮编100096 电话:
                    400-618-4000 传真 :010-829365100 邮箱: sgfgdsfgfd.cn<br>
                    京ICP备08001421号京公安备24356657657
                </div>
            </div>
        </footer>
    </div>
</template>

<script>
export default {
    name:'Login',
    data(){
        return{
            icon:'',
            password:'',
            phone_name:"",
            name:"",
            phone:"",

        }
    },
    methods:{

        return_home: function(){
            let flag=confirm("您所做的操作未保存，是否确定返回主页");
            if(flag==true)
            {
                this.$router.push('/');
            }     
        },

         icon_change: function(){
            let input=document.querySelectorAll('.reg_form input')[1];//密码标签 
            let li=document.querySelector('.reg_form .iconfont');//眼睛所在的li标签 

            if(!this.icon)
            {
                li.innerHTML="&#xe621;";
                input.type="text";
                this.icon=true;
            }else{
                li.innerHTML="&#xe6ad;"
                input.type="password";
                this.icon=false;
            }
        },

        judge: function(){ //判断用户名和密码是否匹配

            // console.log(localStorage.valueOf());//查看localStorage

            for(let i=0;i<localStorage.num;i++)
            {
                let name=JSON.parse(localStorage[i]).name;
                let phone=JSON.parse(localStorage[i]).phone;
                let password=JSON.parse(localStorage[i]).password;

                if(name==this.phone_name || phone==this.phone_name)
                {
                    if(this.password==password)
                    {
                        this.name=name;
                        this.phone=phone;
                        return true;
                    }
                    alert("用户名密码不匹配");
                    return false;
                }
            }
            alert("无此用户");
            return false;
        },
        login(){
            if(this.judge())//用户密码匹配正确
            {
                let url="/";
                // +"?name="+this.name+"&phone="+this.phone;

                localStorage.setItem("name",this.name);
                localStorage.setItem("phone",this.phone);
                localStorage.setItem("password",this.password);
                localStorage.setItem("login",1);
                console.log(localStorage);
                this.$router.push(url);
            }
        },
    },
    mounted(){
        // console.log(localStorage);
    }
}
</script>

<style scoped>
@import './../../static/css/login.css';
</style>