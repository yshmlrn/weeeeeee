---
layout: page
title: 📚 程式課程學習中心
---

<style>
    /* 整體背景優化 */
    :root {
        --primary-color: #4facfe;
        --secondary-color: #00f2fe;
        --text-dark: #2d3436;
        --text-light: #636e72;
    }

    /* 標題與引言 */
    .hero-section {
        text-align: center;
        padding: 40px 0;
    }
    .hero-section h1 {
        font-size: 2.5rem;
        background: linear-gradient(to right, #007bff, #00c6ff);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        margin-bottom: 10px;
    }

    /* 卡片容器佈局 */
    .card-container {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
        gap: 25px;
        margin-top: 20px;
    }

    /* 現代感卡片設計 */
    .card {
        background: #ffffff;
        border-radius: 20px;
        padding: 35px 25px;
        text-align: center;
        text-decoration: none !important;
        color: var(--text-dark) !important;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
        border: 1px solid rgba(0, 0, 0, 0.03);
        transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
        position: relative;
        overflow: hidden;
    }

    .card:hover {
        transform: translateY(-10px);
        box-shadow: 0 20px 40px rgba(0, 123, 255, 0.15);
        border-color: rgba(0, 123, 255, 0.2);
    }

    /* 圖示放大效果 */
    .card .icon {
        font-size: 3.5rem;
        margin-bottom: 15px;
        display: block;
        transition: transform 0.3s ease;
    }
    .card:hover .icon {
        transform: scale(1.15);
    }

    .card h2 {
        font-size: 1.5rem;
        margin-top: 0;
        margin-bottom: 12px;
        color: #333;
    }

    .card p {
        font-size: 0.95rem;
        color: var(--text-light);
        line-height: 1.6;
        margin-bottom: 25px;
    }

    /* 質感按鈕 */
    .btn-start {
        display: inline-block;
        padding: 10px 30px;
        background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
        color: white !important;
        border-radius: 50px;
        font-weight: 600;
        letter-spacing: 0.5px;
        transition: opacity 0.2s;
        box-shadow: 0 4px 15px rgba(79, 172, 254, 0.4);
    }

    .btn-start:hover {
        opacity: 0.9;
    }

    /* 更新日誌區塊 */
    .update-log {
        margin-top: 50px;
        padding: 25px;
        background: #f8f9fa;
        border-radius: 15px;
        border-left: 5px solid #007bff;
    }
    .update-log h3 {
        margin-top: 0;
        font-size: 1.2rem;
        display: flex;
        align-items: center;
    }
    .update-item {
        font-size: 0.9rem;
        margin-bottom: 8px;
        list-style: none;
    }
    .update-date {
        font-weight: bold;
        color: #007bff;
        margin-right: 10px;
    }
</style>

<div class="hero-section">
    <h1>歡迎來到我的線上講義</h1>
    <p>提升專業技能，掌握未來關鍵技術</p>
</div>

<div class="card-container">
    <a href="./matlab/ch01" class="card">
        <span class="icon">📊</span>
        <h2>MATLAB 基礎</h2>
        <p>矩陣運算、數據繪圖與科學計算基礎，打造紮實的數據分析力。</p>
        <span class="btn-start">開始探索</span>
    </a>

    <a href="./ai/ch01" class="card">
        <span class="icon">🤖</span>
        <h2>AI 深度學習</h2>
        <p>從機器學習導論到神經網路實作，一步步進入 AI 的核心領域。</p>
        <span class="btn-start">立即學習</span>
    </a>
</div>

<div class="update-log">
    <h3>📢 最新更新公告</h3>
    <ul>
        <li class="update-item"><span class="update-date">2025-12-28</span> 新增 AI 課程第二章「神經網路」實作內容。</li>
        <li class="update-item"><span class="update-date">2025-12-28</span> 優化 MATLAB 側邊欄導覽，修復失效連結。</li>
    </ul>
</div>
