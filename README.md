# 智能变化检测系统使用说明书

## 版本 v70.1.8

### 1. 产品概述
智能变化检测系统是一款能够实时监控屏幕区域或摄像头画面变化的专业工具。它可以检测画面中的动态变化，并用醒目标记框出变化区域，适用于多种场景：

- **安防监控**：检测监控画面中的异常移动
- **软件测试**：记录UI界面变化
- **游戏开发**：捕捉游戏画面变化
- **教学演示**：展示动态过程
- **工业检测**：监控生产线变化

### 2. 系统要求
- 操作系统：Windows 7/10/11
- Python 3.6+
- 推荐硬件配置：
  - CPU：Intel i5 或同等性能以上
  - 内存：4GB以上
  - 显卡：支持CUDA的NVIDIA显卡(可选)

### 3. 安装说明
1. 确保已安装Python 3.6+
2. 安装依赖库：
   ```
   pip install opencv-python numpy pillow mss psutil pywin32
   ```
3. 可选加速库(根据需要安装)：
   ```
   pip install numba pytorch opencv-contrib-python
   ```

### 4. 界面说明

![控制面板示意图](https://github.com/user-attachments/assets/391c7bab-db7b-4df7-bcc5-eb1ce60afc9e)


#### 主界面区域
1. **视频显示区**：中央黑色区域，显示监控画面和检测结果
2. **控制面板**：可折叠区域，包含所有控制选项
3. **状态栏**：底部显示系统状态、帧率和CPU使用率

#### 控制面板功能
- **监控源选择**：选择监控进程或摄像头
- **检测参数设置**：调整检测灵敏度
- **加速设置**：选择计算加速方式

### 5. 使用指南

#### 基本使用步骤
1. 启动程序
2. 点击"选择监控进程"或"选择镜头监控"
3. 如需监控特定区域，点击"选择监控区域"
4. 调整参数获得最佳检测效果
5. 观察画面中的变化检测框

#### 详细功能说明

**1. 选择监控源**
- **监控进程**：选择正在运行的应用程序窗口
- **监控摄像头**：选择连接的摄像头设备

**2. 参数调整**
- **帧率(FPS)**：控制检测刷新率(1-360)
- **变化阈值**：调整变化检测灵敏度(1-100)
- **最小区域**：设置最小检测区域大小(1-1000像素)

**3. 高级设置**
- **加速后端**：选择计算加速方式(自动/CPU/CUDA/OpenCL等)
- **保持比例**：保持画面原始宽高比
- **总是置顶**：窗口保持在最前

### 6. 技术原理

#### 变化检测算法
1. 连续捕获两帧画面
2. 转换为灰度图像
3. 计算绝对差异
4. 二值化处理
5. 查找轮廓并过滤小区域

#### 性能优化
系统支持多种加速方式：
- **CUDA**：使用NVIDIA GPU加速
- **OpenCL**：使用通用GPU加速
- **Numba**：使用JIT编译加速
- **PyTorch**：使用深度学习框架加速
- **CPU**：纯CPU计算(兼容性最好)

### 7. 应用场景示例

#### 示例1：软件测试
1. 选择被测应用程序窗口
2. 设置帧率30FPS
3. 执行测试用例
4. 系统自动记录所有界面变化

#### 示例2：家庭安防
1. 连接监控摄像头
2. 设置变化阈值为20
3. 最小区域设为200
4. 当有人进入监控区域时会自动标记

#### 示例3：工业检测
1. 对准生产线检测区域
2. 设置高帧率(60FPS)
3. 使用CUDA加速
4. 实时检测产品缺陷

### 8. 常见问题解答

**Q1: 为什么检测不到变化？**
A: 可能原因：
- 变化阈值设置过高
- 最小区域设置过大
- 监控区域选择不正确

**Q2: 系统卡顿怎么办？**
A: 解决方案：
- 降低帧率设置
- 选择更高效的加速方式
- 缩小监控区域

**Q3: 如何提高检测精度？**
A: 建议：
- 适当降低变化阈值
- 减小最小区域值
- 确保监控画面光照充足

### 9. 专业参数说明

#### 技术参数
- 最大分辨率：取决于硬件性能
- 检测延迟：<50ms(取决于设置)
- 支持色彩空间：BGR/RGB

#### 编程接口
开发者可以通过修改以下全局变量调整系统行为：
```python
threshold = 30  # 变化检测阈值
min_contour_area = 500  # 最小变化区域
frame_rate = 60  # 帧率
lock_aspect_ratio = True  # 是否锁定宽高比
```

### 10. 版本更新说明
- v70.1.8 更新：
  - 新增PyTorch加速后端
  - 优化多线程处理
  - 修复已知BUG

### 11. 技术支持
如有任何问题，请联系开发者：杜玛

---
本说明书适用于各行业用户，从普通用户到专业开发者都能找到所需信息。系统设计兼顾易用性和专业性，可根据需要灵活调整使用方式。
