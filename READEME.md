# day 01
  ## 一、功能
      1、首页的静态页面
  ## 二、技术
     1、swiper库实现轮播（Swiper 4.1.6），在这里的轮播图片是作为背景轮播的，
        因为上面还有二级菜单要定位在轮播图上
       使用：
       1）在msit.html中引入swiper库及相应的样式
          <link rel="stylesheet" href="./common/css/swiper.min.css">
          <script type="text/javascript" src="./js/swiper.min.js"></script>
        2）样式：
           .swiper-container{
                 width: 100%;
                 height: 420px;
                 .swiper-wrapper{
                   width: 100%;
                   height: 100%;
                   .swiper-slide{
                     width: 100%;
                     height: 100%;
                     .banner_bd{
                       width: 100%;
                       height: 100%;
                       &.bd1{
                         background: url('../images/banner1.jpg') center center no-repeat;
                       }
                       &.bd2{
                         background: url('../images/banner2.jpg') center center no-repeat;
                       }
                       &.bd3{
                         background: url('../images/banner3.jpg') center center no-repeat;
                       }
                     }
                   }
                 }
                 .swiper-pagination{
                   >span.swiper-pagination-bullet-active{
                     background: #02a774;
                   }
              }
           3）代码
              <div class="banner swiper-container">
                <div class="swiper-wrapper">
                  <div class="swiper-slide">
                    <div class="banner_bd bd1"></div>
                  </div>
                  <div class="swiper-slide">
                    <div class="banner_bd bd2" ></div>
                  </div>
                  <div class="swiper-slide">
                    <div class="banner_bd bd3"></div>
                  </div>
                </div>
                   // 轮播小圆点
                <div class="swiper-pagination"></div>
              </div>   
           4）配置
              $(document).ready(function(){
                    new Swiper ('.banner.swiper-container', {
                      loop: true,
                      // 小圆点分页器
                      pagination: {
                        el: '.swiper-pagination',
                      },
                      effect : 'fade',
                      fadeEffect: {  // 淡入淡出
                        delay: 3000,
                        crossFade: true,
                      },
                      autoplay: {  // 配置无限循环轮播
                        delay: 3000,
                        disableOnInteraction: false,
                      }
                    })
                  })
  ## 三、问题  
    1、用flex做头部布局，当浏览器宽度变小的一定的程度时，布局样式就乱了，内容就会换行了
       解决：给开了flex的元素设置  white-space: nowrap;
    2、二级菜单的实现：两层ul来实现
       1）最外层的包裹器（与外层ul等高宽）开启绝对定位，定位到轮播图，最外层ul开启相对定位，
       外层的li不开定位，里层的ul开启绝对定位（让它相对与外层ul而不是它的父级li），这样就
       可以解决二级菜单的位置出现实总是与其父级同高的问题了
    3、给原价45价格划掉，直接用<del>45</del>   删除标签就出来了