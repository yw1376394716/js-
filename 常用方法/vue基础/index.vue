<template>
    <div>
        <p @click="demoFn()">{{demo}}</p>

        <p>$emit子传父</p>
        <!-- 
        //  父组件  （$emit子传父）
            <home @title="title">
            // 子组件
            this.$emit('title',[{title:'这是title'}]) 
        -->

        <p>$attrs 获取子传父中未在 props 定义的值</p>
        <!-- 
            // 父组件
            <home title="这是标题" width="80" height="80" imgUrl="imgUrl"/>

            // 子组件
            mounted() {
                console.log(this.$attrs) //{title: "这是标题", width: "80", height: "80", imgUrl: "imgUrl"}
            },
 
            相对应的如果子组件定义了 props,打印的值就是剔除定义的属性
            props: {
                width: {
                    type: String,
                    default: ''
                }
            },
            mounted() {
                console.log(this.$attrs) //{title: "这是标题", height: "80", imgUrl: "imgUrl"}
            },
        -->

        <p>$children   $parent</p>
        <!-- 
            //父组件
            mounted(){
                console.log(this.$children) 
                //可以拿到 一级子组件的属性和方法
                //所以就可以直接改变 data,或者调用 methods 方法
            }

            //子组件
            mounted(){
                console.log(this.$parent) //可以拿到 parent 的属性和方法
            } 
            
            // children和parent 并不保证顺序，也不是响应式的 只能拿到一级父组件和子组件
        -->
       
       <p> $refs </p>  
        <!-- 
            // 父组件
            <home ref="home"/>

            mounted(){
                console.log(this.$refs.home) //即可拿到子组件的实例,就可以直接操作 data 和 methods
                // this.$refs.home.子组件的方法
            } 
        -->

        <p>$nextTick</p>
        <!-- 
            mounted(){ //因为 mounted 阶段 dom 并未渲染完毕,所以需要$nextTick
                this.$nextTick(() => {
                    this.$refs.inputs.focus() //通过 $refs 获取dom 并绑定 focus 方法
                })
            }
        -->


        <p>$root </p>
        <!-- 
            // 父组件
            mounted(){
                console.log(this.$root) //获取根实例,最后所有组件都是挂载到根实例上
                console.log(this.$root.$children[0]) //获取根实例的一级子组件
                console.log(this.$root.$children[0].$children[0]) //获取根实例的二级子组件
            }         
        -->

        <p>$EventBus</p>
        <!-- 
            1.就是声明一个全局Vue实例变量 EventBus , 把所有的通信数据，事件监听都存储到这个变量上;
            2.类似于 Vuex。但这种方式只适用于极小的项目
            3.原理就是利用emit 并实例化一个全局 vue 实现数据共享
            // 在 main.js
            Vue.prototype.$eventBus=new Vue()

            // 传值组件
            this.$eventBus.$emit('eventTarget','这是eventTarget传过来的值')

            // 接收组件
            this.$eventBus.$on("eventTarget",v=>{
            console.log('eventTarget',v);//这是eventTarget传过来的值
            })
        -->


        <h3>路由传参</h3>
        <span>三种方案对比 方案二参数不会拼接在路由后面,页面刷新参数会丢失 方案一和三参数拼接在后面,丑,而且暴露了信息</span>

        <p>方案一</p>
        <!--             
            // 路由定义
            {
            path: '/describe/:id',
            name: 'Describe',
            component: Describe
            }
            // 页面传参
            this.$router.push({
            path: `/describe/${id}`,
            })
            // 页面获取
            this.$route.params.id
        -->

        <p>方案二</p>
        <!-- 
            // 路由定义
            {
            path: '/describe',
            name: 'Describe',
            omponent: Describe
            }
            // 页面传参
            this.$router.push({
                name: 'Describe',
                params: {
                    id: id
                }
            })
            // 页面获取
            this.$route.params.id
        -->

        <p>方案三</p>
        <!-- 
            // 路由定义
            {
            path: '/describe',
                name: 'Describe',
                component: Describe
            }
            // 页面传参
            this.$router.push({
                path: '/describe',
                    query: {
                    id: id
                }
            )
            // 页面获取
            this.$route.query.id
        -->

        <p>全局路由钩子router.beforeEach</p>
        <!-- 
            router.beforeEach((to, from, next) => {
                console.log('全局前置守卫：beforeEach -- next需要调用') //一般登录拦截用这个,也叫导航钩子守卫
                if (path === '/login') {
                    next()
                    return
                }
                if (token) {
                    next();
                } 
            }) 
        -->

        <p>$router</p>
        <!-- 
            this.$router.push()
            跳转到不同的url

            this.$router.go(1) 
            返回上一页
        -->

        <p>$route</p>
        <!-- 
            表示当前跳转的路由对象,属性有:
            name:路由名称
            path:路径
            query:传参接收值
            params:传参接收值
            fullPath:完成解析后的 URL，包含查询参数和 hash 的完整路径
            matched:路由记录副本
            redirectedFrom:如果存在重定向，即为重定向来源的路由的名字 

            this.$route.params.id:获取通过 params 或/:id传参的参数    // 参数不会拼接在路由后面,页面刷新参数会丢失
            this.$route.query.id:获取通过 query 传参的参数            
        -->



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