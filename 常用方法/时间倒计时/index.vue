<template>
    <div>
        <p>时间倒计时(2021-09-25 02:02:02)</p>
        <span>{{time}}</span>
    </div>
</template>
<script>
  export default {
    name: "name",
    data(){
        return {
            time:'',
        }
    },
    mounted(){
        let _this = this;
        setInterval(() =>{
            timeFn('2021-09-25 02:02:02');
        }, 1000);

        function timeFn(e){

            e = e.replace(/\-/g, "/");
            var newDate = new Date();
            var endDate = e;
            var s = parseInt((Date.parse(endDate) - Date.parse(newDate)) / 1000);
            var day = Math.floor(s / 86400);
            s = s % 86400;
            var hours = Math.floor(s / 3600);
            s = s % 3600;
            var minutes = Math.floor(s / 60);
            s = s % 60;
            var s4 = s;

            if (day >= 1) {
                var str = day + "天" + hours + "小时" + minutes + "分" + s4 + "秒";
            } else if (day < 1) {
                var str = hours + "小时" + minutes + "分" + s4 + "秒";
            } else if (hours >= 1) {
                var str = minutes + "分" + s4 + "秒";
            } else {
                var str = s4 + "秒";
            }
            console.log('strstrstrstr',str)
            _this.time = str;
        }
    },
    methods:{ 

    } 
  }  
</script>