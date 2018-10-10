<template>
  <section class="msite">
    <!--首页头部-->
    <HeaderTop title="首页">
      <a class="header_search" slot="left" >
        <i class="iconfont icon-sousuo"></i>
      </a>
  		<a class="header_login" slot="right" >
        <span class="header_login_text" >
        		  登录|注册
        </span>
        <span class="header_login_text" >
           <i class="iconfont icon-person"></i>
        </span>
     	</a>
    </HeaderTop>
    <div class="miste-content-wrapper">
      <div class="miste-content">
        <!--首页导航-->
        <nav class="msite_nav">
          <div class="swiper-container" v-if="imgs.length">
            <div class="swiper-wrapper">
              <div class="swiper-slide" v-for="(items,index) in imgs" :key="index">
                <a href="javascript:;" class="link_to_food" v-for="(item,index) in items" :key="index">
                  <div class="food_container">
                    <img :src="item.file">
                  </div>
                  <span>{{item.title}}</span>
                </a>
              </div>
            </div>
            <!-- Add Pagination -->
            <div class="swiper-pagination"></div>
          </div>
          <img src="./images/msite_back.svg" alt="back" v-else>
        </nav>
        <!--首页附近商家-->
        <div class="msite_shop_list">
          <div class="shop_header">
            <i class="iconfont icon-xuanxiang"></i>
            <span class="shop_header_title">附近商家</span>
          </div>
          <ShopList/>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
	
import BScroll from 'better-scroll' 	
import HeaderTop from '../../components/HeaderTop/HeaderTop.vue' 	
import ShopList from '../../components/ShopList/ShopList.vue' 	

import Swiper from 'swiper'
import 'swiper/dist/css/swiper.min.css'

export default {
  data () {
    return {
    	 urlImgPath:'../images/nav/',
    	 imgs:[
    	 		[
    	 			{file:require('../images/nav/1.jpg'),title:'11'},
	    	  	{file:require('../images/nav/2.jpg'),title:'22'},
	    	  	{file:require('../images/nav/3.jpg'),title:'33'},
	    	  	{file:require('../images/nav/4.jpg'),title:'44'},
	    	  	{file:require('../images/nav/5.jpg'),title:'55'},
	    	  	{file:require('../images/nav/6.jpg'),title:'66'},
	    	  	{file:require('../images/nav/7.jpg'),title:'77'}
    	 		],
    	  	[
	    	  	{file:require('../images/nav/8.jpg'),title:'88'},
	    	  	{file:require('../images/nav/9.jpg'),title:'99'},
	    	  	{file:require('../images/nav/10.jpg'),title:'100'},
	    	  	{file:require('../images/nav/11.jpg'),title:'111'},
	    	  	{file:require('../images/nav/12.jpg'),title:'222'},
	    	  	{file:require('../images/nav/13.jpg'),title:'130'},
	    	  	{file:require('../images/nav/14.jpg'),title:'140'}
    	  	]
    	 ]
    }
  },
  mounted(){
  	 new Swiper('.swiper-container',{
  	 	 loop:true,//可以循环轮播
  	 	 //需要分页器
  	 	 pagination:{
  	 	 	el:'.swiper-pagination'
  	 	 }
  	 }) 
  	 
  	 new BScroll('.miste-content-wrapper', {
            click: true
     }) 
  },
  components: {
      HeaderTop,
      ShopList
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style lang="stylus" rel="stylesheet/stylus">
  @import "../../common/stylus/mixins.styl"
  .msite  //首页
    width 100%
    .miste-content-wrapper
      position fixed
      top: 45px
      bottom: 46px
      width: 100%
      .msite_nav
        bottom-border-1px(#e4e4e4)
        margin-top 15px
        height 200px
        background #fff
        .swiper-container
          width 100%
          height 100%
          .swiper-wrapper
            width 100%
            height 100%
            .swiper-slide
              display flex
              justify-content center
              align-items flex-start
              flex-wrap wrap
              .link_to_food
                width 25%
                .food_container
                  display block
                  width 100%
                  text-align center
                  padding-bottom 10px
                  font-size 0
                  img
                    display inline-block
                    width 50px
                    height 50px
                span
                  display block
                  width 100%
                  text-align center
                  font-size 13px
                  color #666
          .swiper-pagination
            >span.swiper-pagination-bullet-active
              background #02a774
      .msite_shop_list
        top-border-1px(#e4e4e4)
        margin-top 10px
        background #fff
        .shop_header
          padding 10px 10px 0
          .shop_icon
            margin-left 5px
            color #999
          .shop_header_title
            color #999
            font-size 14px
            line-height 20px
</style>