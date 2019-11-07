<template>
    <div>
        <p>时间倒计时(2021-09-25 02:02:02)</p>
        <span>{{time}}</span>

        <p>获取某月第一天与最后一天的日期</p>

        <p> 时间格式化</p>

        <p> 获取当前年月日时分秒 星期几</p>

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


    },
    methods:{ 
        fn1(){
            // 时间倒计时
            let _this = this;
            setInterval(() =>{
                timeFn('2019-12-25 02:02:02');
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
        fn2(){
            // 获取某月第一天与最后一天的日期
            function getMonthFirstLastDay(year,month){
                var firstDay=new Date(year,month-1,1);//这个月的第一天
                var currentMonth=firstDay.getMonth(); //取得月份数
                var lastDay=new Date(firstDay.getFullYear(),currentMonth+1,0);//是0而不是-1
                console.log('firstDay',firstDay,lastDay)
                firstDay=firstDay.Format("yyyy-MM-dd");//格式化
                lastDay=lastDay.Format("yyyy-MM-dd");//格式化
                console.log('firstDay',firstDay,lastDay)
                return [firstDay,lastDay];
                
            }
            // 时间格式化
            Date.prototype.Format = function (fmt) { //author: meizz 
                var o = {
                    "M+": this.getMonth() + 1, //月份 
                    "d+": this.getDate(), //日 
                    "h+": this.getHours(), //小时 
                    "m+": this.getMinutes(), //分 
                    "s+": this.getSeconds(), //秒 
                    "q+": Math.floor((this.getMonth() + 3) / 3), //季度 
                    "S": this.getMilliseconds() //毫秒 
                };
                if (/(y+)/.test(fmt)) fmt = fmt.replace(RegExp.$1, (this.getFullYear() + "").substr(4 - RegExp.$1.length));
                for (var k in o)
                if (new RegExp("(" + k + ")").test(fmt)) fmt = fmt.replace(RegExp.$1, (RegExp.$1.length == 1) ? (o[k]) : (("00" + o[k]).substr(("" + o[k]).length)));
                return fmt;
            }        
            getMonthFirstLastDay(2019,10);     // 年 月   
        },
        fn3(){
            // 时间格式化
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
        fn4(){
            var myDate = new Date();

            var myYear = myDate.getFullYear();  // 获取当前年份
            var myMonth = myDate.getMonth() +1; // 获取当前月份
            var myDay = myDate.getDate() // 获取当前日（1- 31）
            var myHours = myDate.getHours() // 获取当前小时(0-23)
            var myMinu = myDate.getMinutes() // 获取当前分钟(0-59)
            var mySec = myDate.getSeconds() // 获取当前秒数(0-59)
            var myWeek = myDate.getDay()  //获取当前星期几(0-6,0代表星期天)
           
        }
    } 
  }  
</script>