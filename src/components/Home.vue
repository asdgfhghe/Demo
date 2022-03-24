<template>
<div>
    <Header></Header>

    <!-- nav导航模块制作 start -->
    <nav class="nav">
        <div class="w">
            <div class="dropdown">
                <div class="dt">全部商品分类</div>
                <div class="dd">
                    <ul>
                        <li v-for="msg in dropdown" :key="msg"><router-link :to="{name:'List'}" target="_blank">{{msg}}</router-link></li>
                        <!-- <li><router-link :to="{name:'List'}" target="_blank">家用电器</router-link></li>
                        <li><router-link :to="{name:'List'}" target="_blank">手机、数码、通信</router-link></li>
                        <li><router-link :to="{name:'List'}" target="_blank">电脑、办公</router-link></li>
                        <li><router-link :to="{name:'List'}" target="_blank">家居、家具、家装、厨具</router-link></li>
                        <li><router-link :to="{name:'List'}" target="_blank">男装、女装、童装、内衣</router-link></li>
                        <li><router-link :to="{name:'List'}" target="_blank">个户化妆、清洁用品、宠物</router-link></li>
                        <li><router-link :to="{name:'List'}" target="_blank">鞋靴、箱包、珠宝、奢侈品</router-link></li>
                        <li><router-link :to="{name:'List'}" target="_blank">运动户外、钟表</router-link></li>
                        <li><router-link :to="{name:'List'}" target="_blank">汽车、汽车用品</router-link></li>
                        <li><router-link :to="{name:'List'}" target="_blank">母婴、玩具乐器</router-link></li>
                        <li><router-link :to="{name:'List'}" target="_blank">食品、酒类、生鲜、特产</router-link></li>
                        <li><router-link :to="{name:'List'}" target="_blank">医疗保健</router-link></li>
                        <li><router-link :to="{name:'List'}" target="_blank">图书、音像、电子书</router-link></li>
                        <li><router-link :to="{name:'List'}" target="_blank">彩票、旅行、充值、票务</router-link></li>
                        <li><router-link :to="{name:'List'}" target="_blank">理财、众筹、白条、保险</router-link></li> -->
                    </ul>
                </div>
            </div>
            <div class="navitems">
                <ul>
                    <li v-for="msg in navitems" :key="msg"><a href="javascript:;">{{msg}}</a></li>
                    <!-- <li><a href="javascript:;">服装城</a></li>
                    <li><a href="javascript:;">美妆馆</a></li>
                    <li><a href="javascript:;">传智超市</a></li>
                    <li><a href="javascript:;">全球购</a></li>
                    <li><a href="javascript:;">闪购</a></li>
                    <li><a href="javascript:;">团购</a></li>
                    <li><a href="javascript:;">拍卖</a></li>
                    <li><a href="javascript:;">有趣</a></li> -->
                </ul>
            </div>
        </div>
    </nav>
    <!-- nav导航模块制作 end -->

    <!-- 首页专有的模块 main start -->
    <div class="w">
        <div class="main">
            <div class="focus">
                <div class="scroll">
                    <img src="./../../static/imges/banner1.jpg" alt="" class="img current" >
                    <img src="./../../static/imges/banner2.jpg" alt="" class="img">
                    <img src="./../../static/imges/banner3.jpg" alt="" class="img">
                    <img src="./../../static/imges/banner4.jpg" alt="" class="img">
                    <img src="./../../static/imges/banner5.jpg" alt="" class="img">
                    
                    <div class="lf" @click="left_change()"></div>
                    <div class="lr" @click="right_change()"></div>

                    <div class="dots">
                        <span class="square" @click="dots_change($event)"></span>
                        <span @click="dots_change($event)"></span>
                        <span @click="dots_change($event)"></span>
                        <span @click="dots_change($event)"></span>
                        <span @click="dots_change($event)"></span>
                    </div>
                </div>
            </div>
            <div class="newsflash">
                <div class="news">
                    <div class="news-hd">
                        <h5>品优购快报</h5>
                        <a href="javascript:;" class="more">更多</a>
                    </div>
                    <div class="news-bd">
                        <ul>
                            <li><a href="javascript:;"><strong>[特惠]</strong>备战开学季全民半价构数码</a></li>
                            <li><a href="javascript:;"><strong>[公告]</strong>品优稳站家电网购六成份额</a></li>
                            <li><a href="javascript:;"><strong>[特惠]</strong>百元中秋全品类礼券限量领</a></li>
                            <li><a href="javascript:;"><strong>[公告]</strong>上品优生鲜享阳澄湖大闸蟹</a></li>
                            <li><a href="javascript:;"><strong>[特惠]</strong>每日享折扣品优品质游</a></li>
                        </ul>
                    </div>
                </div>
                <div class="lifeservice">
                    <ul>
                        <li>
                            <i></i>
                            <p><a href="javascript:;">话费</a></p>
                        </li>
                        <li>
                            <i class="biaoji-2"></i>
                            <p><a href="javascript:;">机票</a></p>
                        </li>
                        <li>
                            <i class="biaoji-3"></i>
                            <p><a href="javascript:;">电影票</a></p>
                        </li>
                        <li>
                            <i class="biaoji-4"></i>
                            <p><a href="javascript:;">游戏</a></p>
                        </li>
                        <li>
                            <i class="biaoji-5"></i>
                            <p><a href="javascript:;">彩票</a></p>
                        </li>
                        <li>
                            <i class="biaoji-6"></i>
                            <p><a href="javascript:;">加油卡</a></p>
                        </li>
                        <li>
                            <i class="biaoji-7"></i>
                            <p><a href="javascript:;">酒店</a></p>
                        </li>
                        <li>
                            <i class="biaoji-8"></i>
                            <p><a href="javascript:;">火车票</a></p>
                        </li>
                        <li>
                            <i class="biaoji-9"></i>
                            <p><a href="javascript:;">众筹</a></p>
                        </li>
                        <li>
                            <i class="biaoji-10"></i>
                            <p><a href="javascript:;">理财</a></p>
                        </li>
                        <li>
                            <i class="biaoji-11"></i>
                            <p><a href="javascript:;">礼品卡</a></p>
                        </li>
                        <li>
                            <i class="biaoji-12"></i>
                            <p><a href="javascript:;">白条</a></p>
                        </li>
                    </ul>
                </div>
                <div class="bargain">
                    <img src="./../../static/imges/service.png" alt="">
                </div>
            </div>
        </div>
    </div>
    <!-- 首页专有的模块 main end -->

    <!-- 推荐模块 start  -->
    <div class="w recom">
        <div class="recom_hd">
            <img src="./../../static/imges/clock.png" alt="">
            <p>今日推荐</p>
        </div>
        <div class="recom_bd">
            <ul>
                <li><img src="./../../static/imges/rm1.jpg" alt=""></li>
                <li><img src="./../../static/imges/rm2.jpg" alt=""></li>
                <li><img src="./../../static/imges/rm3.jpg" alt=""></li>
                <li><img src="./../../static/imges/rm4.jpg" alt=""></li>
            </ul>
        </div>
    </div>
    <!-- 推荐模块 end  -->

    <!-- 楼层区域制作start -->
    <div class="floor">
        <!-- 1楼家用电器楼层 -->
        <div class="w jiadian">
            <div class="box_hd">
                <h3>家用电器</h3>
                <div class="tab_list">
                    <ul>
                        <li><a href="javascript:;" class="style_red">热门</a>|</li>
                        <li><a href="javascript:;">生活电器</a>|</li>
                        <li><a href="javascript:;">厨房电器</a>|</li>
                        <li><a href="javascript:;">个护健康</a>|</li>
                        <li><a href="javascript:;">应季电器</a>|</li>
                        <li><a href="javascript:;">空气/净水</a>|</li>
                        <li><a href="javascript:;">新奇特</a>|</li>
                        <li><a href="javascript:;">高端电器</a></li>

                    </ul>
                </div>
            </div>
            <div class="box_bd">
                <div class="tab_content">
                    <div class="tab_list_item">
                        <div class="col_210">
                            <ul>
                                <li><a href="">节能补贴</a></li>
                                <li><a href="">4K电视机</a></li>
                                <li><a href="">空气净化器</a></li>
                                <li><a href="">IH电饭煲</a></li>
                                <li><a href="">滚筒洗衣机</a></li>
                                <li><a href="">电热水器</a></li>
                            </ul>
                            <a href="javascript:;">
                                <img src="./../../static/imges/jd1.jpg" alt="">
                            </a>
                        </div>
                        <div class="col_329">
                            <a href="javascript:;">
                                <img src="./../../static/imges/jd2.jpg" alt="">
                            </a>
                        </div>
                        <div class="col_221">
                            <a href="javascript:;" class="bb"><img src="./../../static/imges/jd3.jpg" alt=""></a>
                            <a href="javascript:;"><img src="./../../static/imges/jd4.jpg" alt=""></a>

                        </div>
                        <div class="col_221">
                            <a href="javascript:;">
                                <img src="./../../static/imges/jd5.jpg" alt="">
                            </a>
                        </div>
                        <div class="col_219">
                            <a href="javascript:;" class="bb"><img src="./../../static/imges/jd6.jpg" alt=""></a>
                            <a href="javascript:;"><img src="./../../static/imges/jd7.jpg" alt=""></a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- 2楼手机楼层 -->
        <div class="w shouji">
            <div class="box_hd">
                <h3>手机通讯</h3>
                <div class="tab_list">
                    <ul>
                        <li><a href="javascript:;" class="style_red">热门</a>|</li>
                        <li><a href="javascript:;">生活电器</a>|</li>
                        <li><a href="javascript:;">厨房电器</a>|</li>
                        <li><a href="javascript:;">个护健康</a>|</li>
                        <li><a href="javascript:;">应季电器</a>|</li>
                        <li><a href="javascript:;">空气/净水</a>|</li>
                        <li><a href="javascript:;">新奇特</a>|</li>
                        <li><a href="javascript:;">高端电器</a></li>

                    </ul>
                </div>
            </div>
            <div class="box_bd">
                <div class="tab_content">
                    <div class="tab_list_item">
                        <div class="col_210">
                            <ul>
                                <li><a href="javascript:;">节能补贴</a></li>
                                <li><a href="javascript:;">4K电视机</a></li>
                                <li><a href="javascript:;">空气净化器</a></li>
                                <li><a href="javascript:;">IH电饭煲</a></li>
                                <li><a href="javascript:;">滚筒洗衣机</a></li>
                                <li><a href="javascript:;">电热水器</a></li>
                            </ul>
                            <a href="javascript:;">
                                <img src="./../../static/imges/jd1.jpg" alt="">
                            </a>
                        </div>
                        <div class="col_329">
                            <a href="javascript:;">
                                <img src="./../../static/imges/jd2.jpg" alt="">
                            </a>
                        </div>
                        <div class="col_221">
                            <a href="javascript:;" class="bb"><img src="./../../static/imges/jd3.jpg" alt=""></a>
                            <a href="javascript:;"><img src="./../../static/imges/jd4.jpg" alt=""></a>

                        </div>
                        <div class="col_221">
                            <a href="javascript:;">
                                <img src="./../../static/imges/jd5.jpg" alt="">
                            </a>
                        </div>
                        <div class="col_219">
                            <a href="javascript:;" class="bb"><img src="./../../static/imges/jd6.jpg" alt=""></a>
                            <a href="javascript:;"><img src="./../../static/imges/jd7.jpg" alt=""></a>
                        </div>
                    </div>
                </div>
            </div>
        </div>

    </div>
    <!-- 楼层区域制作end -->

    <Footer></Footer>
</div>
</template>

<script>
import Footer from './Footer.vue';
import Header from './Header.vue';
export default {
  name: 'Home',
  data () {
    return {
        imgs:[],
        dots:[],
        timer:"",

        dropdown:[
            "家用电器","手机、数码、通信","电脑、办公","家居、家具、家装、厨具","男装、女装、童装、内衣",
            "个户化妆、清洁用品、宠物","鞋靴、箱包、珠宝、奢侈品","运动户外、钟表","汽车、汽车用品","母婴、玩具乐器",
            "食品、酒类、生鲜、特产","医疗保健","图书、音像、电子书","彩票、旅行、充值、票务","理财、众筹、白条、保险",
        ],
        navitems:[
            "服装城","美妆馆","传智超市","全球购","闪购","团购","拍卖","有趣",
        ],

     }
  },
  components: {Footer,Header},
  methods:{
      changeImage: function(currentIndex) {
        if (currentIndex < 4) {
            this.imgs[currentIndex].classList.remove('current');
            this.dots[currentIndex].classList.remove('square');
            this.imgs[++currentIndex].classList.add('current');
            this.dots[currentIndex].classList.add('square');
        } else {
            this.imgs[currentIndex].classList.remove('current');
            this.dots[currentIndex].classList.remove('square');
            currentIndex = 0;
            this.imgs[currentIndex].classList.add('current');
            this.dots[currentIndex].classList.add('square');
        }
    },
    loop: function(){
        let current = document.querySelector('.scroll .current');
        let currentIndex = current.getAttribute('data-index');
        this.changeImage(currentIndex);
    },
    left_change(){
 
        // 获取当前图片 和 图片的index（数组下标）
        let current = document.querySelector('.scroll .current');
        let currentIndex = current.getAttribute('data-index');
        if (currentIndex > 0) {
            this.imgs[currentIndex].classList.remove('current');
            this.dots[currentIndex].classList.remove('square');
            this.imgs[--currentIndex].classList.add('current');
           this.dots[currentIndex].classList.add('square');
        } else {
            this.imgs[currentIndex].classList.remove('current');
            this.dots[currentIndex].classList.remove('square');
            currentIndex = 4;
            this.imgs[currentIndex].classList.add('current');
            this.dots[currentIndex].classList.add('square');
        }
    },
    right_change(){
        // 获取当前图片 和 图片的index（数组下标）
        let current = document.querySelector('.scroll .current');
        let currentIndex = current.getAttribute('data-index');
        this.changeImage(currentIndex);
    },
    dots_change(e){
            let current = document.querySelector('.scroll .current');
            let currentIndex = current.getAttribute('data-index');

            let index = e.currentTarget.getAttribute('data-index');
            if (index != currentIndex) {
                this.imgs[currentIndex].classList.remove('current');
                this.dots[currentIndex].classList.remove('square');
                this.imgs[index].classList.add('current');
               this.dots[index].classList.add('square');
                // currentIndex = index;
            }
 
    },
      
  },
  created(){
        
  },
  activated(){
      
  },
  mounted(){
    // 获取图片和圆点
    this.imgs = document.querySelectorAll('.scroll .img');
    this.dots = document.querySelector('.scroll .dots').querySelectorAll('span');

    // 给图片设置index 属性，好判断当前的图片是哪一张
    for (let i = 0; i < this.imgs.length; i++) {
        this.imgs[i].setAttribute('data-index', i);
    }
    // 给圆点设置index属性
     for (let k = 0; k < this.dots.length; k++) {
        this.dots[k].setAttribute('data-index', k);
    }

    //设置定时器，自动循环
    this.timer=setInterval(this.loop,3000);
  },
  beforeDestroy() {

      clearInterval(this.timer);//删除定时器

    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import './../../static/css/common.css';
@import './../../static/css/home.css';
</style>
