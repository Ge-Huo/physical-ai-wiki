    # 手机传感器物理实验

   ## 实验概述
   本实验利用手机内置的加速度传感器，通过HTML5的DeviceMotionEvent API实时采集运动数据，验证牛顿力学中的超重、失重现象，或分析运动强度。

   ## 在线工具
   ### 🚀 启动实验

点击下方按钮，将在新标签页中打开全屏交互式仿真环境。

<!-- 下面这一段就是启动按钮的代码 -->
<div style="margin-top: 20px; margin-bottom: 20px;">
    <a href="exp-animation/accelerometer-experiment-with-mobile-phones.html" target="_blank">
        <button 
            style="
                background-color: #007bff; 
                color: white; 
                padding: 12px 24px; 
                font-size: 16px; 
                border: none; 
                border-radius: 6px; 
                cursor: pointer; 
                box-shadow: 0 4px 6px rgba(0,0,0,0.1);
                transition: background-color 0.3s;"
            onmouseover="this.style.backgroundColor='#0056b3'" 
            onmouseout="this.style.backgroundColor='#007bff'"
        >
            ⚡ 打开全屏仿真实验
        </button>
    </a>
</div> 
   *（请用Chrome或手机自带浏览器打开，微信/QQ内需“在浏览器中打开”）*

   ## 实验原理
   1. **数据来源**：手机加速度传感器（含重力分量）。  
   2. **合加速度**：通过三轴加速度的平方和开根号计算，反映运动剧烈程度（静止时约9.8 m/s²）。  
   3. **姿态角**：利用重力方向分量估算手机倾斜角度（仅缓慢运动时准确）。  

   ## 操作步骤
   1. 打开上方链接，点击“点击开始测量”按钮。  
   2. 摇晃手机，观察X/Y/Z轴加速度和合加速度曲线的变化。  
   3. 尝试以下实验：  
      - **电梯超重/失重**：进入电梯，观察上升/下降时的合加速度变化。  
      - **自由落体**：将手机轻轻抛起（注意安全），观察加速度瞬间接近0的现象。  
      - **水平仪**：将手机平放，调整角度至俯仰角/翻滚角为0°。  

   
   
   
   
   
