<template>
    <div>
        
    </div>
</template>
<script>
export default {
    data() {
        return {
            
        }
    },
    mounted() {

        // js运算保留两位小数
        let a = 1   , b = 2 
        console.log('a *100 - b*100 ',a *100 - b*100 ) // 避免精度问题

        Math.round(a *100 - b*100 ) /100    // Math.round() 四舍五入为最接近的整数。




        /**
        * 加法运算，避免数据相加小数点后产生多位数和计算精度损失。
        * 
        * @param num1加数1 | num2加数2
        */
        function numAdd(num1, num2) {
            var baseNum, baseNum1, baseNum2;
            try {
                baseNum1 = num1.toString().split(".")[1].length;
            } catch (e) {
                baseNum1 = 0;
            }
            try {
                baseNum2 = num2.toString().split(".")[1].length;
            } catch (e) {
                baseNum2 = 0;
            }
            baseNum = Math.pow(10, Math.max(baseNum1, baseNum2));
            return (num1 * baseNum + num2 * baseNum) / baseNum;
        }
        
        
        
        /**
        * 减法运算，避免数据相减小数点后产生多位数和计算精度损失。
        * 
        * @param num1被减数  |  num2减数
        */
        function numSub(num1, num2) {
            var baseNum, baseNum1, baseNum2;
            var precision;// 精度
            try {
                baseNum1 = num1.toString().split(".")[1].length;
            } catch (e) {
                baseNum1 = 0;
            }
            try {
                baseNum2 = num2.toString().split(".")[1].length;
            } catch (e) {
                baseNum2 = 0;
            }
            baseNum = Math.pow(10, Math.max(baseNum1, baseNum2));
            precision = (baseNum1 >= baseNum2) ? baseNum1 : baseNum2;
            return ((num1 * baseNum - num2 * baseNum) / baseNum).toFixed(precision);
        }
        
        
        
        /**
        * 乘法运算，避免数据相乘小数点后产生多位数和计算精度损失。
        * 
        * @param num1被乘数 | num2乘数
        */
        function numMulti(num1, num2) {
            var baseNum = 0;
            try {
                baseNum += num1.toString().split(".")[1].length;
            } catch (e) {
            }
            try {
                baseNum += num2.toString().split(".")[1].length;
            } catch (e) {
            }
            return Number(num1.toString().replace(".", "")) * Number(num2.toString().replace(".", "")) / Math.pow(10, baseNum);
        }
        
        
        
        /**
        * 除法运算，避免数据相除小数点后产生多位数和计算精度损失。
        * 
        * @param num1被除数 | num2除数
        */
        function numDiv(num1, num2) {
            var baseNum1 = 0, baseNum2 = 0;
            var baseNum3, baseNum4;
            try {
                baseNum1 = num1.toString().split(".")[1].length;
            } catch (e) {
                baseNum1 = 0;
            }
            try {
                baseNum2 = num2.toString().split(".")[1].length;
            } catch (e) {
                baseNum2 = 0;
            }
            with (Math) {
                baseNum3 = Number(num1.toString().replace(".", ""));
                baseNum4 = Number(num2.toString().replace(".", ""));
                return (baseNum3 / baseNum4) * pow(10, baseNum2 - baseNum1);
            }
        }          
    },
    methods: {

     
    },
}
</script>