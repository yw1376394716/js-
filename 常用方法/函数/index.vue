<template>
    <div>
        <p>函数声明式     例如：fn1()</p>
        

        <p>函数表达式     例如：fn2()</p>


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
        // 函数声明式
        fn1(){
            function demo() {
                // ......
            }
        },
        // 函数表达式
        fn2(){
            var demo = function () {
                // ......
            }
        }
    },
}
</script>