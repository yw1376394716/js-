<template>
    <div>
        <div>
            1. V-Hotkey

            仓库地址: https://github.com/Dafrok/v-hotkey
            Demo: 戳这里 https://dafrok.github.io/v-hotkey
            安装: npm install --save v-hotkey
            这个指令可以给组件绑定一个或多个快捷键。你想要通过按下 Escape 键后隐藏某个组件，按住 Control 和回车键再显示它吗？小菜一碟：        
        </div>
        <div>
            2. V-Click-Outside

            仓库地址: https://github.com/ndelvalle/v-click-outside
            Demo: https://codesandbox.io/s/zx7mx8y1ol?module=%2Fsrc%2Fcomponents%2FHelloWorld.vue
            安装: npm install --save v-click-outside

            你想要点击外部区域关掉某个组件吗？用这个指令可以轻松实现。这是我每个项目必用的指令之一，尤其在弹框和下拉菜单组件里非常好用。    
        </div>
        <div>
            3. V-Clipboard

            仓库地址: https://github.com/euvl/v-clipboard
            安装: npm install --save v-clipboard

            这个简单指令的作者是Yev Vlasenko ，可以用在任何静态或动态元素上。当元素被点击时，指令的值会被复制到剪贴板上。用户需要复制代码片段的时候，这个非常有用。    
        </div>
        <div>
            4. Vue-ScrollTo

            仓库地址: https://github.com/rigor789/vue-scrollTo
            Demo: https://vue-scrollto.netlify.com/
            安装: npm install --save vue-scrollto

            这个指令监听元素的点击事件，然后滚动到指定位置。我通常用来处理文章目录跳转和导航跳转。            
        </div>
        <div>
            5. Vue-Lazyload

            仓库地址: https://github.com/hilongjw/vue-lazyload
            Demo: http://hilongjw.github.io/vue-lazyload/
            安装: npm install --save vue-lazyload
            图片懒加载，非常方便。  
            <!-- <img v-lazy="https://www.domain.com/image.jpg">           -->
        </div>
        <div>
            6. V-Tooltip

            仓库地址: v-tooltip
            Demo: available here
            安装: npm install --save v-tooltip
            几乎每个项目都会用到 tooltip。这个指令可以给元素添加响应式的tooltip，并可控制显示位置、触发方式和监听事件            
            <!-- <button v-tooltip="'You have ' + count + ' new messages.'"> -->
        </div>
        <div>
            7. V-Scroll-Lock

            仓库地址: https://github.com/phegman/v-scroll-lock
            Demo: https://v-scroll-lock.peterhegman.com/
            安装: npm install --save v-scroll-lock

            基于 body-scroll-lock 开发，这个指令的作用是在打开模态浮层的时候防止下层的元素滚动。            
        </div>
        <div>
            8. V-Money

            仓库地址: https://github.com/vuejs-tips/v-money
            Demo: https://vuejs-tips.github.io/v-money/
            安装: npm install --save v-money
            如果你需要在输入框里加上货币前缀或后缀、保留小数点位数或者设置小数点符号——不用找了，就是它！一行代码搞定这些需求：            
        </div>
        <div>
            9. Vue-Infinite-Scroll

            仓库地址: https://github.com/ElemeFE/vue-infinite-scroll
            安装: npm install --save vue-infinite-scroll

            无限滚动指令，当滚动到页面底部时会触发绑定的方法。    
        </div>
        <div>
            10. Vue-Clampy
            
            仓库地址: vue-clampy.
            安装: npm install --save @clampy-js/vue-clampy

            这个指令会截断元素里的文本，并在末尾加上省略号。它是用clampy.js实现的。
        </div>
        <div>
            11. Vue-InputMask

            仓库地址: vue-inputmask
            安装: npm install --save vue-inputmask
            当你需要在输入框里格式化日期时，这个指令会自动生成格式化文本。基于Inputmask library 开发。
        </div>
        <div>
            12. Vue-Ripple-Directive

            仓库地址: vue-ripple-directive
            安装: npm install --save vue-ripple-directive

            Aduardo Marcos 写的这个指令可以给点击的元素添加波纹动效。
        </div>
        <div>
            13. Vue-Focus

            仓库地址: vue-focus
            安装: npm install --save vue-focus
            有时候，用户在界面里操作，需要让某个输入框获得焦点。这个指令就是干这个的。            
        </div>
        <div>
            14. V-Blur

            仓库地址: v-blur
            Demo: 戳这里
            安装: npm install --save v-blur
            假设你的页面在访客没有注册的时候，有些部分需要加上半透明遮罩。用这个指令可以轻松实现，还可以自定义透明度和过渡效果。    
        </div>
        <div>
            15. Vue-Dummy

            仓库地址: vue-dummy
            Demo: available here
            安装: npm install --save vue-dummy
            开发 app 的时候，偶尔会需要使用假文本数据，或者特定尺寸的占位图片。用这个指令可以轻松实现。
        </div>


    </div>


</template>
<script>
    export default {
        data() {
            return {
                
            }
        },
        mounted() {
            
        },
        methods: {
            
        },
    }
</script>