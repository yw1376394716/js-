<template>
    <div>
        <!-- elementUi下拉框可搜索多个参数 -->
        <el-select v-model="demo" filterable placeholder="请选择"  :filter-method="dataFilter" clearable>
            <el-option
                v-for="item in demoList"
                :key="item.id"
                :value="item.id"   
                :label="item.name"                                                                                                           
                >
                <span style="float: right; color: #8492a6; font-size: 13px">{{ item.phone }}</span>
                <span style="float: left; color: #8492a6; font-size: 13px">{{ item.name }}</span>                         
            </el-option>
            
        </el-select>     
        <!--  -->
        <el-select v-model="demo" placeholder="请选择" @visible-change='changeFn($event,demo)'  >
            <el-option
                v-for="item in demoList"
                :key="item.id"
                :value="item.id"   
                :label="item.name"   >
            </el-option>
        </el-select>      



    </div>
</template>
<script>
export default {
    data() {
        return {
            demo:'',
            demoListCopy:[],
            demoList:[
                // {
                //     id:'',  // id
                //     name:'',// 名字
                //     phone:'',// 电话号码                  
                // }
            ],

        }
    },
    mounted() {
        
    },
    methods: {
        // 搜索多个参数
        dataFilter(val){
            this.demo = val;
            if (val) { //val存在                
                this.demoList = this.demoListCopy.filter((item) => {
                    // 添加手机号搜索条件
                    if (!!~item.phone.indexOf(val) || !!~item.phone.toUpperCase().indexOf(val.toUpperCase())) {
                        return true
                    }
                    // 添加名字搜索条件
                    if (!!~item.name.indexOf(val) || !!~item.name.toUpperCase().indexOf(val.toUpperCase())) {
                        return true
                    }                
                })
            } else { //val为空时，还原数组
                this.demoList = this.demoListCopy;
            }            
        },  
        
        // elementUI 下拉框隐藏时触发相关事件（下拉框下拉显示时不触发） 
        // visible-change会触发两次事件一次是显示时一次是关闭时。
        // 该方法可以避免下拉框点击事件在demoList数据改变后自动执行
        changeFn(cllback,val){
            if(!cllback && val != '' ){
                // .....
            }
        }
    },
}
</script>