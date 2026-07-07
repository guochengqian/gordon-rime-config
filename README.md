# Gordon's Rime Config

My [Squirrel](https://github.com/rime/squirrel) (Rime input method for macOS) configuration:
朙月拼音·简化字 with inline English mixed input and emoji suggestions.

## Features

- **朙月拼音·简化字** (`luna_pinyin_simp`) as the main schema, 5 candidates per page.
- **Inline English** via [rime-easy-en](https://github.com/BlindingDark/rime-easy-en):
  type English words directly in Chinese mode without switching
  (sentence mode and completion noise tuned down; `@` always commits as plain
  half-width `@`, handy for emails and handles).
- **Emoji suggestions** via [rime-emoji](https://github.com/rime/rime-emoji):
  typing 中国 also offers 🇨🇳, 微笑 offers 🙂, etc. Toggle with the 🈶️/🈚️
  switch in the schema menu (<kbd>Ctrl</kbd>+<kbd>`</kbd> or <kbd>F4</kbd>).
- **Caps Lock** commits the composition code instead of toggling layouts;
  Shift keys do nothing (no accidental mode switches).
- Horizontal stacked candidate window; inline candidate disabled in iTerm2.

## Install

```bash
git clone <this-repo-url>
cp -R gordon-rime-config/* ~/Library/Rime/
```

Then redeploy Squirrel (menu bar → 重新部署, or
`"/Library/Input Methods/Squirrel.app/Contents/MacOS/Squirrel" --reload`).

The base schemas (`luna_pinyin`, `luna_pinyin_simp`) ship with Squirrel itself,
so only the patches and dictionaries here are needed. Optionally add your own
`custom_phrase.txt` for personal shortcut phrases (not included here).

## Gotcha worth knowing

`luna_pinyin_simp.schema.yaml` redefines `switches` after an `__include`, and
librime's config compiler mishandles a `switches/+` append against that — it
silently **replaces** the whole list, dropping the `zh_simp` switch so output
falls back to traditional Chinese. That is why
`luna_pinyin_simp.custom.yaml` patches the **full** switches list instead of
appending. The emoji filter must also sit **before** the built-in `simplifier`,
because the emoji dictionary is keyed on traditional Chinese.

## Credits

- [rime/squirrel](https://github.com/rime/squirrel) — the macOS Rime frontend
- [rime/rime-emoji](https://github.com/rime/rime-emoji) — emoji OpenCC data (`opencc/emoji*`)
- [BlindingDark/rime-easy-en](https://github.com/BlindingDark/rime-easy-en) — inline English (`easy_en*`, `lua/easy_en.lua`)
