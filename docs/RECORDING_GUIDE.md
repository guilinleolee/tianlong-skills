# 天龙引擎 Skills 演示视频录制指南

> 3 种方案，任选其一

---

## 📊 环境检查结果

| 工具 | 状态 | 说明 |
|------|------|------|
| ffmpeg | ✅ 已安装 | 命令行录制 |
| Node.js | ✅ v22.21.1 | 可安装 terminal-recorder |
| ScreenToGif | ⏳ 需下载 | Windows 最佳免费选择 |
| LICEcap | ❌ 未安装 | 跨平台轻量选择 |
| OBS | ❌ 未安装 | 专业录制（可选） |

---

## 🎯 方案 A：ScreenToGif（推荐 ⭐⭐⭐⭐⭐）

**优势**：
- ✅ 免费、开源、无水印
- ✅ 录制 + 编辑一体化
- ✅ 支持添加文字标注
- ✅ 直接导出 GIF
- ✅ 文件大小优化好

**下载**：https://www.screentogif.com/

**录制步骤**：
1. 下载并解压（无需安装）
2. 打开 ScreenToGif.exe
3. 选择"Recorder"（录制器）
4. 框选终端窗口（建议 800×600）
5. 点击"Rec"开始录制
6. 执行演示命令
7. 点击"Stop"停止
8. 进入编辑器添加文字/箭头
9. 文件 → 另存为 → 选择 GIF
10. 优化设置：帧率 10-15 FPS

**预期文件大小**：2-5 MB（60 秒）

---

## 🎯 方案 B：ffmpeg 命令行（极客选择 ⭐⭐⭐⭐）

**优势**：
- ✅ 已安装，无需下载
- ✅ 可脚本化自动化
- ✅ 高质量输出

**录制步骤**：

### 1. 录制终端窗口
```powershell
# 获取终端窗口句柄
Get-Process | Where-Object { $_.MainWindowTitle -like "*PowerShell*" } | Select-Object Id, MainWindowTitle

# 录制屏幕（全屏）
ffmpeg -f gdigrab -framerate 30 -i desktop -t 60 output.mp4

# 录制指定窗口（需要窗口标题）
ffmpeg -f gdigrab -framerate 30 -i title="Windows PowerShell" -t 60 output.mp4
```

### 2. 转换为 GIF
```powershell
# 生成调色板
ffmpeg -i output.mp4 -vf "fps=10,scale=800:-1:flags=lanczos,palettegen" palette.png

# 转换为 GIF
ffmpeg -i output.mp4 -i palette.png -lavfi "fps=10,scale=800:-1:flags=lanczos[x];[x][1:v]paletteuse" output.gif
```

### 3. 优化文件大小
```powershell
# 降低帧率到 10 FPS
ffmpeg -i output.gif -vf "fps=10" output_optimized.gif
```

---

## 🎯 方案 C：LICEcap（轻量选择 ⭐⭐⭐）

**优势**：
- ✅ 超轻量（<1MB）
- ✅ 直接录制为 GIF
- ✅ 跨平台

**下载**：https://www.cockos.com/licecap/

**录制步骤**：
1. 下载并安装
2. 打开 LICEcap
3. 调整录制窗口大小
4. 点击"Record"
5. 选择保存路径
6. 执行演示命令
7. 点击"Stop"

---

## 🎯 方案 D：terminal-recorder（Node.js 方案 ⭐⭐⭐）

**优势**：
- ✅ 专门录制终端
- ✅ 支持回放
- ✅ 可导出多种格式

**安装**：
```powershell
npm install -g terminal-recorder
```

**录制**：
```powershell
# 开始录制
tr record demo.trc

# 执行演示命令...

# 停止录制（Ctrl+C）

# 导出为 GIF
tr export demo.trc --format gif --output demo.gif
```

---

## 📋 演示脚本（60 秒版）

### 镜头清单

| 镜头 | 时长 | 内容 | 命令 |
|------|------|------|------|
| 1 | 5 秒 | 开场 | - |
| 2 | 10 秒 | 技能列表 | `cat README.md` |
| 3 | 15 秒 | Analyst 演示 | `/tianlong-analyst ...` |
| 4 | 15 秒 | Report 演示 | `/tianlong-report ...` |
| 5 | 15 秒 | Research 演示 | `/tianlong-research ...` |

---

## 🎨 录制设置建议

### 终端配置
```powershell
# 字体大小
字体：Cascadia Code 或 Consolas
大小：16-18px

# 颜色方案（推荐 One Dark）
背景：#282C34
前景：#ABB2BF
强调色：#61AFEF
```

### 窗口尺寸
- 宽度：800px
- 高度：600px
- 帧率：10-15 FPS

### 文件大小目标
- 单个 GIF：<5 MB
- 总大小：<20 MB（5 个镜头）

---

## 📤 后期处理

### 1. 裁剪多余边框
```powershell
ffmpeg -i input.gif -vf "crop=800:600:0:0" output_cropped.gif
```

### 2. 添加文字标注
使用 ScreenToGif 编辑器：
- 添加标题（顶部）
- 添加步骤说明（底部）
- 添加箭头指示

### 3. 优化文件大小
```powershell
# 减少颜色数量
ffmpeg -i input.gif -vf "split[s][pal];[pal]palettegen=stats_mode=diff[pal];[s][pal]paletteuse=new=1" output_optimized.gif
```

---

## ✅ 录制检查清单

- [ ] 终端字体清晰可读（≥16px）
- [ ] 窗口尺寸合适（800×600）
- [ ] 背景干净（关闭无关通知）
- [ ] 命令执行流畅（无错误）
- [ ] 输出结果完整显示
- [ ] 总时长≤60 秒
- [ ] 文件大小<5 MB/个
- [ ] 添加文字标注（可选）
- [ ] 导出为 GIF 格式
- [ ] 上传到 GitHub README

---

## 🚀 快速开始（推荐流程）

1. **下载 ScreenToGif**（5 分钟）
   - https://www.screentogif.com/
   
2. **准备终端环境**（2 分钟）
   - 打开 PowerShell
   - 调整字体大小到 16px
   - 调整窗口到 800×600

3. **录制镜头**（10 分钟）
   - 按脚本执行 5 个镜头
   - 每个镜头单独录制

4. **编辑优化**（10 分钟）
   - 添加文字标注
   - 裁剪多余边框
   - 导出优化 GIF

5. **上传 GitHub**（2 分钟）
   - 拖拽到 README.md
   - 提交推送

**总耗时**：约 30 分钟

---

**准备时间**: 2026 年 3 月 6 日 09:20  
**准备人**: 李依依（一一）
