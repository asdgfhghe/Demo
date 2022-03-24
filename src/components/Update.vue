<template>
    <div class="w">

        <header>
            <div class="logo">
                    <img src="./../../static/imges/logo.png" alt="" @click="return_home()">
            </div>
        </header>
        <div class="registerarea">
            <h3>
                更改密码
                <div class="register">返回 <router-link :to="{name:'Home'}">主页</router-link></div>
            </h3>
            <div class="reg_form">
                <form action="">
                    <ul>
                        <li>
                            <label for="">原密码:</label>
                            <input type="text" class="inp" v-model="old_password" @blur="old_password_check(old_password)">
                            <span class="">
                                <i class=""></i>{{old_password_msg}}
                            </span>
                        </li>
                        <li>
                            <label for="">新密码:</label>
                            <input type="password" class="inp" v-model="new_password" @blur="new_password_check(new_password)">
                            <i class="iconfont" @click="icon_change()">&#xe6ad;</i>
                            <span class="">
                                <i class=""></i>{{new_password_msg}}
                            </span>
                        </li>
                        <li class="safe">安全程度<em>{{safe_msg}}</em>
                        </li>
                        <li>
                            <label for="">确认密码:</label>
                            <input type="text" class="inp" v-model="new_rpassword" @blur="new_rpassword_check(new_password,new_rpassword)">
                            <span class="">
                                <i class=""></i>{{new_rpassword_msg}}
                            </span>
                        </li>
                        <li><input type="button" value="更改" class="btn" @click="update()"></li>
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

export default ({
    name:"Update",
    data(){
        return{
            index:"",

            old_password:"",
            new_password:"",
            new_rpassword:"",

            old_password_msg:"",
            new_password_msg:"",
            new_rpassword_msg:"",
            safe_msg:"",
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
        
        safe_check: function(password){

            let num=0;
            if (password.length > 8) {
                num++;
            }
            if (password.length > 14) {
                num++;
            }
            if (/\d/.test(password)) {//如果用户输入的密码 包含了数字
                num++;
            }
            if (/[a-z]/.test(password)) {//如果用户输入的密码 包含了小写的a到z
                num++;
            }
            if (/[A-Z]/.test(password)) {//如果用户输入的密码 包含了大写的A到Z
                num++;
            }
            if (/\W/.test(password)) {//如果是非数字 字母 下划线
                num++;
            }

            //判断密码强度
            let em=document.querySelector(".reg_form .safe em");
            let flag=0;  //密码不需要重新输入
            if(num<3) //弱
            {
                this.safe_msg="弱";
                em.className="ruo";
                flag=1;

            }
            else if(num<5) //中
            {
                this.safe_msg="中";
                em.className="zhong";
            }
            else //强
            {
                this.safe_msg="强";
                em.className="qiang";
            }
            return flag;

        },
        new_password_check: function(new_password){
            //无输入判定
            if(new_password=="")
            {
                return false;
            }
            else if(new_password==this.old_password)
            {
                alert("新密码不能与原密码一致");
                return false;
            }
            let span=document.querySelectorAll('.reg_form span')[1];//选区第三个span标签即对应密码


            let flag=this.safe_check(new_password);//密码不需要重新输入

            if(flag)
            {
                this.new_password_msg="密码过于简单,请重新输入";
                span.className='error';
                span.children[0].className='error_icon';
                return false;
            }else{
                this.new_password_msg="密码符合条件";
                span.className='success';
                span.children[0].className='success_icon';
                return true;
            }
        },
        old_password_check: function(old_password){
            //无输入判定
            if(old_password=="")
            {
                return false;
            }

            for(let i=0;i<localStorage.num;i++)
            {
                let name=JSON.parse(localStorage[i]).name;
                let password=JSON.parse(localStorage[i]).password;

                if(name==localStorage.getItem("name"))
                {
                    if(old_password==password)
                    {
                        this.index=i;
                        return true;
                    }
                    alert("原密码输入错误");
                    return false;
                }  
            }
            return false;
        },
        new_rpassword_check:function(new_password,new_rpassword){
            //无输入判定
            if(new_rpassword=="")
            {
                return false;
            }

            let span=document.querySelectorAll('.reg_form span')[2];//选区第三个span标签即对应审核密码


            if(new_password != new_rpassword)
            {
                this.new_rpassword_msg="两次输入的密码不一致，请重新输入";
                span.className='error';
                span.children[0].className='error_icon';
                return false;

            }else{
                this.new_rpassword_msg="两次输入密码一致";
                span.className='success';
                span.children[0].className='success_icon';
                return true;
            }
        },
        update(){
            console.log(this.new_password_check(this.new_password));
            console.log(this.new_rpassword_check(this.new_password,this.new_rpassword));
            console.log(this.old_password_check(this.old_password));
            if(this.new_password_check(this.new_password)&&this.new_rpassword_check(this.new_password,this.new_rpassword)&&this.old_password_check(this.old_password)){
                let user={};
                user.name=JSON.parse(localStorage[this.index]).name;
                user.phone=JSON.parse(localStorage[this.index]).phone;
                user.password=this.new_password;
                console.log(user);
                localStorage.setItem(this.index,JSON.stringify(user));
                alert("密码修改成功");
                this.$router.push('/');
            }
        },

    },
})
</script>
<style scoped>
@import './../../static/css/update.css';
</style>