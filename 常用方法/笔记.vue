<template>
    <div>
        <h2>import  ,export  ,export default  (文件引入，导出))</h2>

        <p>import </p>
        <span> import引入文件  例如： import { Vue } from 'vue'; </span>

        <p>export </p>
        <span> 
            export 导出文件 （可以导出多个文件） 

            例子：
            <!-- demo1.js （导出页面）-->
            export const str = 'hello world'
            export function f(a){
                return a+1
            }  

            <!-- 对应的引入方式： -->
            <!-- demo2.js （其他页面引入）-->
            import { str, f } from 'demo1'               
            
        </span>

        <p>export default </p>
        <span> 
            export 导出文件 （只可以导出1个文件，这个模块可以匿名） 
            
            <!-- demo1.js -->
            export default {
                a: 'hello',
                b: 'world'      
            }
            　　对应的引入方式：

            <!-- 对应的引入方式： -->
            <!-- demo2.js （其他页面引入）-->
            import obj from 'demo1'  
            <!-- 使用 a 时 obj.a -->
        </span>        
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