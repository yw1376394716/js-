<template>
    <div>
        
    </div>
</template>
<script>
export default {
    mounted() {
        setTimeout(() => {
            console.log('111111')
        }, 1000);

        setTimeout(function () {
            console.log('222222')
        },2000)
    },
    methods: {
        // 数组某一项放到第一项
        fn1(){
            let id = '03';
            let arr = [{name:'张三',id:'01'},{name:'李四',id:'02'},{name:'王五',id:'03'}];
            for (let i = 0; i < arr.length; i++) {   			  
                console.log(arr[i])  
                if (arr[i].id == id) {
                    let arr2 = arr[i]
                    arr.splice(i,1)
                    arr.unshift(arr2)
                    console.log('arr',arr)
                } 
            }
        }
    },
}
</script>


