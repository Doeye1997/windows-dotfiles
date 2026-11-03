# Windows dotfiles

个人使用的 GlazeWM + YASB 配置，基于 [ashish0kumar/windots](https://github.com/ashish0kumar/windots) 调整，采用 Catppuccin Mocha 配色。

这是 2026-11-03 从正在使用的配置导出的快照。仅包含窗口管理器和顶栏，不包含壁纸、浏览器、终端主题或字体文件。

## 文件

| 仓库文件 | 安装位置 |
| --- | --- |
| `glazewm/config.yaml` | `%USERPROFILE%\.glzr\glazewm\config.yaml` |
| `yasb/config.yaml` | `%USERPROFILE%\.config\yasb\config.yaml` |
| `yasb/styles.css` | `%USERPROFILE%\.config\yasb\styles.css` |

导出时将个人目录替换成 `~/Downloads`、`~/Documents` 和 `~/Pictures`。其余行为设置与本机快照一致；注释中的启动程序名称已修正。

## 当前设置

- 顶栏高 40px，在所有显示器上显示。左侧为主菜单、工作区和媒体，中间为时钟，右侧为应用图标、网络、音量、电池和电源菜单。
- 时钟固定为 `Asia/Taipei`，不改变 Windows 时区。
- 工作区显示编号；没有媒体播放时隐藏媒体组件。
- 应用图标为 18px，图标本身不加内边距，避免被压缩或裁切。
- 字体使用 Windows 中注册的名称 `JetBrainsMono NF`。
- 关闭窗口透明度，保留焦点边框，避免腾讯会议等窗口出现透明问题。
- GlazeWM 启动时启动 YASB；此配置不启动 Zebar。
- `Alt+Space` 留给 Raycast。GlazeWM 的窗口类型焦点切换改为 `Alt+Shift+C`。Raycast 需要自行安装并设置快捷键。
- 不含开机启动设置、浮动状态指示器或腾讯会议专用忽略规则。

## 安装与恢复

这份配置此前用于 GlazeWM 3.10.1 和 YASB 2.0.7。其他版本的兼容性未验证。

1. 安装 GlazeWM、YASB 和 JetBrainsMono Nerd Font。图标需要 Nerd Font 字形；安装后检查字体家族名是否为 `JetBrainsMono NF`。
2. 备份上表列出的现有文件，再把仓库文件复制到对应位置。目录不存在时先创建。
3. 检查 GlazeWM 的 `general.startup_commands`：默认使用 `C:/Program Files/YASB/yasb.exe`，自定义安装位置需要修改。
4. 退出正在运行的 Zebar，以免出现两套顶栏。启动 GlazeWM；如果已经运行，按 `Alt+Shift+R` 重载。重载配置不等于重新执行启动命令，首次切换顶栏时可以手动启动 YASB。
5. YASB 已启用配置和样式文件监视。若未更新，可从托盘退出后重新启动。

恢复时，将备份文件放回原位置，再重载 GlazeWM、重新启动原来的顶栏程序。

此仓库只保存配置，不自动修改系统网络端口、防火墙或 Windows 时区。

## 快捷键

以下对应仓库中的实际配置。

| 快捷键 | 功能 |
| --- | --- |
| `Alt+H/J/K/L` 或 `Alt+方向键` | 向左/下/上/右切换焦点 |
| `Alt+Shift+H/J/K/L` 或 `Alt+Shift+方向键` | 移动当前窗口 |
| `Alt+U` / `Alt+P` | 宽度减少 / 增加 2% |
| `Alt+I` / `Alt+O` | 高度减少 / 增加 2% |
| `Alt+R` | 进入调整大小模式，使用 H/J/K/L 或方向键，Esc/Enter 退出 |
| `Alt+V` | 切换平铺方向 |
| `Alt+Shift+Space` | 切换浮动，进入浮动时居中 |
| `Alt+T` | 切换平铺 |
| `Alt+F` | 切换全屏 |
| `Alt+M` | 最小化 |
| `Alt+Shift+C` | 在平铺、浮动、全屏窗口组之间切换焦点 |
| `Alt+Q` | 关闭当前窗口 |
| `Alt+1` 至 `Alt+9` | 切换工作区 |
| `Alt+Shift+1` 至 `Alt+Shift+9` | 将窗口移到工作区并跟随 |
| Alt + 反引号 | 返回最近的工作区 |
| `Alt+Shift+A/F/D/S` | 将整个工作区移到左/右/上/下方显示器 |
| `Alt+Shift+P` | 进入或退出快捷键暂停模式 |
| `Alt+Shift+R` | 重载 GlazeWM 配置 |
| `Alt+Shift+W` | 重绘窗口 |
| `Alt+Shift+E` | 退出 GlazeWM |
| `Alt+Enter` | 打开 Windows Terminal，需要已安装 `wt` |
| `Alt+E` | 打开资源管理器 |

## 使用说明

浮动快捷键改变的是当前窗口状态，不会自动生成永久应用规则。需要长期浮动或忽略某个应用时，编辑 `window_rules`。

同一工作区只有一个平铺窗口时，该窗口会占满可用区域。其他窗口若处于浮动状态，不会自动与它并排。

顶栏没有开启天气、CPU 或内存组件。截图未随此次快照发布；上游截图仅代表原作者的完整桌面，不能视为此配置的实测效果图。

## 来源与许可

- 配置及样式基于 [windots](https://github.com/ashish0kumar/windots)，保留其 MIT 许可证及原作者版权声明，见 `LICENSE`。
- 窗口管理器：[GlazeWM](https://github.com/glzr-io/glazewm)。
- 顶栏：[YASB](https://github.com/amnweb/yasb)。
- 配色：[Catppuccin](https://github.com/catppuccin/catppuccin)。
- 字体：[Nerd Fonts](https://github.com/ryanoasis/nerd-fonts)。

上述软件和字体各自遵循其许可证；本仓库不分发其二进制文件。
