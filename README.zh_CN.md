<p align="right">
  <a href="README.md">English</a> · <strong>简体中文</strong>
</p>

# coopa-store

Coopa Store 的公开部分:官方游戏检查在这里跑,只用公开的 Coopa SDK,没有任何密钥。

- `.github/workflows/check-core.yml`:可复用的检查(网页版部分在 Emscripten 里,卡上版部分在 ESP-IDF 里)。游戏模板的「自查」也调它,开发者看到的结果和商店一样。
- `.github/workflows/check.yml`:官方检查。以后由官网触发;现在手动:

```bash
gh workflow run check.yml -R coopa-store-dev/coopa-store -f repo=OWNER/NAME -f ref=COMMIT
```

结果(JSON、截图、能玩的网页版)在这次运行的 Artifacts 里。现在只能查公开的游戏仓库。

商店目录在 `catalog.toml`(图标在 `icons/`)。官网审核通过、下架、退回版本时自动改它,构建服务每分钟拉一次,卡上「刷新目录」就能看到。不要手改。
