<template>
    <!-- 在index.html页面引入LodopFuncs.js文件 -->
    <div>
        <el-button  @click="printListFn(row)" type="primary" size="small"  >打印清单</el-button>
        <div id="print-box" class="print-box" style="width: 100%;background: red; display: none ">
            <div class="print" v-if="detail" style="width: 80%; font-size: 14px;margin: 0 auto;   ">
                <div class="title" style="text-align: center;">
                    <p style="font-weight:bolder;font-size: 16px;">{{detail.XXX}}</p>
                </div>
            </div>
        </div> 
    </div>
</template>
<script>
  export default {
    name: "name",
    data(){
        return {
            detail:null,
        }
    },
    mounted(){

    },
    methods:{   
        // 打印清单
        printListFn(row){
            console.log('打印清单',row)
            let LODOP;
            CreatePrintPage();
            LODOP.PREVIEW();
            console.log('确认打印..')
            function CreatePrintPage() {
                LODOP = getLodop();
                LODOP.PRINT_INIT("");
                let strBodyStyle="<style>*{margin: 0px;padding: 0px;font-size:13px;}</style>";
                let strFormHtml = strBodyStyle + document.getElementById("print-box").innerHTML;                    
                // let strFormHtml = document.getElementById("print-box").innerHTML;
                LODOP.SET_SHOW_MODE("HIDE_PAPER_BOARD ", true);
                LODOP.ADD_PRINT_HTM(0, 10, "100%", "100%", strFormHtml);
            }            
        }        
    } 
  }  
</script>