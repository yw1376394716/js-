<template>
    <div>
        <h2>js 循环</h2>

        <p>for in </p>
        <p>for of </p>
    </div>
</template>
<script>
export default {
    data() {
        return {
            
        }
    },
    mounted() {
            var arr = ['a','s','f','g','h']
            // for in 
            for (const key in arr) {
                console.log(key)  // 0 1 2 3 4 
            }
            // for of
            for (const i of arr) {
                console.log(i)    // a s f g h
            }
    },
    methods: {
        





    },
}
</script>