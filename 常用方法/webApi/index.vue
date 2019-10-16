<template>
    <!-- https://mp.weixin.qq.com/s/kJwUvbdMFQ5P74_Q1UfeTw -->
    <div>
            querySelector（元素向下查询，返回一个）
            querySelectorAll（元素向下查询，返回多个）
            closest（元素向上查询）
            dataset（获取元素以"data-"为前缀的属性集合）
            URLSearchParams（查询url参数）
            hidden（隐藏元素）
            contenteditable（使元素可以在页面上直接被编辑） 
            spellCheck（检查拼音）
            classList（类名控制器）
            getBoundingClientRect（元素空间结构详细信息）
            contains（判断是否包含指定元素）
            online state（网络状态）
            battery state（电池状态）
            vibration（设备震动）
            page visibility（页面可见性）
            deviceOrientation（陀螺仪）
            toDataUrl（画布内容转base64）
            customEvent（自定义事件）
            notification（桌面通知）
            fullScreen（全屏）    <!-- 会直接开启全屏，并且只显示指定的元素，元素的宽高填充了整个屏幕✅ -->
            orientation（屏幕方向）   
            geolocation
        <div>
            <p>
                - querySelector

                获取指定元素中匹配css选择器的元素：

                // 作用在document
                document.querySelector("#nav"); // 获取文档中id="nav"的元素
                document.querySelector(".nav"); // 获取文档中class="nav"的元素
                document.querySelector("#nav li:first-child"); // 获取文档中id="nav"下面的第一个li元素

                // 也可以作用在其他元素
                let nav = dodocument.querySelector("#nav");
                nav.querySelector("li"); // 如果有多个li的话，返回第一个li

                注意：无论如何只返回一个元素，如果有多个素，那也只返第一个✅        
            </p>
            <p>
                - querySelectorAll

                获取指定元素中匹配css选择器的所有元素：

                let list = document.querySelectorAll("li");  // NodeList(2) [li, li] 这里假设返回2个

                注意：返回的值是一个类数组，无法使用数组的原生方法（forEach、map等），需
                要转换一下：

                Array.from(list).map();                
            </p>
            <p>
                - dataset
                就跟原生微信小程序一样，能获取标签上以"data-"为前缀的属性集合：

                <!-- <p data-name="蜘蛛侠" data-age="16"></p> -->
                document.querySelector("p").dataset; // {name: "蜘蛛侠", age: "16"}

                注意：虽然可以用getAttribute方法获取任何属性值，但是性质却不一样，这是开发规范问题，凡是自定义属性都要加上data-前缀哦✅                
            </p>

            <p>
                - URLSearchParams
                假设浏览器的url参数是 "?name=蜘蛛侠&age=16"：

                new URLSearchParams(location.search).get("name"); // 蜘蛛侠                
            </p>
            <p>
                - hidden
                这是一个html属性，规定元素是否隐藏，表现跟css的display: none一致：

                <!-- <div hidden>我被隐藏了</div> -->
                document.querySelector("div").hidden = true / false;                
            </p>
            <p>
                - contenteditable
                可以使一个元素可以被用户编辑：
                
                <!-- <p contenteditable>我是P元素，但是我也可以被编辑</p>                 -->
            </p>
            <p>
                - classList
                这是一个对象，该对象里封装了许多操作元素类名的方法：

                <!-- <p class="title"></p> -->
                let elem = document.querySelector("p");

                // 增加类名
                elem.classList.add("title-new"); // "title title-new"

                // 删除类名
                elem.classList.remove("title"); // "title-new"

                // 切换类名（有则删、无则增，常用于一些切换操作，如显示/隐藏）
                elem.classList.toggle("title"); // "title-new title"

                // 替换类名
                elem.classList.replace("title", "title-old"); // "title-new title-old"

                // 是否包含指定类名
                elem.classList.contains("title"); // false                
            </p>
            <p>
                - getBoundingClientRect

                可以获取指定元素在当前页面的空间信息：

                elem.getBoundingClientRect();

                // 返回
                {
                x: 604.875,
                y: 1312,
                width: 701.625,
                height: 31,
                top: 1312,
                right: 1306.5,
                bottom: 1343,
                left: 604.875
                }

                注意：top是距离文档顶部的距离，y则是距离可视窗口（浏览器屏幕）的顶部距离，如果浏览器滚动，top值不变，y值会变                
            </p>
            <p>
                - contains
                可以判断指定元素是否包含了指定的子元素：

                <!-- <div>
                    <p></p>
                </div> -->
                document.querySelector("div").contains(document.querySelector("p")); // true                
            </p>
            <p>
                - online state
                监听当前的网络状态变动，然后执行对应的方法：

                window.addEventListener("online", xxx);

                window.addEventListener("offline", () => {
                    alert("你断网啦！");
                });           
                使用场景：提示用户已断网，直接一个弹框把用户吓懵✅     
            </p>
            <p>
                - battery state
                获取设备的电池状态：

                navigator.getBattery().then(battery => console.log(battery));

                // 返回
                {
                charging, // 是否在充电
                chargingTime, // 充满电所需时间
                dischargingTime, // 当前电量可使用时间
                level, 剩余电量

                onchargingchange, // 监听充电状态变化
                onchargingtimechange, // 监听充满电所需时间变化
                ondischargingtimechange, // 监听当前电量可使用时间变化
                onlevelchange // 监听电量变化
                }

                使用场景：提示用户电量已充满，或者为了让用户有安全感，电量低于99%的时候来个弹框提示"该充电啦"✅                
            </p>
            <p>
                - vibration
                使设备进行震动：

                // 震动一次
                navigator.vibrate(100);

                // 连续震动，震动200ms、暂停100ms、震动300ms
                navigator.vibrate([200, 100, 300]);

                效果如下：不好意思你得用你自己的手握住手机才能感受得到;
                使用场景：通过振动来提供感官反馈，比如太久没有触摸屏幕的时候连续震动提醒用户✅                
            </p>
            <p>
                - deviceOrientation
                陀螺仪，也就是设备的方向，又名重力感应，该API在IOS设备上失效的解决办法，将域名协议改成https；                
            </p>
            <p>
                - toDataURL

                这个canvas的API，作用是将画布的内容转换成一个base64的图片地址：

                let canvas = document.querySelector("canvas");
                let context = canvas.getContext("2d");

                // 画东西
                ...

                let url = canvas.toDataURL("image/png"); // 将画布内容转换成base64地址

                使用a标签进行图片下载时，图片链接跨域（图片是我的掘金头像），无法进行下载而是进行图片预览：

                <!-- <img src="xxx">

                <button>
                <a href="xxx" download="avatar">下载图片</a>
                </button>                 -->
                const downloadImage = (url, name) => {
                    // 实例化画布
                    let canvas = document.createElement("canvas");
                    let context = canvas.getContext("2d");

                    // 实例化一个图片对象
                    let image = new Image();
                    image.crossOrigin = "Anonymous";
                    image.src = url;

                    // 当图片加载完毕
                    image.onload = () => {
                        // 将图片画在画布上
                        canvas.height = image.height;
                        canvas.width = image.width;
                        context.drawImage(image, 0, 0);

                        // 将画布的内容转换成base64地址
                        let dataURL = canvas.toDataURL("image/png");

                        // 创建a标签模拟点击进行下载
                        let a = document.createElement("a");
                        a.hidden = true;
                        a.href = dataURL;
                        a.download = name;

                        document.body.appendChild(a);
                        a.click();
                    }
                }
                或者将当前的DOM转换成图片进行下载，常用于生成海报，推荐插件html2canvas，

            </p>
            <p>
                - notification

                PC端的桌面通知，如网页端的微信，当收到消息时，右下角会出现一个通知（尽管你把浏览器最小化），因为这个通知时独立于浏览器的，是系统的一个原生控件：

                const notice = new Notification("前端宇宙情报局", {
                body: "这20个不常用的Web API真的有用吗?，别问，问就是有用🈶",
                icon: "我的掘金头像",
                data: {
                    url: "https://www.baidu.com"
                }
                });

                // 点击回调
                notice.onclick = () => {
                    window.open(notice.data.url); // 当用户点击通知时，在浏览器打开百度网站                
                }
                注意：想要成功的调起通知，首先要用户的授权✅

                Notification.requestPermission(prem => {
                prem == "granted" // 同意
                prem == "denied" // 拒绝
                })

                所以，再调用之前先向用户发起请求：

                let permission = Notification.permission;

                if (permission == "granted") {
                    // 已同意，开始发送通知
                    ...
                } else if (permission == "denied") {
                    // 不同意，发不了咯
                } else {
                    // 其他状态，可以重新发送授权提示
                    Notification.requestPermission();
                }                                
            </p>
            <p>
                - orientation
                可以监听用户手机设备的旋转方向变化：

                window.addEventListener("orientationchange", () => {
                    <!-- document.body.innerHTML += `<p>屏幕旋转后的角度值：${window.orientation}</p>`; -->
                }, false);                
            </p>
            <p>
                geolocation 对象
                地理位置 API 通过 navigator.geolocation 提供。

                如果该对象存在，那么地理位置服务可用。    
                if ("geolocation" in navigator) {
                    /* 地理位置服务可用 */
                } else {
                    /* 地理位置服务不可用 */
                }                            
            </p>
        </div>     
    </div>
</template>