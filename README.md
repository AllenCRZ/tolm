<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>给最爱的老婆</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #ff9a9e 0%, #fad0c4 100%);
            margin: 0;
            padding: 0;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            color: #333;
            text-align: center;
        }
        
        .container {
            max-width: 800px;
            padding: 30px;
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            position: relative;
            overflow: hidden;
            margin: 20px 0;
        }
        
        h1 {
            color: #e74c3c;
            margin-bottom: 30px;
            font-size: 2.5rem;
        }
        
        .date-info {
            margin-bottom: 20px;
            font-size: 1.2rem;
            color: #7f8c8d;
        }
        
        .love-message {
            font-size: 1.5rem;
            line-height: 1.6;
            margin: 30px 0;
            padding: 20px;
            background-color: rgba(231, 76, 60, 0.1);
            border-radius: 10px;
            border-left: 5px solid #e74c3c;
        }
        
        .heart-btn {
            width: 80px;
            height: 80px;
            background-color: #e74c3c;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 30px auto;
            cursor: pointer;
            box-shadow: 0 5px 15px rgba(231, 76, 60, 0.4);
            transition: all 0.3s;
            position: relative;
            border: none;
            outline: none;
        }
        
        .heart-btn:hover {
            transform: scale(1.1);
            box-shadow: 0 8px 20px rgba(231, 76, 60, 0.6);
        }
        
        .heart-btn:active {
            transform: scale(0.95);
        }
        
        .heart-btn i {
            color: white;
            font-size: 40px;
        }
        
        .special-event {
            margin-top: 20px;
            padding: 10px;
            background-color: rgba(52, 152, 219, 0.1);
            border-radius: 10px;
            border-left: 5px solid #3498db;
            font-size: 1.2rem;
        }
        
        /* 彩带效果 - 减慢速度 */
        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            background-color: #f00;
            border-radius: 50%;
            pointer-events: none;
        }
        
        .surprise-message {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: rgba(255, 255, 255, 0.95);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            z-index: 100;
            display: none;
            max-width: 80%;
            text-align: center;
            animation: fadeIn 0.5s;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translate(-50%, -40%); }
            to { opacity: 1; transform: translate(-50%, -50%); }
        }
        
        .close-surprise {
            position: absolute;
            top: 10px;
            right: 15px;
            font-size: 24px;
            cursor: pointer;
            color: #7f8c8d;
        }
        
        .footer {
            margin-top: 30px;
            color: #7f8c8d;
            font-size: 0.9rem;
        }
        
        /* 心跳动画 */
        @keyframes heartbeat {
            0% { transform: scale(1); }
            25% { transform: scale(1.1); }
            50% { transform: scale(1); }
            75% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }
        
        .heartbeat {
            animation: heartbeat 1.5s infinite;
        }
        
        /* 新增样式 */
        .weather-recommendation {
            margin-top: 20px;
            padding: 15px;
            background-color: rgba(46, 204, 113, 0.1);
            border-radius: 10px;
            border-left: 5px solid #2ecc71;
            font-size: 1.1rem;
            text-align: left;
        }
        
        .calendar-container {
            width: 100%;
            margin-top: 30px;
            background-color: rgba(255, 255, 255, 0.8);
            border-radius: 10px;
            padding: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .calendar-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }
        
        .calendar-title {
            font-size: 1.2rem;
            color: #e74c3c;
        }
        
        .calendar-nav {
            display: flex;
            gap: 10px;
        }
        
        .calendar-nav button {
            background: none;
            border: none;
            font-size: 1.2rem;
            cursor: pointer;
            color: #7f8c8d;
        }
        
        .calendar-grid {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 5px;
        }
        
        .calendar-day-header {
            font-weight: bold;
            text-align: center;
            padding: 5px;
            color: #e74c3c;
        }
        
        .calendar-day {
            text-align: center;
            padding: 8px;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .calendar-day:hover {
            background-color: rgba(231, 76, 60, 0.1);
        }
        
        .calendar-day.today {
            background-color: #e74c3c;
            color: white;
            font-weight: bold;
        }
        
        .calendar-day.period-day {
            background-color: rgba(231, 76, 60, 0.3);
            position: relative;
        }
        
        .calendar-day.period-day::after {
            content: '♥';
            position: absolute;
            bottom: 2px;
            right: 2px;
            font-size: 10px;
            color: #e74c3c;
        }
        
        .calendar-day.other-month {
            color: #ccc;
        }
        
        .water-reminder {
            margin-top: 20px;
            padding: 15px;
            background-color: rgba(52, 152, 219, 0.1);
            border-radius: 10px;
            border-left: 5px solid #3498db;
            font-size: 1.1rem;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        
        .water-btn {
            background-color: #3498db;
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            font-size: 1.2rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .period-tracker {
            margin-top: 20px;
            padding: 15px;
            background-color: rgba(155, 89, 182, 0.1);
            border-radius: 10px;
            border-left: 5px solid #9b59b6;
            font-size: 1.1rem;
        }
        
        .period-controls {
            display: flex;
            gap: 10px;
            margin-top: 10px;
            justify-content: center;
        }
        
        .period-btn {
            padding: 8px 15px;
            border: none;
            border-radius: 5px;
            background-color: #9b59b6;
            color: white;
            cursor: pointer;
            font-size: 0.9rem;
        }
        
        .period-info {
            margin-top: 10px;
            font-size: 0.9rem;
            color: #7f8c8d;
        }
        
        .hidden {
            display: none;
        }
        
        /* 新增运动提醒 */
        .exercise-reminder {
            margin-top: 20px;
            padding: 15px;
            background-color: rgba(241, 196, 15, 0.1);
            border-radius: 10px;
            border-left: 5px solid #f1c40f;
            font-size: 1.1rem;
            text-align: left;
        }
        
        /* 惊喜消息样式加强 */
        #surprise-title {
            font-size: 2rem;
            font-weight: bold;
            color: #e74c3c;
            margin-bottom: 20px;
        }
        
        #surprise-content {
            font-size: 1.5rem;
            font-weight: bold;
            color: #3498db;
            line-height: 1.5;
        }
        
        .surprise-footer {
            margin-top: 20px;
            font-size: 1rem;
            color: #7f8c8d;
        }
    </style>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css">
</head>
<body>
    <div class="container">
        <h1>亲爱的老婆 <i class="fas fa-heart" style="color: #e74c3c;"></i></h1>
        
        <div class="date-info">
            <p id="current-date">今天是2023年1月1日，星期X</p>
            <p id="solar-term">节气：XX</p>
            <p id="festival">节日：XX</p>
            <p id="weather-info">天气：加载中...</p>
        </div>
        
        <div class="love-message" id="daily-message">
            今天的情话加载中...
        </div>
        
        <div class="special-event" id="special-message" style="display: none;">
            <!-- 特别节日/节气情话 -->
        </div>
        
        <div class="weather-recommendation" id="weather-recommendation">
            <p><i class="fas fa-tshirt"></i> 今日穿搭推荐：加载中...</p>
        </div>
        
        <div class="exercise-reminder" id="exercise-reminder">
            <p><i class="fas fa-running"></i> 今日运动提醒：每天坚持30分钟运动，健康又美丽！</p>
        </div>
        
        <button class="heart-btn heartbeat" id="heart-btn">
            <i class="fas fa-heart"></i>
        </button>
        
        <div class="water-reminder" id="water-reminder">
            <div>
                <i class="fas fa-glass-whiskey"></i> 今日喝水提醒：你已经喝了 <span id="water-count">0</span> 杯水
            </div>
            <button class="water-btn" id="water-btn">+</button>
        </div>
        
        <div class="period-tracker">
            <div><i class="fas fa-heartbeat"></i> 生理期记录</div>
            <div class="period-controls">
                <button class="period-btn" id="period-start-btn">开始日</button>
                <button class="period-btn" id="period-end-btn">结束日</button>
            </div>
            <div class="period-info" id="period-info">
                上次记录：无
            </div>
        </div>
        
        <div class="calendar-container">
            <div class="calendar-header">
                <div class="calendar-title" id="calendar-title">2023年1月</div>
                <div class="calendar-nav">
                    <button id="calendar-prev"><i class="fas fa-chevron-left"></i></button>
                    <button id="calendar-next"><i class="fas fa-chevron-right"></i></button>
                </div>
            </div>
            <div class="calendar-grid" id="calendar-grid">
                <!-- 日历将通过JavaScript动态生成 -->
            </div>
        </div>
        
        <div class="footer">
            <p>每一天都比昨天更爱你 ❤️</p>
        </div>
    </div>
    
    <div class="surprise-message" id="surprise-message">
        <span class="close-surprise" id="close-surprise">&times;</span>
        <h2 id="surprise-title">惊喜!</h2>
        <p id="surprise-content">今天也是爱你的一天!</p>
        <p class="surprise-footer" id="surprise-footer"></p>
    </div>
    
    <script>
        // 全新优化的随机顺序情话库（土味+暖心+幽默混合）
        const loveMessages = [
            "你是黄赤交角，我是蓝色星球，我的冷暖变化由你决定。",
            "我想和你一起逛超市，因为想和你柴米油盐。",
            "我最近想买块地，你的死心塌地。",
            "你是我面包上的黄油，生命里的呼吸。",
            "我这个人很害羞的，不信你问我，我都不敢说我喜欢你。",
            "今天也想见到你，不管什么天气。",
            "你知道你和手机的区别吗？手机可以充电，你让我电力十足。",
            "你是我所有温柔的具象化，是我所有诗意的来源。",
            "我最近在练习微笑，因为想给你最灿烂的笑容。",
            "和你在一起的时光都很耀眼，因为天气好，因为天气不好，因为天气刚刚好。",
            "你知道我想喝什么吗？呵护你。",
            "你是我疲惫生活中的英雄梦想。",
            "我最近在学做饭，因为想把你养得白白胖胖。",
            "世界很暗，然后你来了，带着星星和月亮。",
            "你猜我想吃什么？痴痴地望着你。",
            "我想把攒了好多年的温柔都给你。",
            "我最近在练习跳舞，因为想在婚礼上和你跳第一支舞。",
            "你是我所有的不矜持，不理智，不安分。",
            "你知道你和星星的区别吗？星星在天上，你在我心里。",
            "你是我电量只剩1%也想回消息的人。",
            "我怀疑你的本质是一本书，不然为什么让我越看越想睡。",
            "你是我愿意跑遍整个城市去见的人。",
            "我最近在练习摄影，因为想记录你最美的样子。",
            "你是我洗澡时擦擦手也要回复的人。",
            "你知道我的缺点是什么吗？缺点你。",
            "你是我失眠到凌晨三点也不舍得敷衍的人。",
            "我最近在练字，因为想亲手写我们的结婚请柬。",
            "你是我愿意把冰淇淋第一口让给你的人。",
            "我最近手头有点紧，能借你的手牵牵吗？",
            "你是我愿意把最后一块巧克力留给的人。",
            "你上辈子一定是碳酸饮料吧，为什么我一看到你就开心得冒泡。",
            "你是我的文艺复兴，带我走出黑暗，给我新的信仰和救赎。",
            "我最近在存钱，因为想给你一个完美的未来。",
            "你是我字典里所有褒义词的集合，胜过一切美好事物的总和。",
            "我最近在学画画，因为想把你画进我未来的蓝图里。",
            "你是我所有灵感的缪斯，是我所有创作的源泉。",
            "我这个人很专一的，比如我吃火锅就只吃一种菜——你这个小菜。",
            "你是我所有坚持的理由，是我所有努力的终点。",
            "我最近要换个座右铭：近朱者赤，近你者甜。",
            "你是我所有梦想的起点，是我所有未来的终点。",
            "我最近在练习举重，因为想举起你在我心里的分量。",
            "你是我所有快乐的源泉，是我所有幸福的归宿。",
            "如果人类有尾巴，和你在一起我会忍不住摇起来。",
            "你是我所有勇气的来源，是我所有坚强的后盾。",
            "我想和你一起生活，在某个小镇，共享无尽的黄昏和绵绵不绝的钟声。",
            "你是北大西洋暖流，我是摩尔曼斯克港，因为你的到来，我的世界成了不冻港。",
            "你是我所有诗篇的第一行和最后一行。",
            "你是我想要反复阅读的那本书，每次都有新发现。",
            "你是我想要单曲循环的那首歌，永远听不腻。",
            "你是我想要永远收藏的那幅画，越看越喜欢。",
            "你是我想要永远珍藏的那瓶酒，越陈越香。",
            "你是我想要永远守护的那朵花，越开越美。",
            "你是我想要永远追随的那颗星，越追越近。",
            "我想和你一起做饭，因为想和你共享人间烟火。",
            "我想和你一起洗碗，因为想和你分担生活琐碎。",
            "我想和你一起散步，因为想和你慢慢变老。",
            "我想和你一起看剧，因为想和你共享休闲时光。",
            "我想和你一起发呆，因为想和你虚度时光。",
            "我想和你一起淋雨，因为想和你一起疯狂。",
            "我想和你一起晒太阳，因为想和你一起慵懒。",
            "我想和你一起数星星，因为想和你一起浪漫。",
            "我想和你一起等日出，因为想和你一起期待。",
            "你知道你和猴子的区别吗？猴子住在树上，你住在我心里。",
            "我最近学会了一门新手艺，把心门钥匙交给你保管。",
            "你知道你和地图的区别吗？地图上有千万条路，而我只想走向你。",
            "我最近想换个造型，变成你喜欢的模样。"
        ];

        // 节气情话
        const solarTermMessages = {
            "立春": "立春了，万物复苏，而我对你的爱也在不断生长。",
            "雨水": "雨水滋润大地，而你滋润我的心田。",
            "惊蛰": "惊蛰雷动，不如你一笑让我心动。",
            "春分": "春分昼夜平分，而我愿把全部时间都分给你。",
            "清明": "清明时节雨纷纷，而我对你的思念更深沉。",
            "谷雨": "谷雨播种希望，而你播种了我全部的爱。",
            "立夏": "立夏了，天气渐热，而我对你的热情更甚。",
            "小满": "小满未满，而我对你的爱已经满溢。",
            "芒种": "芒种忙种，而我忙着爱你。",
            "夏至": "夏至日最长，而我对你的思念更长。",
            "小暑": "小暑炎热，而我对你的爱更热烈。",
            "大暑": "大暑最热，而你是我最热的爱恋。",
            "立秋": "立秋了，暑气渐消，而我对你的爱丝毫不减。",
            "处暑": "处暑暑气止，而我对你的爱永不止息。",
            "白露": "白露凝霜，而我的心里装满了你。",
            "秋分": "秋分昼夜均，而我愿与你平分秋色。",
            "寒露": "寒露渐冷，而你的温暖让我心热。",
            "霜降": "霜降天寒，而你的拥抱最温暖。",
            "立冬": "立冬了，万物收藏，而我想把你收藏在心里。",
            "小雪": "小雪飘飘，而我对你的爱纷纷扬扬。",
            "大雪": "大雪纷飞，而我对你的爱铺天盖地。",
            "冬至": "冬至夜最长，而我对你的思念更长。",
            "小寒": "小寒冷冽，而你的笑容最温暖。",
            "大寒": "大寒最冷，而你是我最暖的依靠。"
        };
        
        // 节日情话
        const festivalMessages = {
            "元旦": "新年第一天，第一个想到的就是你，元旦快乐我的爱！",
            "情人节": "情人节快乐！你是我今生唯一的情人，也是永远的挚爱。",
            "妇女节": "女神节快乐！在我心中你永远是最美的女神。",
            "劳动节": "劳动节快乐！感谢你为这个家付出的一切，辛苦了亲爱的。",
            "儿童节": "儿童节快乐我的小宝贝！在我心里你永远是需要我呵护的小朋友。",
            "七夕": "七夕快乐！牛郎织女一年一见，而我们天天相见更幸福。",
            "中秋节": "中秋月圆人团圆，而我最想团圆的人就是你。",
            "国庆节": "国庆节快乐！和你在一起的每一天都值得庆祝。",
            "圣诞节": "圣诞快乐！你就是我今年最想要的礼物。",
            "生日": "生日快乐我的爱！你出生的那天就是我最感恩的日子。",
            "结婚纪念日": "结婚纪念日快乐！每一天都比昨天更爱你。",
            "相识纪念日": "还记得我们相识的那天吗？那是我生命中最美好的一天。"
        };
        
        // 天气穿搭推荐
        const weatherRecommendations = {
            "晴天": {
                "高温": "今天阳光明媚，建议穿轻薄透气的衣物，别忘了涂防晒霜和戴太阳镜哦！",
                "适中": "天气晴朗舒适，适合穿轻便的长袖或薄外套，享受户外活动吧！",
                "低温": "虽然阳光很好，但气温较低，建议穿保暖的衣物，可以搭配一件漂亮的围巾。"
            },
            "阴天": {
                "高温": "虽然是阴天但气温不低，穿短袖或薄长袖都可以，带把伞以防下雨。",
                "适中": "阴天微凉，建议穿长袖衬衫或薄毛衣，搭配一件轻便外套。",
                "低温": "阴天加上低温，记得穿保暖的毛衣和外套，保持温暖最重要。"
            },
            "雨天": {
                "高温": "下雨天气闷热，穿防水材质的轻薄衣物，别忘了带雨伞或雨衣。",
                "适中": "雨天微凉，建议穿防水外套和防滑鞋，保持干爽很重要。",
                "低温": "雨天寒冷，穿保暖的防水外套和靴子，可以喝点热饮驱寒。"
            },
            "雪天": {
                "高温": "下雪但不冷，穿保暖的防水外套和靴子，注意防滑。",
                "适中": "雪天寒冷，建议穿羽绒服、厚毛衣和保暖靴，戴手套和围巾。",
                "低温": "严寒雪天，一定要穿最保暖的衣物，多层穿搭最有效，尽量减少外出。"
            },
            "雾天": {
                "高温": "雾气弥漫但温度不低，穿轻便透气的衣物，注意交通安全。",
                "适中": "雾天微凉，建议穿长袖和轻便外套，选择亮色衣物增加可见度。",
                "低温": "雾天寒冷，穿保暖的衣物，特别是高领毛衣和厚外套。"
            }
        };
        
        // 获取当前日期信息
        function getCurrentDate() {
            const now = new Date();
            const year = now.getFullYear();
            const month = now.getMonth() + 1;
            const day = now.getDate();
            const weekdays = ["日", "一", "二", "三", "四", "五", "六"];
            const weekday = weekdays[now.getDay()];
            
            return {
                year,
                month,
                day,
                weekday,
                dateStr: `${year}年${month}月${day}日，星期${weekday}`,
                dayOfYear: Math.floor((now - new Date(year, 0, 0)) / (1000 * 60 * 60 * 24)),
                dateObj: now
            };
        }
        
        // 获取节气信息（简化版，实际节气计算复杂）
        function getSolarTerm(date) {
            // 这里是一个简化的节气判断，实际节气计算需要精确的天文计算
            const terms = [
                {name: "小寒", month: 1, day: 5},
                {name: "大寒", month: 1, day: 20},
                {name: "立春", month: 2, day: 4},
                {name: "雨水", month: 2, day: 19},
                {name: "惊蛰", month: 3, day: 5},
                {name: "春分", month: 3, day: 20},
                {name: "清明", month: 4, day: 4},
                {name: "谷雨", month: 4, day: 20},
                {name: "立夏", month: 5, day: 5},
                {name: "小满", month: 5, day: 21},
                {name: "芒种", month: 6, day: 6},
                {name: "夏至", month: 6, day: 21},
                {name: "小暑", month: 7, day: 7},
                {name: "大暑", month: 7, day: 23},
                {name: "立秋", month: 8, day: 7},
                {name: "处暑", month: 8, day: 23},
                {name: "白露", month: 9, day: 7},
                {name: "秋分", month: 9, day: 23},
                {name: "寒露", month: 10, day: 8},
                {name: "霜降", month: 10, day: 23},
                {name: "立冬", month: 11, day: 7},
                {name: "小雪", month: 11, day: 22},
                {name: "大雪", month: 12, day: 7},
                {name: "冬至", month: 12, day: 22}
            ];
            
            for (const term of terms) {
                if (date.month === term.month && date.day === term.day) {
                    return term.name;
                }
            }
            
            return null;
        }
        
        // 获取节日信息（简化版）
        function getFestival(date) {
            const festivals = [
                {name: "元旦", month: 1, day: 1},
                {name: "情人节", month: 2, day: 14},
                {name: "妇女节", month: 3, day: 8},
                {name: "劳动节", month: 5, day: 1},
                {name: "儿童节", month: 6, day: 1},
                {name: "七夕", month: 8, day: 25}, // 七夕日期每年不同，这里简化
                {name: "中秋节", month: 9, day: 21}, // 中秋节日期每年不同，这里简化
                {name: "国庆节", month: 10, day: 1},
                {name: "圣诞节", month: 12, day: 25},
                {name: "生日", month: 4, day: 15}, // 示例生日，请替换为实际生日
                {name: "结婚纪念日", month: 6, day: 18}, // 示例纪念日，请替换为实际日期
                {name: "相识纪念日", month: 3, day: 12} // 示例纪念日，请替换为实际日期
            ];
            
            for (const festival of festivals) {
                if (date.month === festival.month && date.day === festival.day) {
                    return festival.name;
                }
            }
            
            return null;
        }
        
        // 获取每日情话（基于日期确保每天不同）
        function getDailyLoveMessage(date) {
            // 使用日期作为种子确保每天相同
            const seed = date.year * 10000 + date.month * 100 + date.day;
            const index = seed % loveMessages.length;
            return loveMessages[index];
        }
        
        // 模拟获取天气信息
        function getWeatherInfo(date) {
            // 这里应该是调用天气API，为了示例我们模拟一些天气数据
            const weatherTypes = ["晴天", "阴天", "雨天", "雪天", "雾天"];
            const tempLevels = ["高温", "适中", "低温"];
            
            // 根据月份模拟季节天气
            let weatherType, tempLevel;
            
            if (date.month >= 3 && date.month <= 5) { // 春季
                weatherType = Math.random() > 0.7 ? "雨天" : (Math.random() > 0.5 ? "阴天" : "晴天");
                tempLevel = Math.random() > 0.7 ? "高温" : (Math.random() > 0.3 ? "适中" : "低温");
            } else if (date.month >= 6 && date.month <= 8) { // 夏季
                weatherType = Math.random() > 0.8 ? "雨天" : "晴天";
                tempLevel = Math.random() > 0.6 ? "高温" : "适中";
            } else if (date.month >= 9 && date.month <= 11) { // 秋季
                weatherType = Math.random() > 0.6 ? "晴天" : (Math.random() > 0.3 ? "阴天" : "雨天");
                tempLevel = Math.random() > 0.7 ? "适中" : (Math.random() > 0.3 ? "高温" : "低温");
            } else { // 冬季
                weatherType = Math.random() > 0.7 ? "雪天" : (Math.random() > 0.5 ? "晴天" : "阴天");
                tempLevel = Math.random() > 0.8 ? "适中" : "低温";
            }
            
            return {
                type: weatherType,
                temp: tempLevel,
                description: `${weatherType}，${tempLevel.replace("高温", "气温较高").replace("适中", "气温适宜").replace("低温", "气温较低")}`
            };
        }
        
        // 获取穿搭推荐
        function getDressRecommendation(weather) {
            const recommendation = weatherRecommendations[weather.type]?.[weather.temp] || 
                                 "根据当前天气，建议穿着舒适的衣物，注意保暖和防晒。";
            return recommendation;
        }
        
        // 创建彩带效果 - 减慢速度并增加数量
        function createConfetti() {
            const colors = ['#e74c3c', '#3498db', '#2ecc71', '#f1c40f', '#9b59b6', '#1abc9c'];
            
            for (let i = 0; i < 200; i++) { // 数量增加2倍
                const confetti = document.createElement('div');
                confetti.className = 'confetti';
                confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                confetti.style.left = Math.random() * 100 + 'vw';
                confetti.style.top = -10 + 'px';
                confetti.style.width = Math.random() * 10 + 5 + 'px';
                confetti.style.height = Math.random() * 10 + 5 + 'px';
                
                document.body.appendChild(confetti);
                
                // 动画 - 减慢速度
                const animation = confetti.animate([
                    { top: '-10px', opacity: 1, transform: 'rotate(0deg)' },
                    { top: '100vh', opacity: 0, transform: 'rotate(' + (Math.random() * 360) + 'deg)' }
                ], {
                    duration: Math.random() * 5000 + 3000, // 减慢速度
                    easing: 'cubic-bezier(0.1, 0.8, 0.3, 1)'
                });
                
                animation.onfinish = () => {
                    confetti.remove();
                };
            }
        }
        
        // 显示惊喜消息
        function showSurpriseMessage() {
            const today = new Date().toDateString();
            const lastSurpriseDate = localStorage.getItem('lastSurpriseDate');
            
            if (lastSurpriseDate === today) {
                document.getElementById('surprise-content').textContent = "今天的惊喜已经看过了，明天再来看看吧！";
                document.getElementById('surprise-title').textContent = "耐心等待";
                document.getElementById('surprise-footer').textContent = "";
            } else {
                const surpriseMessages = [
                    "你是我的今天和所有的明天",
                    "遇见你是我这辈子最幸运的事",
                    "我想和你一起慢慢变老",
                    "你是我生命中最美的风景",
                    "有你的地方就是家",
                    "爱你是我做过最正确的事",
                    "你是我每天早上醒来的理由",
                    "我的世界因你而完整",
                    "你是我今生唯一的挚爱",
                    "和你在一起的每一秒都值得珍惜"
                ];
                
                const randomMessage = surpriseMessages[Math.floor(Math.random() * surpriseMessages.length)];
                document.getElementById('surprise-content').textContent = randomMessage;
                document.getElementById('surprise-title').textContent = "惊喜!";
                document.getElementById('surprise-footer').textContent = "记得明天再来看看新的惊喜哦！";
                localStorage.setItem('lastSurpriseDate', today);
            }
            
            document.getElementById('surprise-message').style.display = 'block';
        }
        
        // 日历功能
        class LoveCalendar {
            constructor() {
                this.currentDate = new Date();
                this.periodDays = JSON.parse(localStorage.getItem('periodDays')) || [];
                this.renderCalendar();
            }
            
            renderCalendar() {
                const year = this.currentDate.getFullYear();
                const month = this.currentDate.getMonth();
                
                document.getElementById('calendar-title').textContent = `${year}年${month + 1}月`;
                
                const firstDay = new Date(year, month, 1);
                const lastDay = new Date(year, month + 1, 0);
                const daysInMonth = lastDay.getDate();
                const startingDay = firstDay.getDay();
                
                const calendarGrid = document.getElementById('calendar-grid');
                calendarGrid.innerHTML = '';
                
                // 添加星期标题
                const weekdays = ['日', '一', '二', '三', '四', '五', '六'];
                weekdays.forEach(day => {
                    const dayHeader = document.createElement('div');
                    dayHeader.className = 'calendar-day-header';
                    dayHeader.textContent = day;
                    calendarGrid.appendChild(dayHeader);
                });
                
                // 添加上个月的日期
                const prevMonthLastDay = new Date(year, month, 0).getDate();
                for (let i = 0; i < startingDay; i++) {
                    const dayElement = document.createElement('div');
                    dayElement.className = 'calendar-day other-month';
                    dayElement.textContent = prevMonthLastDay - startingDay + i + 1;
                    calendarGrid.appendChild(dayElement);
                }
                
                // 添加当前月的日期
                const today = new Date();
                for (let i = 1; i <= daysInMonth; i++) {
                    const dayElement = document.createElement('div');
                    dayElement.className = 'calendar-day';
                    dayElement.textContent = i;
                    
                    // 检查是否是今天
                    if (year === today.getFullYear() && month === today.getMonth() && i === today.getDate()) {
                        dayElement.classList.add('today');
                    }
                    
                    // 检查是否是生理期
                    const dateStr = `${year}-${month + 1}-${i}`;
                    if (this.periodDays.includes(dateStr)) {
                        dayElement.classList.add('period-day');
                    }
                    
                    dayElement.addEventListener('click', () => this.togglePeriodDay(year, month + 1, i));
                    calendarGrid.appendChild(dayElement);
                }
                
                // 添加下个月的日期
                const totalCells = startingDay + daysInMonth;
                const remainingCells = totalCells <= 35 ? 35 - totalCells : 42 - totalCells;
                
                for (let i = 1; i <= remainingCells; i++) {
                    const dayElement = document.createElement('div');
                    dayElement.className = 'calendar-day other-month';
                    dayElement.textContent = i;
                    calendarGrid.appendChild(dayElement);
                }
            }
            
            togglePeriodDay(year, month, day) {
                const dateStr = `${year}-${month}-${day}`;
                const index = this.periodDays.indexOf(dateStr);
                
                if (index === -1) {
                    this.periodDays.push(dateStr);
                } else {
                    this.periodDays.splice(index, 1);
                }
                
                localStorage.setItem('periodDays', JSON.stringify(this.periodDays));
                this.renderCalendar();
                
                // 更新生理期信息显示
                this.updatePeriodInfo();
            }
            
            prevMonth() {
                this.currentDate.setMonth(this.currentDate.getMonth() - 1);
                this.renderCalendar();
            }
            
            nextMonth() {
                this.currentDate.setMonth(this.currentDate.getMonth() + 1);
                this.renderCalendar();
            }
            
            updatePeriodInfo() {
                if (this.periodDays.length === 0) {
                    document.getElementById('period-info').textContent = "上次记录：无";
                    return;
                }
                
                // 按日期排序
                const sortedDates = this.periodDays.sort((a, b) => new Date(a) - new Date(b));
                const lastDate = sortedDates[sortedDates.length - 1];
                
                // 计算连续天数
                let consecutiveDays = 1;
                for (let i = sortedDates.length - 2; i >= 0; i--) {
                    const currentDate = new Date(sortedDates[i]);
                    const nextDate = new Date(sortedDates[i + 1]);
                    
                    // 检查是否是连续的天数
                    const diffTime = nextDate - currentDate;
                    const diffDays = diffTime / (1000 * 60 * 60 * 24);
                    
                    if (diffDays === 1) {
                        consecutiveDays++;
                    } else {
                        break;
                    }
                }
                
                const formattedDate = lastDate.split('-').join('/');
                document.getElementById('period-info').textContent = 
                    `上次记录：${formattedDate}，持续${consecutiveDays}天`;
            }
            
            markPeriodStart() {
                const today = new Date();
                const dateStr = `${today.getFullYear()}-${today.getMonth() + 1}-${today.getDate()}`;
                
                if (!this.periodDays.includes(dateStr)) {
                    this.periodDays.push(dateStr);
                    localStorage.setItem('periodDays', JSON.stringify(this.periodDays));
                    this.renderCalendar();
                    this.updatePeriodInfo();
                    alert("已记录生理期开始日");
                } else {
                    alert("今天已经标记为生理期");
                }
            }
            
            markPeriodEnd() {
                const today = new Date();
                const dateStr = `${today.getFullYear()}-${today.getMonth() + 1}-${today.getDate()}`;
                
                if (this.periodDays.includes(dateStr)) {
                    // 找到所有连续日期
                    const sortedDates = this.periodDays.sort((a, b) => new Date(a) - new Date(b));
                    const periodBlocks = [];
                    let currentBlock = [];
                    
                    for (let i = 0; i < sortedDates.length; i++) {
                        if (currentBlock.length === 0) {
                            currentBlock.push(sortedDates[i]);
                        } else {
                            const prevDate = new Date(currentBlock[currentBlock.length - 1]);
                            const currDate = new Date(sortedDates[i]);
                            const diffDays = (currDate - prevDate) / (1000 * 60 * 60 * 24);
                            
                            if (diffDays === 1) {
                                currentBlock.push(sortedDates[i]);
                            } else {
                                periodBlocks.push([...currentBlock]);
                                currentBlock = [sortedDates[i]];
                            }
                        }
                    }
                    
                    if (currentBlock.length > 0) {
                        periodBlocks.push([...currentBlock]);
                    }
                    
                    // 找到包含今天的区块
                    const currentBlockIndex = periodBlocks.findIndex(block => block.includes(dateStr));
                    if (currentBlockIndex !== -1) {
                        // 计算周期长度
                        const periodLength = periodBlocks[currentBlockIndex].length;
                        alert(`已记录生理期结束，本次持续${periodLength}天`);
                    }
                } else {
                    alert("今天不是生理期，无需标记结束");
                }
            }
        }
        
        // 初始化页面
        function initPage() {
            const date = getCurrentDate();
            
            // 显示日期信息
            document.getElementById('current-date').textContent = date.dateStr;
            
            // 获取并显示节气
            const solarTerm = getSolarTerm(date);
            if (solarTerm) {
                document.getElementById('solar-term').textContent = `节气：${solarTerm}`;
                document.getElementById('special-message').textContent = solarTermMessages[solarTerm];
                document.getElementById('special-message').style.display = 'block';
            } else {
                document.getElementById('solar-term').textContent = '';
            }
            
            // 获取并显示节日
            const festival = getFestival(date);
            if (festival) {
                document.getElementById('festival').textContent = `节日：${festival}`;
                if (!solarTerm) { // 如果当天不是节气才显示节日情话
                    document.getElementById('special-message').textContent = festivalMessages[festival];
                    document.getElementById('special-message').style.display = 'block';
                }
            } else {
                document.getElementById('festival').textContent = '';
            }
            
            // 获取并显示天气信息
            const weather = getWeatherInfo(date);
            document.getElementById('weather-info').textContent = `天气：${weather.description}`;
            
            // 获取并显示穿搭推荐
            const dressRecommendation = getDressRecommendation(weather);
            document.getElementById('weather-recommendation').innerHTML = 
                `<p><i class="fas fa-tshirt"></i> 今日穿搭推荐：${dressRecommendation}</p>`;
            
            // 显示每日情话
            document.getElementById('daily-message').textContent = getDailyLoveMessage(date);
            
            // 初始化日历
            const loveCalendar = new LoveCalendar();
            
            // 初始化喝水计数器
            let waterCount = parseInt(localStorage.getItem('waterCount')) || 0;
            document.getElementById('water-count').textContent = waterCount;
            
            // 爱心按钮事件
            document.getElementById('heart-btn').addEventListener('click', function() {
                createConfetti();
                showSurpriseMessage();
            });
            
            // 关闭惊喜消息
            document.getElementById('close-surprise').addEventListener('click', function() {
                document.getElementById('surprise-message').style.display = 'none';
            });
            
            // 喝水按钮事件
            document.getElementById('water-btn').addEventListener('click', function() {
                waterCount++;
                document.getElementById('water-count').textContent = waterCount;
                localStorage.setItem('waterCount', waterCount);
                
                if (waterCount % 8 === 0) {
                    alert("今天已经喝了8杯水，很棒哦！继续保持～");
                }
            });
            
            // 日历导航按钮
            document.getElementById('calendar-prev').addEventListener('click', function() {
                loveCalendar.prevMonth();
            });
            
            document.getElementById('calendar-next').addEventListener('click', function() {
                loveCalendar.nextMonth();
            });
            
            // 生理期记录按钮
            document.getElementById('period-start-btn').addEventListener('click', function() {
                loveCalendar.markPeriodStart();
            });
            
            document.getElementById('period-end-btn').addEventListener('click', function() {
                loveCalendar.markPeriodEnd();
            });
            
            // 更新生理期信息显示
            loveCalendar.updatePeriodInfo();
            
            // 每天重置喝水计数
            const lastWaterReset = localStorage.getItem('lastWaterReset');
            const todayStr = `${date.year}-${date.month}-${date.day}`;
            
            if (lastWaterReset !== todayStr) {
                localStorage.setItem('waterCount', 0);
                localStorage.setItem('lastWaterReset', todayStr);
                document.getElementById('water-count').textContent = 0;
            }
        }
        
        // 页面加载完成后初始化
        window.addEventListener('DOMContentLoaded', initPage);
    </script>
</body>
</html>