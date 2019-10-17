<template>
    <div>
        <p @click="demoFn()">{{demo}}</p>
    </div>
</template>
<script>
export default {
    data() {
        return {
            // 页面响应的数据都放在这里  
            demo:'vueDemo' 
        }
    },
  props:['父组件传来的值'],
  methods:  {
    //页面或组件定义的方法的集合
    demoFn(){
        console.log('.......')
    }
  },
  computed: {
    //计算属性(computed)与方法(methods) 类似，如果计算数据量比较大，建议放到这里
    //计算属性的结果会被缓存，除非依赖的响应式属性变化才会重新计算。
    //参考（https://cn.vuejs.org/v2/api/?#computed）
  },
  components:{
    // 局部组件注册的地方
    'component-a': ComponentA,
    'component-b': ComponentB
  },
  directives: {
    // 局部指令注册的地方
    focus: {
      // 指令的定义
      inserted: function (el,binding) {
        el.focus(); 
      }
    }
  },
  filters:{
    // 局部过滤器注册的地方
  },
  //生命周期钩子
  beforeCreate: function (){}, //在实例初始化之后，数据观测 (data observer) 和 event/watcher 事件配置之前被调用。
  created: function (){},//在实例创建完成后被立即调用。
  beforeMount: function (){},//在挂载开始之前被调用:相关的 render 函数首次被调用。
  mounted: function (){},//el 被新创建的 vm.$el 替换，并挂载到实例上去之后调用该钩子。
  beforeUpdate: function (){},//数据更新时调用，发生在虚拟 DOM 打补丁之前。
  updated: function (){},//由于数据更改导致的虚拟 DOM 重新渲染和打补丁，在这之后会调用该钩子。
  beforeDestroy: function (){},//实例销毁之前调用。在这一步，实例仍然完全可用。
  destroyed: function (){
    //Vue 实例销毁后调用。
    //调用后，Vue 实例指示的所有东西都会解绑定，所有的事件监听器会被移除，所有的子实例也会被销毁。
  },    
}
</script>