---
layout: course_layout
title: "期中報告"
---
# 工程專題期中報告：MATLAB程式設計

# 前言
Matlab是一個和數學高度相關的程式軟體，可以幫助使用者運算數值、影像處理、建立使用者介面等等。這次的報告主要分為三個主題，分別是三維圖形、GUI設計和影像動畫製作，呈現課程中的練習以及課程以外的更多應用。

# 主題一：三維圖形                                                                                      
## 大綱        
1. 利用 plot3、mesh、surf、contour等函數配合meshgrid、view繪製各種三維曲線、曲面、等高線與立體圖形。
2. 常用函數、和二維圖形函數做比較：  
  mesh, ezmesh	：立體網狀圖、meshc, ezmeshc：網狀圖加上等高線  
  meshz：網狀圖加上“圍裙”（或“舞臺”）  
  plot3, ezplot3：立體曲線圖  
  contour, ezcontour：平面上的等高線、contour3：空間中的等高線                                                                                   
## 實作    
 1. 用mesh、meshc、meshz、waterfall語法繪製圖形
```matlab
clear;
x = -5:0.1:5;         y = -5:0.1:5;
[X, Y] = meshgrid(x, y);
R=1.25*sqrt(X.^2+Y.^2);
Z=175-cos(R)+4*cos(3*R)+0.25;
% 使用mesh()語法
figure(1);
mesh(X, Y, Z);
xlabel('x');     ylabel('y');     zlabel('z');
grid on;      title('Mesh Plot');     axis tight;
% 使用meshc()語法
figure(2);      
meshc(X, Y, Z);
xlabel('x');     ylabel('y');     zlabel('z');
grid on;      title('Mesh Plot with Contour plot');     axis tight;
% 使用meshz()語法
figure(3);      
meshz(X, Y, Z);
xlabel('x');     ylabel('y');     zlabel('z');
grid on;      title('Mesh Plot with Zero Plates');     axis tight;
% 使用waterfall()語法
figure(4);      
waterfall(X, Y, Z);
xlabel('x');     ylabel('y');     zlabel('z');
grid on;      title('Waterfall Plot');     axis tight;
```


2. 使用surf、shading flat、shading interp、surfc語法繪製peaks圖形
```matlab
figure(1);    surfl(X, Y, Z);    shading flat;
   view(-30,30);
   xlabel('x');    ylabel('y');      zlabel('z');
   axis tight;     title('Surface plot');
figure(2);    surf(X, Y, Z);    shading interp;
   view(-60,60);
   xlabel('x');    ylabel('y');      zlabel('z');
   axis tight;     title('Surface plot with Flat shading');
figure(3);    surf(X, Y, Z);    shading flat;
   view(-60,90);
   xlabel('x');    ylabel('y');      zlabel('z');
   axis tight;     title('Surface plot with Interpolated shading'); 
figure(4);    surfc(X, Y, Z);    shading interp;
   view(0,90);
   xlabel('x');    ylabel('y');      zlabel('z');
   axis tight;     title('Surface plot with Contours');
```


3. 已知一物體以初速度120m/s ，仰角40度往70度方向拋出，重力加速度為10m/s2，利用plot3語法繪製其拋物線，並顯示標題、格線、標註x、y與z座標。  
*說明：將所有已知數據帶進去後用斜拋公式求函數，再用函數畫圖
```matlab
clc; clear; close all;
% 參數設定
v0=120;       % 初速度 (m/s)
theta=40;     % 仰角 (deg)
phi=70;       % 水平面方向角 (deg)
g=10;         % 重力加速度 (m/s^2)
% 初速在各軸分量
v0x=v0*cosd(theta)*cosd(phi);
v0y=v0*cosd(theta)*sind(phi);
v0z=v0*sind(theta);
% 飛行時間 (落地時 z=0)
T=2*v0z/g;
% 時間序列
t=linspace(0, T, 200);
% 軌跡方程
x=v0x*t;
y=v0y*t;
z=v0z*t-0.5*g*t.^2;
% 繪圖
plot3(x, y, z, 'b', 'LineWidth', 2);
grid on;
xlabel('x (m)');
ylabel('y (m)');
zlabel('z (m)');
title('三維拋體運動軌跡');
```
## 延伸應用
動機：
以前在上化學課的時候一直覺得立體分子模型很難懂，想不通講義上的平面圖到底怎麼變成立體的，透過所學的三維繪圖實際把模型畫出來後，我對分子的鍵角等等有更多的了解，讓抽象的概念具體的呈現在我面前。  
*以AI輔助完成
```matlab
% PCl5 的球棒模型 (Trigonal bipyramidal)
figure(2);
hold on;
axis equal;
xlabel('X'); ylabel('Y'); zlabel('Z');
view(45,30);
P = [0 0 0]; % 中心 P 原子
% 軸向 Cl (在 z 軸)
Cl_axial = [0 0 3;
           0 0 -3];
% 赤道 Cl (xy 平面上，120°)
theta = [0, 120, 240] * pi/180;
Cl_equatorial = [cos(theta)' sin(theta)' zeros(3,1)] * 3;
Cl = [Cl_axial; Cl_equatorial]; % 全部氯原子
% --- 畫 P 原子 ---
[r, s, t] = sphere(20);
surf(0.6*r + P(1), 0.6*s + P(2), 0.6*t + P(3), ...
   'FaceColor','y','EdgeColor','none');  % P = 黃色
% --- 畫 Cl 原子 + 鍵 ---
for i = 1:size(Cl,1)
   % 氯原子 (綠色)
   surf(0.8*r + Cl(i,1), 0.8*s + Cl(i,2), 0.8*t + Cl(i,3), ...
       'FaceColor','g','EdgeColor','none');
  
   % 鍵 (黑色直線)
   plot3([P(1) Cl(i,1)], [P(2) Cl(i,2)], [P(3) Cl(i,3)], ...
       'k-', 'LineWidth', 2);
end
light; lighting gouraud; %讓球體平滑
title('PCl_5 球棒模型');
```
## 心得
之前從來沒有自己繪製過三維圖形，我覺得這是個很新奇的體驗。  
在學習繪製三維圖形之後，原本在平面上看不懂的化學模型和等高線，變成立體圖形後變得清楚許多，可以自己透過程式畫出圖形對我來說是件很酷也很有成就感的事。  

# 主題二：GUI設計                                                                                      
## 大綱        
1. propedit：開啟性質編輯器  
   set：改變物件性質(寬度、線標、大小)  
  (也可用set來列出物件所有性質)  
2. UI控制物件：按鈕、滑動棒、圓形按鈕、框架、核計方塊、文字欄位、列表式選單、下拉式選單
3. 設定滑鼠事件反應：WindowButtonDownFcn(按下)、WindowButtonMotionFcn(移動)、WindowButtonUpFcn(釋放)                                                                	
## 實作    
1. 用線段將繪製的點連起來，並加上兩個下拉選單，分別可以讓使用者改變 marker 和 line 的顏色。
```matlab
function mouse03(action)
% mouse03: 用滑鼠畫線＋點，並提供下拉選單選擇 marker 和線段顏色
if nargin < 1, action = 'start'; end
switch(action)
	case 'start'
		% 建立圖形視窗與控制項
		figure('Name', 'Mouse Drawing Tool', 'NumberTitle', 'off', ...
			'WindowButtonDownFcn', 'mouse03 down');
		% 建立兩個下拉選單
		uicontrol('Style', 'text', 'String', 'Marker Color:', ...
			'position', [10 60 80 20], 'HorizontalAlignment', 'left');
		uicontrol('Style', 'popupmenu', 'String', {'r','g','b','k','m','c','y'}, ...
			'position', [90 60 60 20], 'Tag', 'markerMenu');
		uicontrol('Style', 'text', 'String', 'Line Color:', ...
			'position', [10 30 80 20], 'HorizontalAlignment', 'left');
		uicontrol('Style', 'popupmenu', 'String', {'r','g','b','k','m','c','y'}, ...
			'position', [90 30 60 20], 'Tag', 'lineMenu');
		% 設定座標區
		axes('Units', 'pixels', 'Position', [170 20 400 400]);
		axis([0 1 0 1]);
		box on;
		hold on;
		title('Click and drag your mouse in this window!');
		% 清除 UserData
		set(gcf, 'UserData', []);
	case 'down'
		set(gcf, 'WindowButtonMotionFcn', 'mouse03 move');
		set(gcf, 'WindowButtonUpFcn', 'mouse03 up');
		currPt = get(gca, 'CurrentPoint');
		prevPt = currPt(1,1:2);
		set(gcf, 'UserData', prevPt);
		fprintf('Mouse down at (%.3f, %.3f)\n', prevPt(1), prevPt(2));
	case 'move'
		currPt = get(gca, 'CurrentPoint');
		x = currPt(1,1);
		y = currPt(1,2);
		prevPt = get(gcf, 'UserData');
		% 取得選單顏色
		markerColor = getColorFromMenu('markerMenu');
		lineColor   = getColorFromMenu('lineMenu');
		% 畫線與點
		if ~isempty(prevPt)
			plot([prevPt(1), x], [prevPt(2), y], '-', 'Color', lineColor);
		end
		plot(x, y, '.', 'Color', markerColor);
		% 更新上一個點
		set(gcf, 'UserData', [x, y]);
		fprintf('Mouse is moving! Current location = (%.3f, %.3f)\n', x, y);
	case 'up'
		currPt = get(gca, 'CurrentPoint');
		x = currPt(1,1);
		y = currPt(1,2);
		markerColor = getColorFromMenu('markerMenu');
		plot(x, y, '.', 'Color', markerColor);
		% 清除事件與記錄
		set(gcf, 'WindowButtonMotionFcn', '');
		set(gcf, 'WindowButtonUpFcn', '');
		set(gcf, 'UserData', []);
		fprintf('Mouse up at (%.3f, %.3f)\n', x, y);
end
end
% 子函數：取得選單選取的顏色 
function color = getColorFromMenu(tag)
	menuHandle = findobj('Tag', tag);
	options = get(menuHandle, 'String');
	idx = get(menuHandle, 'Value');
	color = options{idx};
end
```

2. 延伸應用：可變換顏色的拋物線動畫  
*結合GUI、二維圖形、多項式  
*以AI輔助完成  
*節錄完整程式中的段落  
```matlab
% 控制元件
   uicontrol('Style', 'pushbutton', 'String', '開始', 'FontSize', 12, ...
             'Position', [70 20 80 40], 'Callback', @(src, event) startMotion());
   uicontrol('Style', 'pushbutton', 'String', '停止', 'FontSize', 12, ...
             'Position', [170 20 80 40], 'Callback', @(src, event) stopMotion());
   uicontrol('Style', 'pushbutton', 'String', '重設', 'FontSize', 12, ...
             'Position', [270 20 80 40], 'Callback', @(src, event) resetBall());
% 顏色下拉選單
   popupColor = uicontrol('Style', 'popupmenu', ...
             'String', {'紅', '藍', '綠', '黃', '紫', '黑'}, ...
             'FontSize', 12, ...
             'Position', [380 20 100 40], ...
             'Callback', @(src, event) changeColor(src));
% 角度調整滑桿
   uicontrol('Style', 'text', 'String', '角度：', 'FontSize', 12, ...
             'Position', [500 50 60 20]);
   sliderTheta = uicontrol('Style', 'slider', ...
             'Min', 20, 'Max', 80, 'Value', 45, ...
             'Position', [500 25 80 20]); 
   isMoving = false;
   currentColor = 'r'; % 初始顏色
% 開始運動
   function startMotion()
       if isMoving, return; end
       isMoving = true;
       theta = get(sliderTheta, 'Value');
       t = 0; dt = 0.03;
       xPrev = 0; yPrev = 0;      
       while isMoving && ishandle(hBall)
           % 拋物線公式
           x = v0 * cosd(theta) * t;
           y = v0 * sind(theta) * t - 0.5 * g * t^2;
           if y < 0
               break;
           end    
           % 每一小段畫出軌跡
           plot([xPrev x], [yPrev y], '-', 'Color', currentColor, 'LineWidth', 2);         
           % 更新球位置
           set(hBall, 'XData', x, 'YData', y, ...
               'MarkerFaceColor', currentColor, 'MarkerEdgeColor', currentColor);          
           drawnow;
           pause(dt);          
           % 更新前一點位置
           xPrev = x;
           yPrev = y;
           t = t + dt;
       end
       isMoving = false;
   end
   function stopMotion()
       isMoving = false;
   end
```
說明：
程式中設有開始、停止和重設三個控制按鈕，讓使用者能開始或停止模擬，透過下拉式選單可改變球的顏色，且運動軌跡會跟著球的顏色做改變，角度滑桿能控制拋射角度，觀察角度變化對拋物線形狀的影響。

## 心得
這個主題對我來說很有趣，比起單純寫程式讓東西在執行的時候自己跑完，我更喜歡程式運行後可以互動的感覺，讓本來死板的程式活起來。  
在這個章節中，我學會了如何使用控制按鈕、列表、下拉式選單，也很意外可以透過滑鼠點擊、移動、放開來控制程式運行的內容，這些內容能很有效地和其他主題結合，像是二維、三維圖形等等，在平淡的程式中增添一點樂趣。

# 主題三：影像與動畫                                                                                      
## 大綱        
1. 索引圖像、將圖像導入：load(內建影像樣本)、imread(讀取外部圖檔)、  
  imwrite(X,map,'cape.tif','tif'); 將生成的圖片儲存成名為cape.tif的檔案  
  [X,map]=imread('trees.tif');  讀取tree.tif這個檔案、含變數X、map(會出現在workspace中)
2. 動畫：調整視角(view)搭配for迴圈、comet(二維曲線追蹤動畫) 
3. imfinfo：顯示所有屬性資料                                                                                           	
## 實作    
1. 將彩色圖片變成灰階
```matlab
%%
clear;
  imfile = 'cinnamon.jpg';        % 設定影像檔
  x = imread(imfile);         % 讀入影像檔
  y=rgb2gray(x);
  imshow(y);
  colormap(gray(size(unique(y),1)));
  % 顯示影像
  imfinfo('cinnamon.jpg')
title(size(unique(y),1));     axis image;
```
將影像檔讀入後利用colormap找出灰階影像的灰階大小，並顯示影像(imshow)和屬性資料(imfinfo)


2. 繪出影像直方圖
```matlab
%%
%直方圖等化
%hw
clear
%
x = imread('woman.tif');  
%image(x);
figure(1);  imshow(x);
figure(2);  imhist(x);
```

3. 延伸應用：影像強化、直方圖系統  
*以AI輔助完成  
*結合GUI  
```matlab
function image_enhance_color_gui
   % 建立主視窗 
   f = figure('Name', '影像強化系統（彩色版）', ...
              'Position', [400 200 800 500], ...
              'NumberTitle', 'off', ...
              'Color', [0.95 0.95 0.95]);
   % 顯示區 
   ax = axes('Parent', f, 'Units', 'pixels', 'Position', [50 100 500 370]);
   axis off;
   title('原始影像');
   imfile = 'stripedog.jfif';   % 載入自己的圖像
   img = im2double(imread(imfile));
   adjustedImg = img;
   axes(ax);
   imshow(img);
   % 按鈕 
   uicontrol('Style', 'pushbutton', 'String', '直方圖均衡化', ...
             'FontSize', 11, 'Position', [600 340 150 40], ...
             'Callback', @(~,~) enhanceHistogram());
   uicontrol('Style', 'pushbutton', 'String', '重設', ...
             'FontSize', 11, 'Position', [600 280 150 40], ...
             'Callback', @(~,~) resetImage());
   % 亮度滑桿 
   uicontrol('Style', 'text', 'String', '亮度', 'FontSize', 11, ...
             'Position', [600 230 50 20]);
   sliderBright = uicontrol('Style', 'slider', 'Min', -0.5, 'Max', 0.5, ...
             'Value', 0, 'Position', [650 235 100 20], ...
             'Callback', @(src,~) adjustImage());
   % 對比滑桿 
   uicontrol('Style', 'text', 'String', '對比', 'FontSize', 11, ...
             'Position', [600 190 50 20]);
   sliderContrast = uicontrol('Style', 'slider', 'Min', 0.5, 'Max', 2, ...
             'Value', 1, 'Position', [650 195 100 20], ...
             'Callback', @(src,~) adjustImage());
   % 功能函式 
   function enhanceHistogram()
       hsvImg = rgb2hsv(adjustedImg);
       hsvImg(:,:,3) = histeq(hsvImg(:,:,3)); % 對亮度通道均衡化
       adjustedImg = hsv2rgb(hsvImg);
       axes(ax);
       imshow(adjustedImg);
       title('直方圖均衡化後影像');
   end
   function adjustImage()
       brightness = get(sliderBright, 'Value');
       contrast = get(sliderContrast, 'Value');
       adjustedImg = img * contrast + brightness;
       adjustedImg = min(max(adjustedImg, 0), 1); % 限制在[0,1]
       axes(ax);
       imshow(adjustedImg);
       title(sprintf('亮度=%.2f, 對比=%.2f', brightness, contrast));
   end
   function resetImage()
       adjustedImg = img;
       axes(ax);
       imshow(img);
       title('原始影像');
       set(sliderBright, 'Value', 0);
       set(sliderContrast, 'Value', 1);
   end
end
```
說明：程式開始後會載入圖片，可以直接透過滑桿控制亮度與對比變化，畫面會更新顯示結果，若按下「直方圖均衡化」按鈕，系統會針對影像的亮度分佈進行重新分配，使影像明暗更均勻、細節更清晰。


## 心得
影像處理是個我從來沒有接觸過的單元，調整解析度、轉成灰階都讓我對影像處理有更深的認識，做出直方圖讓我更了解圖片其實是由數值組成的，可以透過程式去分析肉眼看到的顏色和形狀也讓我對影像處理的原理更有概念。


