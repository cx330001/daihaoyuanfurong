<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>我的应用启动器</title>
    
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="theme-color" content="#f0f2f5">

    <style>
        /* === 全局重置 === */
        * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
        body, html { margin: 0; padding: 0; width: 100%; height: 100%; overflow: hidden; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif; background: #f0f2f5; }

        /* === 1. 桌面启动器 (Launcher) === */
        #launcher {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            background: linear-gradient(135deg, #e0c3fc 0%, #8ec5fc 100%); /* 漂亮的渐变背景 */
            transition: transform 0.4s cubic-bezier(0.25, 0.8, 0.25, 1), opacity 0.4s;
            z-index: 1;
        }

        /* 隐藏启动器时的动画 */
        #launcher.hidden { transform: scale(1.2); opacity: 0; pointer-events: none; }

        .app-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 40px; }

        .app-icon {
            display: flex; flex-direction: column; align-items: center; cursor: pointer;
            transition: transform 0.2s;
        }
        .app-icon:active { transform: scale(0.95); }

        .icon-box {
            width: 80px; height: 80px; border-radius: 18px;
            background: white;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
            display: flex; justify-content: center; align-items: center;
            font-size: 32px; margin-bottom: 10px;
        }
        /* 给不同的 App 不同的图标颜色 */
        .icon-a { background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 99%); color: white; }
        .icon-b { background: linear-gradient(135deg, #a18cd1 0%, #fbc2eb 100%); color: white; }

        .app-name { font-size: 14px; color: #333; font-weight: 500; text-shadow: 0 1px 2px rgba(255,255,255,0.5); }

        /* === 2. 应用容器 (App Container) === */
        #app-viewer {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            background: #fff; z-index: 2;
            transform: translateY(100%); /* 默认藏在屏幕下方 */
            transition: transform 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
        }
        #app-viewer.active { transform: translateY(0); }

        iframe { width: 100%; height: 100%; border: none; display: none; }
        iframe.show { display: block; }

        /* === 3. 悬浮按钮 (FAB) === */
        /* 主按钮 */
        .fab-container {
            position: fixed; bottom: 30px; right: 20px; z-index: 999;
            display: none; /* 只有在应用内才显示 */
            flex-direction: column-reverse; align-items: center; gap: 15px;
        }
        .fab-container.visible { display: flex; }

        .fab-main {
            width: 56px; height: 56px; border-radius: 50%;
            background: #333; color: white;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            display: flex; justify-content: center; align-items: center;
            font-size: 24px; cursor: pointer; user-select: none;
            transition: transform 0.3s, background 0.3s;
        }
        .fab-main.open { transform: rotate(45deg); background: #ff4757; }

        /* 子菜单按钮 */
        .fab-menu {
            display: flex; flex-direction: column; gap: 15px;
            opacity: 0; transform: translateY(20px) scale(0.8); pointer-events: none;
            transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }
        .fab-menu.show { opacity: 1; transform: translateY(0) scale(1); pointer-events: auto; }

        .fab-item {
            width: 48px; height: 48px; border-radius: 50%;
            background: white; color: #333;
            box-shadow: 0 2px 10px rgba(0,0,0,0.15);
            display: flex; justify-content: center; align-items: center;
            font-size: 20px; cursor: pointer; position: relative;
        }
        .fab-item::after {
            content: attr(data-label);
            position: absolute; right: 60px;
            background: rgba(0,0,0,0.7); color: white; padding: 4px 8px; border-radius: 4px;
            font-size: 12px; opacity: 0; pointer-events: none; transition: opacity 0.2s; white-space: nowrap;
        }
        .fab-item:hover::after { opacity: 1; }
/* 1. 基础页面设置：移除居中和内边距 */
body {
    margin: 0 !important;
    font-family: 'bulangni', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    font-weight: normal;
    background-color: #f0f2f5;
    height: 100% !important;
    overflow: hidden !important;
    
    /* 强制重置 Flex 布局，防止居中 */
    display: block !important;
    padding: 0 !important;
    align-items: unset !important;
    justify-content: unset !important;
}

/* 2. 手机屏幕容器：强制占满全屏 */
#phone-screen {
    width: 100% !important;
    height: 100vh !important; /* 视口高度的 100% */
    position: relative !important;
    overflow: hidden !important;
    display: flex !important;
    flex-direction: column !important;
    background-color: #ffffff;
    
    /* 重置可能存在的固定尺寸和边框 */
    max-width: none !important;
    max-height: none !important;
    border: none !important;
    border-radius: 0 !important;
    box-shadow: none !important;
    margin: 0 !important;
    top: 0 !important;
    left: 0 !important;
}

/* 3. 隐藏可能残留的刘海或屏幕装饰 */
body #phone-screen::before,
body #phone-screen::after {
    display: none !important;
}
    </style>
</head>
<body>

    <div id="launcher">
        <h2 style="color: #fff; margin-bottom: 40px; text-shadow: 0 2px 4px rgba(0,0,0,0.2);">我的空间</h2>
        <div class="app-grid">
            <div class="app-icon" onclick="openApp('a')">
                <div class="icon-box icon-a">A</div>
                <div class="app-name">功能 A</div>
            </div>
            
            <div class="app-icon" onclick="openApp('b')">
                <div class="icon-box icon-b">B</div>
                <div class="app-name">功能 B</div>
            </div>
        </div>
    </div>

    <div id="app-viewer">
        <iframe id="frame-a" src="https://cx3300-1.github.io/ooooka/" class="active"></iframe>
    <iframe id="frame-b" src="https://cx3300-1.github.io/sfsfdf/"></iframe>
    </div>

    <div class="fab-container" id="fabContainer">
        <div class="fab-main" onclick="toggleMenu()">+</div>
        
        <div class="fab-menu" id="fabMenu">
            <div class="fab-item" onclick="switchApp('a')" data-label="切换到 A">A</div>
            <div class="fab-item" onclick="switchApp('b')" data-label="切换到 B">B</div>
            <div class="fab-item" style="background: #333; color: #fff;" onclick="goHome()" data-label="退出桌面">🏠</div>
        </div>
    </div>

    <script>
        const launcher = document.getElementById('launcher');
        const appViewer = document.getElementById('app-viewer');
        const fabContainer = document.getElementById('fabContainer');
        const fabMenu = document.getElementById('fabMenu');
        const fabMain = document.querySelector('.fab-main');
        
        let currentAppId = null;

        // 打开应用
        function openApp(id) {
            currentAppId = id;
            const iframe = document.getElementById('frame-' + id);

            // 懒加载：第一次点击时才加载 URL，节省流量
            if (!iframe.src && iframe.dataset.src) {
                iframe.src = iframe.dataset.src;
            }

            // 1. 隐藏所有 iframe，只显示当前的
            document.querySelectorAll('iframe').forEach(el => el.classList.remove('show'));
            iframe.classList.add('show');

            // 2. 界面动画
            launcher.classList.add('hidden'); // 桌面放大消失
            appViewer.classList.add('active'); // 应用滑上来
            
            // 3. 显示悬浮按钮
            setTimeout(() => {
                fabContainer.classList.add('visible');
            }, 300);
        }

        // 返回桌面
        function goHome() {
            // 收起菜单
            toggleMenu(false);
            
            // 界面动画
            appViewer.classList.remove('active'); // 应用滑下去
            launcher.classList.remove('hidden');  // 桌面显示

            // 隐藏悬浮按钮
            fabContainer.classList.remove('visible');
            currentAppId = null;
        }

        // 快速切换
        function switchApp(id) {
            if (currentAppId === id) {
                toggleMenu(false); // 如果点的就是当前 App，只关菜单
                return;
            }
            toggleMenu(false); // 关菜单
            
            // 简单的切换动画效果
            appViewer.style.opacity = '0'; // 先变透明
            
            setTimeout(() => {
                openApp(id); // 切换 iframe
                appViewer.style.opacity = '1'; // 变回来
            }, 200);
        }

        // 控制悬浮菜单开关
        function toggleMenu(forceState) {
            const isOpen = fabMenu.classList.contains('show');
            const shouldOpen = forceState !== undefined ? forceState : !isOpen;

            if (shouldOpen) {
                fabMenu.classList.add('show');
                fabMain.classList.add('open');
            } else {
                fabMenu.classList.remove('show');
                fabMain.classList.remove('open');
            }
        }
    </script>
</body>
</html>
