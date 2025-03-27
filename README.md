
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>河南牧业经济学院</title>
    <style>
        /* 原有样式保留 */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: Arial, sans-serif; line-height: 1.6; }
        nav { background: #333; padding: 1rem; color: white; }
        nav ul { display: flex; list-style: none; gap: 2rem; flex-wrap: wrap; }
        nav a { color: white; text-decoration: none; }
        .container { display: flex; gap: 2rem; padding: 2rem; max-width: 1200px; margin: 0 auto; }
        .sidebar { flex: 1; background: #f4f4f4; padding: 1rem; }
        .main-content { flex: 3; }
        .news-item { margin-bottom: 2rem; padding: 1rem; border-bottom: 1px solid #ddd; }
        @media (max-width: 768px) { .container { flex-direction: column; } }
        .features { padding: 2rem; background: #e7f3fe; margin: 2rem 0; }
        .features ul { padding-left: 2rem; }
        footer { background: #333; color: white; text-align: center; padding: 1rem; position: fixed; bottom: 0; width: 100%; }

        /* 新增轮播图样式 */
        .carousel-container {
            position: relative;
            width: 100%;
            overflow: hidden;
            border-radius: 8px;
            margin-top: 1rem;
        }
        .carousel-slide {
            display: flex;
            transition: transform 0.5s ease-in-out;
        }
        .carousel-item {
            min-width: 100%;
            position: relative;
        }
        .carousel-item img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }
        .carousel-control {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(0,0,0,0.5);
            color: white;
            padding: 10px 15px;
            border: none;
            cursor: pointer;
            font-size: 18px;
        }
        .carousel-prev { left: 0; }
        .carousel-next { right: 0; }
        .carousel-indicators {
            position: absolute;
            bottom: 10px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 8px;
        }
        .indicator {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: rgba(255,255,255,0.5);
            cursor: pointer;
            transition: background0.3s;
        }
        .indicator.active { background: #fff; }
    </style>
</head>
<body>
    <nav>
        <ul>
            <li>首页</li>
            <li>新闻公告</li>
            <li>院系设置</li>
            <li>招生就业</li>
            <li>联系我们</li> <!-- 更新为超链接 -->
            <li>校园地图</li> <!-- 新增链接 -->
        </ul>
    </nav>

    <div class="container">
        <!-- 左侧边栏 - 校园风光轮播 -->
        <aside class="sidebar">
            <h2>校园风光</h2>
            <div class="carousel-container">
                <div class="carousel-slide">
                    <div class="carousel-item">
                        <img src="images/campus1.jpg" alt="校园风光1">
                    </div>
                    <div class="carousel-item">
                        <img src="images/campus2.jpg" alt="校园风光2">
                    </div>
                    <div class="carousel-item">
                        <img src="images/campus3.jpg" alt="校园风光3">
                    </div>
                </div>
                <button class="carousel-control carousel-prev">❮</button>
                <button class="carousel-control carousel-next">❯</button>
                <div class="carousel-indicators"></div>
            </div>
            <div class="features">
                <h3>特色服务</h3>
                <ul>
                    <li>响应式布局</li>
                    <li>现代设计风格</li>
                    <li>交互动画效果</li>
                </ul>
            </div>
        </aside>

        <!-- 中间主要内容区保持不变 -->
        <main class="main-content">
            <!-- 原有内容 -->
        </main>

        <!-- 右侧边栏 -->
        <aside class="sidebar">
            <h3>快速链接</h3>
            <ul style="margin-top: 1rem;">
                <li>招生信息</li>
                <li>联系方式</li>
                <li>校园地图</li>
            </ul>
        </aside>
    </div>

    <script>
        // 轮播图功能
        const slide = document.querySelector('.carousel-slide');
        const items = document.querySelectorAll('.carousel-item');
        const prevBtn = document.querySelector('.carousel-prev');
        const nextBtn = document.querySelector('.carousel-next');
        const indicatorsContainer = document.querySelector('.carousel-indicators');
        let currentIndex = 0;

        // 初始化指示器
        items.forEach((_, index) => {
            const indicator = document.createElement('div');
            indicator.className = 'indicator';
            if(index === 0) indicator.classList.add('active');
            indicator.addEventListener('click', () => goToSlide(index));
            indicatorsContainer.appendChild(indicator);
        });

        function updateCarousel() {
            slide.style.transform = `translateX(-${currentIndex * 100}%)`;
            document.querySelectorAll('.indicator').forEach((indicator, index) => {
                indicator.classList.toggle('active', index === currentIndex);
            });
        }

        function goToSlide(index) {
            currentIndex = (index + items.length) % items.length;
            updateCarousel();
        }

        // 事件监听
        prevBtn.addEventListener('click', () => goToSlide(currentIndex - 1));
        nextBtn.addEventListener('click', () => goToSlide(currentIndex + 1));

        // 自动播放（可选）
        setInterval(() => goToSlide(currentIndex + 1), 5000);
    </script>
</body>
</html>
