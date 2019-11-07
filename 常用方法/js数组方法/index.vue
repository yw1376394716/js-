<template>
    <div>
        <h2>js数组方法</h2>

        <p>
            (1) concat()  该方法用于连接两个或多个数组。该方法不会改变现有的数组，仅会返回被连接数组的一个副本。
                例如： concatFn();
        </p>

        <p>
            (2) push() 该方法可向数组的末尾添加一个或多个元素，并返回新的长度。末尾添加，返回的是长度，会改变原数组。
                例如： pushFn();
        </p>   

        <p>
            (3) unshift() 该方法可向数组的开头添加一个或更多元素，并返回新的长度。返回新长度，改变原数组。
                例如： unshiftFn();
        </p>

        <p>
            (4) pop() 该方法用于删除并返回数组的最后一个元素。返回最后一个元素，会改变原数组。
            例如： popFn();
        </p>

        <p>
            (5) shift() 该方法用于把数组的第一个元素从其中删除，并返回第一个元素的值。返回第一个元素，改变原数组
            例如： shiftFn();
        </p>       

        <p>
            (6) slice() (数组截取) 返回一个新的数组，包含从 start 到 end （不包括该元素）的 arrayObject 中的元素。返回选定的元素，该方法不会修改原数组
            例如：sliceFn()
        </p> 

        <p>
            (7) filter  对数组的每一项都运行给定的函数，返回 结果为 ture 的项组成的数组。
        </p>
    </div>
</template>
<script>
export default {
    data() {
        return {
            
        }
    },
    mounted() {
        
    },
    methods: {
        //   合并数组
        concatFn(){
            var arr1 = [1,2,3];    
            var arr2 = [4,5];    
            var arr3 = arr1.concat(arr2);
            console.log(arr1);//[1, 2, 3]
            console.log(arr3);//[1, 2, 3, 4, 5]            
        },
        //  末尾添加元素
        pushFn(){
            var a = [2,3,4];    
            var b = a.push(5);
            console.log(a); //[2,3,4,5]
            console.log(b);//4
            // push方法可以一次添加多个元素push(data1,data2....)            
        },
        //  开头添加元素
        unshiftFn(){
            var arr = [2,3,4,5];
            console.log(arr.unshift(3,6)); //6
            console.log(arr); //[3, 6, 2, 3, 4, 5]            
        },
        //  删除最后一个元素
        popFn(){
            var arr = [2,3,4];
            console.log(arr.pop());//4
            console.log(arr); //[2,3]
        },
        //  删除第一个元素
        shiftFn(){
            var arr = [2,3,4];
            console.log(arr.shift()); //2
            console.log(arr);  //[3,4]
        },
        //  数组截取
        sliceFn(){
            // slice(start,end)
            // 参数:  start:开始位置的索引   end:结束位置的索引(但不包含该索引位置的元素)
            let  arr = [2,3,4,5];
            let newarr = arr.slice(0,3) // 不包含索引值为3的元素
            console.log(newarr);  // [2, 3, 4]

            let newarr2 = arr.slice(0)   // 如果没有第二个参数，截取到最后一位元素
            console.log(newarr2); // [2, 3, 4 ,5]
        },
        //  具有删除，插入，替换的功能
        spliceFn(){
            // 1:删除的功能 splice(index,count)
            // 参数:  index:开始位置的索引 count:要删除元素的个数
            // 返回:返回的是包含被删除元素的数组对象
            let  arr = ['a','b','c','d'];
            let  newarr = arr.splice(1,2);// 会删除b,c两个元素
            console.log(arr) // ['a', 'd'],
            console.log(newarr) // ["b", "c"]  返回的是被删除的元素组成的数组


            // 2:插入功能 splice(index,0,插入的项)
            // 参数 index:插入元素的索引值            
            let  arr = ['a','b','c','d'];
            let  newarr = arr.splice(2,0,'张三');   
            console.log(arr) // ["a", "b", "张三", "c", "d"] 
            
            // 3:替换功能 splice(index,num,value)
            // 参数:  index:开始的索引位置 num:删除项的数量(如果num为0，就是插入功能) value:插入的值
            // 返回:返回的是包含被删除的元素的数组对象     
                        
            let  arr = ['a','b','c','d'];
            let  newarr = arr.splice(1,2,'张三'); 
            console.log(arr)   // ["a", "张三", "d"]
            console.log(newarr) //  ["b", "c"]            

        },
        //  过滤数组
        filterFn(){
            let arr=[1,2,3,4,5,6];
            arr.filter(item=>{
                return item >3
            })   

            // 数组求交集
            let arr1=[1,2,3,4,5,6];
            let arr2=[11,2,13,4,15,6]
            arr1.filter(item => arr2.includes(item)) // [2, 4, 6]
            
            
        }
    },
}
</script>