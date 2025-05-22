# Ubuntu中的meme生成器的安装步骤

## 下载源码
```bash
mkdir ~/memeGenerator
```
```bash
cd ~/memeGenerator
```
```bash
git clone https://github.com/misaka20002/meme-generator.git
```
## 创建虚拟环境安装依赖
```bash
cd ~/memeGenerator/meme-generator
```
```bash
venv\Scripts\activate
```
```bash
source venv/bin/activate
```
```bash
python -m pip install .
```
## 创建配置文件
```bash
mkdir ~/.config/meme_generator
```
```bash
vim ~/.config/meme_generator/config.toml
```
粘贴以下内容
```toml
[meme]
load_builtin_memes = true  # 是否加载内置表情包
meme_dirs = ["/root/memeGenerator/meme-generator-contrib/memes"]  # 加载其他位置的表情包，填写文件夹路径
meme_disabled_list = []  # 禁用的表情包列表，填写表情的 `key`

[resource]
# 下载内置表情包图片时的资源链接，下载时选择最快的站点
resource_urls = [
  "https://raw.githubusercontent.com/MeetWq/meme-generator/",
  "https://ghproxy.com/https://raw.githubusercontent.com/MeetWq/meme-generator/",
  "https://fastly.jsdelivr.net/gh/MeetWq/meme-generator@",
  "https://raw.fastgit.org/MeetWq/meme-generator/",
  "https://raw.fgit.ml/MeetWq/meme-generator/",
  "https://raw.gitmirror.com/MeetWq/meme-generator/",
  "https://raw.kgithub.com/MeetWq/meme-generator/",
]

[gif]
gif_max_size = 10.0  # 限制生成的 gif 文件大小，单位为 Mb
gif_max_frames = 100  # 限制生成的 gif 文件帧数

[translate]
baidu_trans_appid = ""  # 百度翻译api相关，表情包 `dianzhongdian` 需要使用
baidu_trans_apikey = ""  # 可在 百度翻译开放平台 (http://api.fanyi.baidu.com) 申请

[server]
host = "0.0.0.0"  # web server 监听地址
port = 50835  # web server 端口

[log]
log_level = "INFO"  # 日志等级
```
vim保存文件
```bash
:wq 
```
## 下载图片
- 下载默认图片
```bash
python -m meme_generator.cli meme download
```
- 可选：
  - 查看帮助
    ```
    python -m meme_generator.cli meme help
    ```
- 下载额外图片
```bash
mkdir /root/memeGenerator
```
```bash
cd /root/memeGenerator
```
```bash
git clone https://github.com/misaka20002/meme-generator-contrib.git
```
## 安装字体
```bash
sudo apt install fonts-noto-cjk fonts-noto-color-emoji
```
```bash
cp ~/memeGenerator/meme-generator/resources/fonts/* /usr/share/fonts
```
## 开放 50835端口
- 自行去服务器防火墙开启TDP端口50835
# 运行meme web服务器
```bash
cd ~/memeGenerator/meme-generator
source venv/bin/activate
python -m meme_generator.app
```
## 报错
### 若报错 ImportError: libGL.so.1: cannot open shared object file: No such file or directory
- 这个错误通常是由于缺少OpenGL库引起的（重新安装了一次依赖不行，是原作者没写入这个依赖进去）
```bash
sudo apt-get update
sudo apt-get install python3-opengl
```

### 欢迎入群 285744328 
# 完






<div align="center">

<img src="https://s2.loli.net/2023/03/26/4URd1BKj3ToycLl.png" width=200 />

# meme-generator

_✨ 表情包生成器，用于制作各种沙雕表情包 ✨_

<p align="center">
  <img src="https://img.shields.io/github/license/MemeCrafters/meme-generator" alt="license">
  <img src="https://img.shields.io/badge/python-3.9+-blue.svg" alt="Python">
  <a href="https://pypi.org/project/meme-generator">
    <img src="https://badgen.net/pypi/v/meme-generator" alt="pypi">
  </a>
  <a href="https://jq.qq.com/?_wv=1027&k=wDVNrMdr">
    <img src="https://img.shields.io/badge/QQ%E7%BE%A4-682145034-orange" alt="qq group">
  </a>
</p>

</div>

> [!NOTE]
> 本项目另有 Rust 重构版 [--> meme-generator-rs <--](https://github.com/MemeCrafters/meme-generator-rs)
> 
> 拥有更小的内存占用和更快的运行速度，欢迎使用！

## 表情列表

表情详细信息、表情预览等可以在 [--> 表情列表 <--](https://github.com/MemeCrafters/meme-generator/wiki/%E8%A1%A8%E6%83%85%E5%88%97%E8%A1%A8) 查看

## 安装、使用、配置

详见 Wiki：[--> Wiki <--](https://github.com/MemeCrafters/meme-generator/wiki)

## 其他表情

可以加载非本仓库内置的表情，参考 [--> 加载其他表情 <--](https://github.com/MemeCrafters/meme-generator/wiki/%E5%8A%A0%E8%BD%BD%E5%85%B6%E4%BB%96%E8%A1%A8%E6%83%85)

其他表情仓库：
- [MemeCrafters/meme-generator-contrib](https://github.com/MemeCrafters/meme-generator-contrib) meme-generator 额外表情仓库
- [anyliew/meme_emoji](https://github.com/anyliew/meme_emoji) 更多热门表情包模板

## 声明

本仓库的表情素材等均来自网络，如有侵权请联系作者删除

## 鸣谢

本仓库的表情整合自原 [nonebot-plugin-petpet](https://github.com/noneplugin/nonebot-plugin-petpet) 和 [nonebot-plugin-memes](https://github.com/noneplugin/nonebot-plugin-memes) 仓库

感谢以下开发者作出的贡献：

<a href="https://github.com/noneplugin/nonebot-plugin-petpet/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=noneplugin/nonebot-plugin-petpet&max=1000" />
</a>

部分表情素材或代码参考了以下项目，感谢这些项目的开发者们

- [Ailitonia/omega-miya](https://github.com/Ailitonia/omega-miya) 基于nonebot2的qq机器人
- [FloatTech/ZeroBot-Plugin](https://github.com/FloatTech/ZeroBot-Plugin) 基于 ZeroBot 的 OneBot 插件
- [HibiKier/zhenxun_bot](https://github.com/HibiKier/zhenxun_bot) 基于 Nonebot2 和 go-cqhttp 开发，以 postgresql 作为数据库，非常可爱的绪山真寻bot
- [SAGIRI-kawaii/sagiri-bot](https://github.com/SAGIRI-kawaii/sagiri-bot) 基于Graia Ariadne和Mirai的QQ机器人 SAGIRI-BOT
- [Dituon/petpet](https://github.com/Dituon/petpet) Mirai插件 生成各种奇怪的图片
- [kexue-z/nonebot-plugin-nokia](https://github.com/kexue-z/nonebot-plugin-nokia) 诺基亚手机图生成
- [RafuiiChan/nonebot_plugin_charpic](https://github.com/RafuiiChan/nonebot_plugin_charpic) 字符画生成插件
