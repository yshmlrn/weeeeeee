---
layout: page
title: 📚 程式課程學習中心
---

<style>
    /* 全域背景設定：使用深藍與深紫的漸層，營造科技感 */
    body {
        background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
        color: #e0e0e0;
        min-height: 100vh;
    }

    /* 標題區域 */
    .hero-section {
        text-align: center;
        padding: 60px 20px;
    }
    .hero-section h1 {
        font-size: 3rem;
        font-weight: 800;
        background: linear-gradient(to right, #4facfe, #00f2fe, #a8edea);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        margin-bottom: 15px;
    }
    .hero-section p {
        color: #94a3b8;
        font-size: 1.1rem;
        letter-spacing: 1px;
    }

    /* 卡片容器 */
    .card-container {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 30px;
        max-width: 1000px;
        margin: 0 auto 50px auto;
        padding: 0 20px;
    }

    /* 磨砂玻璃卡片效果 */
    .card {
        background: rgba(255, 255, 255, 0.05); /* 半透明背景 */
        backdrop-filter: blur(10px); /* 模糊背後內容 */
        -webkit-backdrop-filter: blur(10px);
        border: 1px solid rgba(255, 255, 255, 0.1);
        border-radius: 24px;
        padding: 40px 30px;
        text-align: center;
        text-decoration: none !important;
        transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .card:hover {
        transform: translateY(-15px) scale(1.02);
        background: rgba(255, 255, 255, 0.1);
        border-color: rgba(79, 172, 254, 0.5);
        box-shadow: 0 25px 50px rgba(0, 0, 0, 0.3);
    }

    /* 圖示與文字 */
    .icon-box {
        width: 80px;
        height: 80px;
        background: rgba(79, 172, 254, 0.1);
        border-radius: 20px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 2.5rem;
        margin-bottom: 20px;
    }

    .card h2 {
        color: #fff;
        font-size: 1.6rem;
        margin-bottom: 15px;
    }

    .card p {
        color: #cbd5e1;
        font-size: 0.95rem;
        line-height: 1.6;
        margin-bottom: 30px;
        flex-grow: 1;
    }

    /* 按鈕樣式 */
    .btn-start {
        width: 100%;
        padding: 12px 0;
        background: linear-gradient(135deg, #007bff 0%, #00d2ff 100%);
        color: white !important;
        border-radius: 12px;
        font-weight: bold;
        text-transform: uppercase;
        letter-spacing: 1px;
        box-shadow: 0 4px 15px rgba(0, 123, 255, 0.3);
    }

    /* 更新日誌區塊 */
    .update-log {
        max-width: 800px;
        margin: 50px auto;
        padding: 30px;
        background: rgba(0, 0, 0, 0.2);
        border-radius: 20px;
        border: 1px dashed rgba(255, 255, 255, 0.1);
    }
    .update-log h3 {
        color: #4facfe;
        margin-bottom: 20px;
        font-size: 1.2rem;
    }
    .update-item {
        list-style: none;
        padding: 10px 0;
        border-bottom: 1px solid rgba(255, 255, 255, 0.05);
        font-size: 0.9rem;
    }
    .update-date {
        display: inline-block;
        background: rgba(79, 172, 254, 0.2);
        color: #4facfe;
        padding: 2px 10px;
        border-radius: 6px;
        margin-right: 15px;
        font-family: monospace;
    }
</style>

<div class="hero-section">
    <h1>程式課程學習中心</h1>
    <p>探索科學計算與人工智慧的無限可能</p>
</div>

<div class="card-container">
    <a href="./matlab/ch01" class="card">
        <div class="icon-box">📊</div>
        <h2>MATLAB 核心</h2>
        <p>掌握矩陣運算的靈魂，從基礎語法到進階數據可視化，建立紮實的科學計算能力。</p>
        <span class="btn-start">進入課程</span>
    </a>

    <a href="./ai/ch01" class="card">
        <div class="icon-box">🤖</div>
        <h2>AI 深度學習</h2>
        <p>解密神經網路黑盒子，學習機器學習模型建構，親手打造屬於自己的 AI 應用。</p>
        <span class="btn-start">進入課程</span>
    </a>
</div>

<div class="update-log">
    <h3>📢 最近更新</h3>
    <ul>
        <li class="update-item">
            <span class="update-date">2025.12.28</span> 
            發布 AI 課程第二章：神經網路架構與反向傳播
        </li>
        <li class="update-item">
            <span class="update-date">2025.12.28</span> 
            MATLAB 單元新增「圖像處理」範例代碼
        </li>
    </ul>
</div>
