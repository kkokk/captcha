# captcha

#### 介绍
滑块、旋转、点击等图片验证的前端js，引入一行js即可方便快捷使用

可搭配仓库 [poster ](https://github.com/kkokk/poster) 一起使用

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
   <script type="text/javascript" src="./slider/slider.js"></script>
   ```

#### 使用说明

1. 滑块验证

   ```html
   <script type="text/javascript">
       function captcha(){
           // 根据 poster 获取验证参数
           sliderStart(res, 
           function(sliderKey, sliderX, sliderSuccess, sliderError){
               // sliderKey // 验证key
               // sliderX // 验证x轴距离
               // ...调用验证接口
   
               // 模拟调用验证接口
               const check = () => {
                   const success = Math.floor(Math.random() * 2 + 1)
                   if(success === 1){
                       // 成功调用该方法
                       sliderSuccess()
                   } else {
                       // 错误调用该方法
                       // 模拟调用获取验证参数接口
                       getSliderOption(sliderError)
                   }
               }
               setTimeout(function(){
                   check()
               }, 1000)
           },
           function(refresh){
               // 刷新
               // ... 需要调用刷新接口 重新获取图片参数
   
               // 模拟调用获取验证参数接口
               setTimeout(function(){
                   getSliderOption(refresh)
               }, 1000)
   
           })
       }
   
       // 获取验证参数接口
       function getSliderOption(callback){
           const res = {
               sliderBg: './slider/img/slider.png', 
               sliderKey: '1212', 
               sliderY: 46
           }
           callback(res)
       }
   </script>
   ```

   

#### 参与贡献

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request
