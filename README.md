<p align="right">
  <strong>English</strong> · <a href="README.zh_CN.md">简体中文</a>
</p>

# coopa-store

The public side of the Coopa Store: the official game check runs here, with the public Coopa SDK only and no secrets.

- `.github/workflows/check-core.yml`: the reusable check (web part in Emscripten, card part in ESP-IDF). Game templates call it for their self-check, so developers see the same result the store sees.
- `.github/workflows/check.yml`: the official check. The website will trigger it; for now run it by hand:

```bash
gh workflow run check.yml -R coopa-store-dev/coopa-store -f repo=OWNER/NAME -f ref=COMMIT
```

Results (JSON, screenshots, the playable web build) are in the run's artifacts. Only public game repositories can be checked for now.

The store catalog is `catalog.toml` (icons in `icons/`). The website updates it when a game is approved, delisted or reverted; the build service pulls it every minute and cards see it after refreshing the catalog. Do not edit it by hand.
