<template>
  
        <!-- <div class="videosamplex" style="width:500px;height:500px;margin: 0 auto">
            <video id="videoplayer" style="width:100%" :src="url"></video>
        </div> -->
        <div id="video"> </div>
</template>
<script>
export default {
    // props: ['url'],
    data() {
        return {
            
        }
    },
    mounted(){
        var videoObject = {
            // container: '.videosamplex',//“#”代表容器的ID，“.”或“”代表容器的class
            // variable: 'player',//该属性必需设置，值等于下面的new chplayer()的对象
            // poster:'pic/wdm.jpg',
            // mobileCkControls:true,//是否在移动端（包括ios）环境中显示控制栏
            // mobileAutoFull:false,//在移动端播放后是否按系统设置的全屏播放
            // h5container:'#videoplayer',//h5环境中使用自定义容器
            // video: this.url,//视频地址


            width: 1015, // 宽度，也可以支持百分比(不过父元素宽度要有)
            height: 574, // 高度，也可以支持百分比
            container: "#video", //“#”代表容器的ID，“.”或“”代表容器的class
            variable: "player", //该属性必需设置，值等于下面的new chplayer()的对象
            autoplay: true, //自动播放
            live: true,
            video: "" //视频地址(必填)            
            // video: 'rtmp://58.200.131.2:1935/livetv/hunantv'



        };
        videoObject.video = this.url;
        var player=new ckplayer(videoObject);
    },
    methods:{

    }
}
</script>
<style  scoped>

</style>

