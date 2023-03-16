# captcha

#### 介绍
滑块、旋转、点击等图片验证的前端js，引入一行js即可方便快捷使用

可搭配仓库 [poster ](https://gitee.com/langlanglang/poster) 一起使用

觉得不错的话，点个星星，谢谢大家

lang 732853989@qq.com

群号 590660254 [点击链接加入群聊【海报图片验证交流群】](https://jq.qq.com/?_wv=1027&k=k374FhrR)

#### 演示
[滑块前端演示 http://langlanglang.gitee.io/captcha/](http://langlanglang.gitee.io/captcha/ "滑块前端演示")


#### 安装教程

1. 直接引入js 

   ```html
   <!DOCTYPE html>
   <html>
       <head>
           <meta charset="utf-8">
           <meta name="viewport" content="width=device-width, initial-scale=1">
           <title>图片验证DEMO</title>
       </head>
       <body>
           <button type="button" onclick="captcha()">
               验证
           </button>
       </body>
   </html>
   <script type="text/javascript" src="./slider/slider-min.js"></script>
   ```

#### 使用说明

1. 滑块验证

   ```html
   <script type="text/javascript">
       // 开始验证
       function captcha(){
           // 根据 poster 获取验证参数
           Slider = new langSlider({
               title: '滑块安全验证', 
               start: function(Slider) {
                   setTimeout(function(){
                       Slider.sliderStart({
                           sliderBg: './slider/img/slider.png', 
                           sliderKey: '1212', 
                           sliderY: 46
                       })
                   }, 1000);
               },
               check: function(sliderKey, sliderX, Slider) {
   
                   // 模拟调用验证接口
                   const check = () => {
                       const leeway = 5 // 误差值
                       const value = 208 // 正确值
                       if(value >= (sliderX - leeway) && value <= (sliderX + leeway)){
                           // 成功调用该方法
                           Slider.sliderSuccess()
                       } else {
                           // 错误调用该方法
                           // 模拟调用获取验证参数接口
                           setTimeout(function(){
                               Slider.sliderError({
                                   sliderBg: './slider/img/slider.png', 
                                   sliderKey: '1212', 
                                   sliderY: 46
                               })
                           }, 1000);
                       }
                   }
   
                   setTimeout(function(){
                       check()
                   }, 1000)
   
               },
               refresh: function(Slider){
                   
                   setTimeout(function(){
                       Slider.sliderRefresh({
                           sliderBg: './slider/img/slider.png', 
                           sliderKey: '1212', 
                           sliderY: 46
                       })
                   }, 1000);
               },
           })
       }
   </script>
   ```
   
   

#### 参与贡献

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request
