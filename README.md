# Gordon 的 Rime 配置

朙月拼音·简化字 + 中英混输 + Emoji。详细介绍见博客:<https://guochengqian.github.io/blog/squirrel-rime/>

- `squirrel/` — macOS([Squirrel 鼠须管](https://github.com/rime/squirrel))
- `hamster/` — iOS([Hamster 仓输入法](https://github.com/imfuxiao/Hamster)),待添加

## 功能

- 中文模式下直接打英文单词,无需切换([rime-easy-en](https://github.com/BlindingDark/rime-easy-en))
- 打中文出 Emoji 候选:中国 → 🇨🇳([rime-emoji](https://github.com/rime/rime-emoji))
- `@` 永远直接上屏,方便打邮箱
- Caps Lock 直接上屏字母,Shift 不切换中英文

## 安装(macOS)

```bash
git clone https://github.com/guochengqian/gordon-rime-config.git
cp -R gordon-rime-config/squirrel/* ~/Library/Rime/
```

然后重新部署鼠须管(菜单栏 → 重新部署)。
