<template>
    <div class="box">        
        <!-- 48个 JS 开发常用工具函数 https://mp.weixin.qq.com/s/uSm4Ktb_vGJK8EL1D2zjMA -->
        <h1>js常用方法</h1>
        <p> 
            <span>防抖</span>
            当一次事件发生后，事件处理器要等一定阈值的时间，如果这段时间过去后 再也没有 事件发生，
            就处理最后一次发生的事件。假设还差 0.01 秒就到达指定时间，
            这时又来了一个事件，那么之前的等待作废，需要重新再等待指定时间。
        </p>
        <p> 
            <span>节流</span>
            可以理解为事件在一个管道中传输，加上这个节流阀以后，事件的流速就会减慢。
            实际上这个函数的作用就是如此，它可以将一个函数的调用频率限制在一定阈值内，
            例如 1s，那么 1s 内这个函数一定不会被调用两次
        </p>     
        <p>生成随机UID</p>
        <p>全屏</p>
        <p>退出全屏</p>
        <p>求取数组中非NaN数据中的最大值</p>
        <p>求取数组中非NaN数据中的最小值</p>
        <p>无loop生成指定长度的数组</p>
        <p>RGB色值生成16进制色值</p>
        <p>颜色混合</p>
        <p>判断是否为质数</p>
        <p>遍历类数组对象</p>
        <p>时间格式化</p> 

        <p>sort 排序</p>
        <p>reduce(数组内每一项数字相加)</p>
        <p>filter(过滤数组)</p>
        <p>every(每一项是否满足)</p>
        <p>some(有一项满足返回 true)</p>
        <p>indexOf (如果存在返回-1)</p>  
        <p>includes(字符串或数组中是否含有某项)</p>
        <p>find</p>

        <p>对象和数组转化</p>
        <p>数字金额千分位格式化</p>
        
    </div>
</template>
<script>
export default {
    name:name,
    data() {
        return {
            
        }
    },
    mounted() {
        
    },
    methods: {
        // 防抖动函数
        debounce(fn,wait=50,immediate){             
            let timer;
            return function() {
                if (immediate) {
                    fn.apply(this,arguments)
                }
                if (timer) 
                clearTimeout(timer)
                timer = setTimeout(()=>{
                    fn.apply(this,arguments)
                },wait)
            }
        },
        // 节流函数
           
        // 生成随机UID
        idfn(){
            const genUid = () => {
            var length = 20
            var soupLength = genUid.soup_.length
            var id = []
            for (var i = 0; i < length; i++) {
                id[i] = genUid.soup_.charAt(Math.random() * soupLength)
            }
            return id.join('')
            }
            genUid.soup_ = '!#$%()*+,-./:;=?@[]^_`{|}~ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789'
            genUid() // ;l`yCPc9A8IuK}?N6,%}  
        },
        // 全屏
        toFullScreen(){
            let elem = document.body;
            elem.webkitRequestFullScreen
            ? elem.webkitRequestFullScreen()
            : elem.mozRequestFullScreen
            ? elem.mozRequestFullScreen()
            : elem.msRequestFullscreen
            ? elem.msRequestFullscreen()
            : elem.requestFullScreen
            ? elem.requestFullScreen()
            : alert("浏览器不支持全屏");
        },
        // 退出全屏
        exitFullscreen(){
            let elem = parent.document;
            elem.webkitCancelFullScreen
            ? elem.webkitCancelFullScreen()
            : elem.mozCancelFullScreen
            ? elem.mozCancelFullScreen()
            : elem.cancelFullScreen
            ? elem.cancelFullScreen()
            : elem.msExitFullscreen
            ? elem.msExitFullscreen()
            : elem.exitFullscreen
            ? elem.exitFullscreen()
            : alert("切换失败,可尝试Esc退出");
        },     
        // 求取数组中非NaN数据中的最大值
        max(arr){
            arr = arr.filter(item => !_isNaN(item))
            return arr.length ? Math.max.apply(null, arr) : undefined
            // 例：max([1, 2, '11', null, 'fdf', []]) ==> 11 
        },   
        //  求取数组中非NaN数据中的最小值   
        min(arr){
            arr = arr.filter(item => !_isNaN(item))
            return arr.length ? Math.min.apply(null, arr) : undefined
            //min([1, 2, '11', null, 'fdf', []]) ==> 1 
        },
         
        // 无loop生成指定长度的数组
        fn1(){
            const List = len => [...new Array(len).keys()]
            const list = List(10) // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
        },
        // RGB色值生成16进制色值
        fn2(){
            const rgb2Hex = (r, g, b) => {
                r = Math.max(Math.min(Number(r), 100), 0) * 2.55
                g = Math.max(Math.min(Number(g), 100), 0) * 2.55
                b = Math.max(Math.min(Number(b), 100), 0) * 2.55
                r = ('0' + (Math.round(r) || 0).toString(16)).slice(-2)
                g = ('0' + (Math.round(g) || 0).toString(16)).slice(-2)
                b = ('0' + (Math.round(b) || 0).toString(16)).slice(-2)
                return '#' + r + g + b
            }
            rgb2Hex(100, 50, 0) // "#ff7f00"            
        },
        // 颜色混合
        fn3(){
            const colourBlend = (c1, c2, ratio) => {
                ratio = Math.max(Math.min(Number(ratio), 1), 0)
                let r1 = parseInt(c1.substring(1, 3), 16)
                let g1 = parseInt(c1.substring(3, 5), 16)
                let b1 = parseInt(c1.substring(5, 7), 16)
                let r2 = parseInt(c2.substring(1, 3), 16)
                let g2 = parseInt(c2.substring(3, 5), 16)
                let b2 = parseInt(c2.substring(5, 7), 16)
                let r = Math.round(r1 * (1 - ratio) + r2 * ratio)
                let g = Math.round(g1 * (1 - ratio) + g2 * ratio)
                let b = Math.round(b1 * (1 - ratio) + b2 * ratio)
                r = ('0' + (r || 0).toString(16)).slice(-2)
                g = ('0' + (g || 0).toString(16)).slice(-2)
                b = ('0' + (b || 0).toString(16)).slice(-2)
                return '#' + r + g + b
            }
            colourBlend('#ff0000', '#3333ff', 0.5) // "#991a80"            
        },
        // 判断是否为质数
        fn4(){
            const mathIsPrime = n => {
            if (n === 2 || n === 3) {
                return true
            }
            if (isNaN(n) || n <= 1 || n % 1 != 0 || n % 2 == 0 || n % 3 == 0) {
                return false;
            }
            for (let x = 6; x <= Math.sqrt(n) + 1; x += 6) {
                if (n % (x - 1) == 0 || n % (x + 1) == 0) {
                return false
                }
            }
            return true
            }
            mathIsPrime(0) // true            
        },
        // 遍历类数组对象
        fn5(){
            const elements = document.querySelectorAll(selector);
            [].prototype.forEach.call(elements, (el, idx, list) => {
                console.log(el) // 元素节点
            })            
        },
        // 时间格式化
        fn6(){
            const dateFormatter = (formatter, date) => {
                date = (date ? new Date(date) : new Date)
                const Y = date.getFullYear() + '',
                    M = date.getMonth() + 1,
                    D = date.getDate(),
                    H = date.getHours(),
                    m = date.getMinutes(),
                    s = date.getSeconds()
                return formatter.replace(/YYYY|yyyy/g, Y)
                                .replace(/YY|yy/g, Y.substr(2, 2))
                                .replace(/MM/g, (M < 10 ? '0' : '') + M)
                                .replace(/DD/g, (D < 10 ? '0' : '') + D)
                                .replace(/HH|hh/g, (H < 10 ? '0' : '') + H)
                                .replace(/mm/g, (m < 10 ? '0' : '') + m)
                                .replace(/ss/g, (s < 10 ? '0' : '') + s)
            }

            dateFormatter('YYYY-MM-DD HH:mm', '1995/02/15 13:55') // 1995-02-15 13:55
        },
        // sort 排序
        fn7(){
            let arr=[1,2,3,4,5,6];
            arr.sort();//[1,2,3,4,5,6]
            arr.sort((a,b)=>b-a);//[6,5,4,3,2,1]
        },        
        // reduce (https://www.jianshu.com/p/541b84c9df90)  
        fn8(){
            // arr.reduce(function(prev,cur,index,arr){
            // ...
            // }, init);    
            // arr 表示原数组；
            // prev 表示上一次调用回调时的返回值，或者初始值 init;
            // cur 表示当前正在处理的数组元素；
            // index 表示当前正在处理的数组元素的索引，若提供 init 值，则索引为0，否则索引为1；
            // init 表示初始值    
            
            // 1. 求数组项之和 0是初始值
            let arr=[1,2,3,4,5];
            var sum = arr.reduce(function (prev, cur) {
                return prev + cur;
            },0);
            // 由于传入了初始值0，所以开始时prev的值为0，cur的值为数组第一项3，
            // 相加之后返回值为3作为下一轮回调的prev值，然后再继续与下一个数组项相加，
            // 以此类推，直至完成所有数组项的和并返回。

            // 2. 求数组项最大值
            var max = arr.reduce(function (prev, cur) {
                return Math.max(prev,cur);
            });    
            // 由于未传入初始值，所以开始时prev的值为数组第一项3，cur的值为数组第二项9，取两值最大值后继续进入下一轮回调。
        },
        // filter 过滤数组
        fn9(){
            let arr=[1,2,3,4,5,6];
            arr.filter(item=>{
                return item >3
            })
        },
        // every 每一项是否满足 (只有每一项满足返回 true。)
        fn10(){
            let arr=[1,2,3,4,5,6];
            arr.every(item=>{
                return item >3
            })
        },
        // some 有一项满足返回 true
        fn11(){
            let arr=[1,2,3,4,5,6];
            arr.some(item=>{
                return item >3
            })            
        },
        // indexOf 如果存在返回索引,如果数组中无值返回-1
        fn12(){
            let arr=[1,2,3,4,5,6];
            arr.indexOf(0) // -1
            arr.indexOf(1) // 0
        },
        fn13(){
            var str = '123456789asdqwert';
            console.log(str.includes('d'));  // true

            var arr = ['a','s','f','g','h','j','k','a']
            console.log(arr.includes('s'));    // true
            console.log(arr.includes('a','s')); // true  

            // 该方法的第二个参数表示搜索的起始位置，默认为0。如果第二个参数为负数，则表示倒数的位置，
            // 如果这时它大于数组长度(比如第二个参数为-4， 但数组长度为3)，则会重置为0开始
            console.log(arr.includes('a',0));  // true  
            console.log(arr.includes('a',-1)); // true 

        },
        // find 
        fn14(){
            let arr=[1,2,3,4,5,6];
            arr.find((value, index, arr) => {
                // value：每一次迭代查找的数组元素。
                // index：每一次迭代查找的数组元素索引。
                // arr：被查找的数组。
            })
        },
        // Object 对象和数组转化
        fn15(){
            Object.keys({name:'张三',age:14});   // ["name", "age"]
            Object.values({name:'张三',age:14}); // ["张三", 14]
            Object.entries({name:'张三',age:14});// [[name,'张三'],[age,14]]
        },
        // 数字金额千分位格式化
        fn16(){
            
            var num = 123455678;
            var num1 = 123455678.12345;

            // 1 使用Number.prototype.toLocaleString()
            var formatNum = num.toLocaleString('en-US');
            var formatNum1 = num1.toLocaleString('en-US');

            console.log(formatNum); // 123,455,678
            console.log(formatNum1); // 123,455,678.123     

            // 2 使用正则表达式
            var formatNum = String(num).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
            var formatNum1 = String(num1).replace(/\B(?=(\d{3})+(?!\d))/g, ',');

            console.log(formatNum); // 123,455,678
            console.log(formatNum1); // 123,455,678.12,345                   
        }
    },
}
</script>
<style >
    .box p{
        font-size: 20px;
        color: rgb(218, 82, 82);
    }
</style>