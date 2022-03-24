<template>
    <div class="w">

        <header>
            <div class="logo">
                    <img src="./../../static/imges/logo.png" alt="" @click="return_home()">
            </div>
        </header>
        <div class="registerarea">
            <h3>
                注册新用户
                <div class="login">我有账号，去<router-link :to="{name:'Login'}">登录</router-link></div>
            </h3>
            <div class="reg_form">
                <form action="">
                    <ul>
                        <li>
                            <label for="">手机号:</label>
                            <input type="text" class="inp" v-model="phone" @blur="phone_check(phone)">
                            <span class="" >
                                <i class=""></i>{{phone_msg}}
                            </span>
                        </li>
                        <li>
                            <label for="">用户名:</label>
                            <input type="text" class="inp" v-model="name" @blur="name_check(name)">
                            <span class="">
                                <i class=""></i>{{name_msg}}
                            </span>
                        </li>
                        <li>
                            <label for="">登录密码:</label>
                            <input type="password" class="inp" v-model="password" @blur="password_check(password)">
                            <i class="iconfont" @click="icon_change()">&#xe6ad;</i>
                            <span class="">
                                <i class=""></i>{{password_msg}}
                            </span>
                        </li>
                        <li class="safe">安全程度<em>{{safe_msg}}</em>
                        
                        <li>
                            <label for="">验证密码:</label>
                            <input type="password" class="inp" v-model="rpassword" @blur="rpassword_check(password,rpassword)">
                            <span class="">
                                <i class=""></i>{{rpassword_msg}}
                            </span>
                        </li>
                        <li class="agree"><input type="checkbox" name="" id="" v-model="agree">
                            同意协议并注册<a href="javascript:;">《同意用户协议》</a>
                        </li>
                        <li><input type="button" value="完成注册" class="btn" @click="register()"></li>
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
    name: 'Register',
    data(){
        return{
            user:{},
            phone:"",
            name:"",
            password:"",
            rpassword:"",
            agree:"",

            phone_msg:"",
            name_msg:"",
            password_msg:"",
            rpassword_msg:"",

            icon:false,
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
            let input=document.querySelectorAll('.reg_form input')[2];//密码标签 
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
        
        phone_check: function(phone){
            //无输入判定
            if(phone=="")
            {
                return false;
            }

	        let myreg = /^[1][3,4,5,7,8,9][0-9]{9}$/;

                let span=document.querySelectorAll('.reg_form span')[0];//选区第一个span标签即对应手机号

            if (!myreg.test(phone)) {

		        this.phone_msg='手机号格式不正确，请重新输入';
                span.className='error';
                span.children[0].className='error_icon';
	            return false;

	        }else{

		        this.phone_msg='手机号格式正确';
                span.className='success';
                span.children[0].className='success_icon';
	            return true;
	        }
        },
        name_check: function(name){

            //无输入判定
            if(name=="")
            {
                return false;
            }

            let span=document.querySelectorAll('.reg_form span')[1];//选区第二个span标签即对应用户名

            let flag=false;//判断是否有重复昵称
            for(let i=0;i<localStorage.num;i++)//遍历已注册的用户列表
            {
                let name_contrast=JSON.parse(localStorage[i]).name;

                if(name==name_contrast)
                {
                    flag=true;
                    break;
                }
            }
            if(flag)
            {
                this.name_msg="用户名已被占用";
                span.className='error';
                span.children[0].className='error_icon';
                return false;
            }else{
                this.name_msg="用户名未被占用";
                span.className='success';
                span.children[0].className='success_icon';
                return true;
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
        password_check: function(password)
        {

            //无输入判定
            if(password=="")
            {
                return false;
            }

            let span=document.querySelectorAll('.reg_form span')[2];//选区第三个span标签即对应密码


            let flag=this.safe_check(password);//密码不需要重新输入
            if(flag)
            {
                this.password_msg="密码过于简单,请重新输入";
                span.className='error';
                span.children[0].className='error_icon';
                return false;
            }else{
                this.password_msg="密码符合条件";
                span.className='success';
                span.children[0].className='success_icon';
                return true;
            }

        },
        rpassword_check(password,rpassword){

            //无输入判定
            if(rpassword=="")
            {
                return false;
            }

            let span=document.querySelectorAll('.reg_form span')[3];//选区第三个span标签即对应审核密码


            if(password != rpassword)
            {
                this.rpassword_msg="两次输入的密码不一致，请重新输入";
                span.className='error';
                span.children[0].className='error_icon';
                return false;

            }else{
                this.rpassword_msg="两次输入密码一致";
                span.className='success';
                span.children[0].className='success_icon';
                return true;
            }
        },
        agree_check: function(agree)
        {
            if(agree==false)
            {
                alert("请勾选同意协议并注册");
                return false;
            }
            return true;
        },

        register(){
            // console.log(this.phone);
            // console.log(this.agree);
            // console.log(this.password);
            
            if(this.phone_check(this.phone)&&this.password_check(this.password)
            &&this.rpassword_check(this.password,this.rpassword)&&this.agree_check(this.agree))
            {
                console.log("可以注册了");
                this.user.name=this.name;
                this.user.phone=this.phone;
                this.user.password=this.password;

            //发送axios请求
            this.$http.post("http://rap2api.taobao.org/app/mock/299174/users/add",this.user).then(res=>{
                    // console.log(res.data);
                    
                    if(res.data.success){
                        alert("注册成功");
                        
                        let index=localStorage.getItem('num');
                        localStorage.setItem(index,JSON.stringify(this.user));
                        localStorage.setItem('num',parseInt(index)+1);

                        // console.log(localStorage.valueOf());//查看localStorage
                        console.log(JSON.parse(localStorage[index]));//输入当前添加的用户信息

                        let url="/";
                        // +"?name="+this.name+"&phone="+this.phone;

                        localStorage.setItem("name",this.name);
                        localStorage.setItem("phone",this.phone);
                        localStorage.setItem("password",this.password);
                        localStorage.setItem("login",1);
                        console.log(localStorage);
                        this.$router.push(url);
                    }
            });
            }else{
                console.log("还不能注册");
            }
        },
            
    },
    // watch: {
    //     phone: function(newVal, oldVal) {
    //         // TO DO
    //         console.log("newVal:", newVal);
    //         console.log("oldVal:", oldVal);
    //     }
    // },

})
</script>
<style scoped>

@import './../../static/css/register.css';
</style>