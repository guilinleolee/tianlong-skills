# ScreenToGif 快速上手指南

> 3 分钟开始录制！

---

## ✅ 安装状态

**ScreenToGif v2.42.1** 已安装并启动！

**安装位置**: `C:\Program Files\ScreenToGif\ScreenToGif.exe`

**启动方式**:
- ✅ 已自动启动
- 或双击桌面快捷方式
- 或运行：`"C:\Program Files\ScreenToGif\ScreenToGif.exe"`

---

## 🎬 快速录制（5 步）

### Step 1: 选择录制模式
打开 ScreenToGif 后，选择 **"Recorder"**（录制器）

### Step 2: 框选录制区域
- 拖动窗口边缘调整大小
- 建议尺寸：800×600px
- 对准 PowerShell 终端窗口

### Step 3: 开始录制
- 点击 **"Rec"** 按钮（或按 F7）
- 倒计时 3 秒后开始

### Step 4: 执行演示命令
```powershell
# 镜头 1：打开 GitHub 仓库
Start-Process "https://github.com/guilinleolee/tianlong-skills"

# 镜头 2：查看 README
cd C:\Users\li\.openclaw\workspace\tianlong-skills
cat README.md

# 镜头 3：演示 Analyst 技能
# （在 OpenClaw 中输入）
/tianlong-analyst 我想做一个 AI 写作助手

# 镜头 4：演示 Report 技能
/tianlong-report 周报 本周完成：天龙引擎产品化

# 镜头 5：演示 Research 技能
/tianlong-research AI 写作助手竞品分析
```

### Step 5: 停止录制
- 点击 **"Stop"** 按钮（或按 F8）
- 自动进入编辑器

---

## ✏️ 简单编辑

### 添加文字标注
1. 点击顶部菜单 **"Insert"** → **"Title"**
2. 输入文字（如："天龙引擎 Skills 演示"）
3. 拖动到合适位置

### 裁剪多余帧
1. 在下方帧预览中
2. 右键点击不需要的帧
3. 选择 **"Delete"**

### 添加箭头指示
1. 点击 **"Insert"** → **"Arrow"**
2. 拖动绘制箭头
3. 调整颜色和大小

---

## 💾 导出 GIF

### 推荐设置
1. 点击 **"File"** → **"Save as"**
2. 选择格式：**GIF**
3. 点击 **"Options"** 设置：
   - **FPS**: 10-15（文件大小优化）
   - **Quality**: 80-90%
   - **Colors**: 256
   - **Dither**: Floyd-Steinberg

4. 点击 **"Save"**
5. 选择保存位置：`C:\Users\li\.openclaw\workspace\tianlong-skills\docs\demo.gif`

---

## 🎯 录制演示视频（完整流程）

### 准备阶段（2 分钟）
1. 打开 PowerShell
2. 调整字体：16-18px
3. 调整窗口：800×600px
4. 清理桌面（关闭无关通知）

### 录制阶段（10 分钟）
按顺序录制 5 个镜头：

| 镜头 | 内容 | 时长 | 命令 |
|------|------|------|------|
| 1 | GitHub 仓库首页 | 5 秒 | 浏览器打开 |
| 2 | README 技能列表 | 10 秒 | `cat README.md` |
| 3 | Analyst 演示 | 15 秒 | `/tianlong-analyst ...` |
| 4 | Report 演示 | 15 秒 | `/tianlong-report ...` |
| 5 | Research 演示 | 15 秒 | `/tianlong-research ...` |

### 编辑阶段（10 分钟）
1. 添加标题（顶部）
2. 添加步骤说明（底部）
3. 裁剪多余帧
4. 导出 GIF

### 上传阶段（2 分钟）
1. 拖拽 GIF 到 README.md
2. Git 提交推送

**总耗时**: 约 30 分钟

---

## 🔥 快捷键速查

| 功能 | 快捷键 |
|------|--------|
| 开始录制 | F7 |
| 停止录制 | F8 |
| 暂停/继续 | F9 |
| 删除帧 | Delete |
| 撤销 | Ctrl+Z |
| 保存 | Ctrl+S |
| 导出 | Ctrl+E |

---

## 💡 高级技巧

### 1. 录制鼠标点击效果
- 设置 → 录制器 → 显示鼠标点击
- 点击时显示动画效果

### 2. 添加键盘按键显示
- 设置 → 录制器 → 显示按键
- 实时显示按下的键

### 3. 批量导出多个 GIF
- 每个镜头单独录制
- 分别导出
- 在 README 中按顺序展示

### 4. 优化文件大小
- 降低 FPS 到 10
- 减少颜色数量
- 裁剪录制区域

---

## 📤 上传到 GitHub

### 方法 1：直接拖拽
1. 打开 GitHub README.md 编辑页面
2. 拖拽 GIF 文件到编辑区
3. GitHub 自动上传并生成链接

### 方法 2：手动上传
1. 将 GIF 放到 `docs/` 目录
2. Git 提交推送
3. 在 README 中使用相对链接

```markdown
![演示视频](docs/demo.gif)
```

---

## 🎨 示例输出

### 预期效果
```
┌─────────────────────────────────────────┐
│  🐉 天龙引擎 Skills - 产品化套件         │
├─────────────────────────────────────────┤
│                                         │
│  [终端窗口：800×600]                    │
│  - 深色背景                             │
│  - 绿色文字                             │
│  - 清晰可读（16px 字体）                 │
│                                         │
│  [底部：3 个技能列表]                    │
│  - tianlong-analyst（免费）             │
│  - tianlong-report（¥9.9/次）           │
│  - tianlong-research（¥19.9 起）        │
│                                         │
└─────────────────────────────────────────┘
```

### 文件大小目标
- 单个 GIF: <5 MB
- 总大小： <20 MB（5 个镜头）

---

## 🆘 常见问题

### Q: 录制时卡顿？
A: 降低 FPS 到 10，减少录制区域

### Q: 文件太大？
A: 导出时选择更低质量，或裁剪帧数

### Q: 没有声音？
A: ScreenToGif 默认不录声音，如需录音选择"Webcam"模式

### Q: 如何录制浏览器？
A: 同样用 Recorder 模式，框选浏览器窗口即可

---

**准备就绪！开始录制吧！** 🎬

---

**创建时间**: 2026 年 3 月 6 日 09:26  
**状态**: ScreenToGif 已启动，等待录制
