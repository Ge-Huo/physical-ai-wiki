# 裸眼3D视差照片 - 手机传感器交互实验

## 实验概述
本实验利用手机内置的陀螺仪传感器，通过 HTML5 的 `DeviceOrientationEvent` API 实时采集手机的倾斜角度，并将其映射为前端 CSS3 3D 空间中的变换指令。用户只需上传一张普通的 2D 照片，在倾斜或晃动手机时，照片中的景物便会随着视角的改变产生真实的景深位移，体验沉浸式的“裸眼3D”视觉效果。

## 在线工具
### 🚀 启动实验

点击下方按钮，将在新标签页中打开全屏交互式 3D 照片体验页面。

<!-- 启动按钮，需要根据实际部署路径修改 href -->
<div style="margin-top: 20px; margin-bottom: 20px;">
    <a href="exp-animation/3d-photo.html" target="_blank">
        <button 
            style="
                background: linear-gradient(135deg, #667eea, #764ba2); 
                color: white; 
                padding: 12px 28px; 
                font-size: 16px; 
                font-weight: 600;
                border: none; 
                border-radius: 8px; 
                cursor: pointer; 
                box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
                transition: transform 0.2s, box-shadow 0.2s;"
            onmouseover="this.style.transform='scale(1.03)'; this.style.boxShadow='0 6px 25px rgba(102, 126, 234, 0.6)'" 
            onmouseout="this.style.transform='scale(1)'; this.style.boxShadow='0 4px 15px rgba(102, 126, 234, 0.4)'"
        >
            🖼️ 打开3D照片体验
        </button>
    </a>
</div>

*（请用 Chrome 或手机自带浏览器打开，微信/QQ 内需“在浏览器中打开”以启用传感器权限）*

## 实验原理

1. **传感器数据**：利用 `deviceorientation` 事件获取手机的 **β（前后倾斜）** 和 **γ（左右倾斜）** 角度。
2. **3D 渲染模型**：利用 CSS3 的 `perspective` 属性定义观察者的视距，并通过 `transform-style: preserve-3d` 确保照片在三维空间中旋转时保持立体结构。
3. **控制映射**：将采集到的倾斜角度映射为 CSS 的 `rotateX` 和 `rotateY` 变换属性。为了防止画面过度翻转，代码中对旋转角度进行了限幅处理，并除以系数以降低灵敏度，使交互更加丝滑。
4. **交互机制**：
   - **iOS 权限拦截**：苹果在 iOS 13 之后对陀螺仪增加了隐私限制，必须通过用户点击触发 `DeviceOrientationEvent.requestPermission()` 才能获取数据。
   - **多端兼容**：在桌面端或无传感器设备上，自动将鼠标移动轨迹映射为 3D 旋转角度，实现跨平台体验。

## 操作步骤

1. 点击上方按钮打开 3D 照片体验页面。
2. **首次使用**：允许浏览器获取设备方向权限（iOS 会弹出授权框，请点击“允许”）。
3. **上传照片**：点击右上角的“📷 换一张照片”按钮，从本地相册选择一张图片。
4. **体感交互**：
   - 手持手机，向前/后/左/右缓慢倾斜或晃动。
   - 观察照片在 3D 空间中的跟随转动效果。
5. **观察反馈**：
   - 页面底部会显示“🖱 倾斜手机或滑动屏幕查看3D效果”的提示文字。
   - 照片带有圆角和阴影，在转动时具有强烈的立体悬浮感。
6. **备选操控**：在电脑上可使用鼠标移动来模拟手机的倾斜效果，无需传感器。

## 注意事项

- 传感器数据在手机平稳握持时最稳定，剧烈抖动可能导致画面旋转过快，建议匀速晃动。
- 如果 3D 立体感不够强烈，可在代码中调小 `.scene` 的 `perspective` 值（例如从 `800px` 调至 `500px`）；若希望画面更平缓，则调大该值。
- 上传的照片建议比例适中，使用 `object-fit: cover` 自动裁剪填充，以保证最佳的 3D 视觉呈现。

## 扩展思考

- 当前的 3D 效果是整张照片作为一个平面在空间中旋转。如果接入 AI 深度图生成接口，将照片拆分为前景人物和背景，能否实现“人物不动，背景随手机倾斜而移动”的极致裸眼3D视差效果？
- 能否将这种 3D 视差效果导出为动态视频，预装到带有陀螺仪的实体电子相框中，将其转化为高溢价的商业定制产品？
- 如何结合 Canvas 和 WebGL 技术，在 3D 照片上添加动态的光影追踪，使高光位置随手机的倾斜角度发生真实的物理变化？