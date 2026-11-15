# mino-mac-build

Mino macOS 安装包的公壳构建仓：公仓只为吃 GitHub 对 public repo 免费的
macOS runner 额度；产品源码在私仓 `694410194/mino-agent`（BASE + format-patch
备份形态），workflow 用只读 deploy key checkout 后现场重建。

- 触发：Actions → mac-build → Run workflow（`workflow_dispatch`）。
- 产物：run 页 artifacts `mino-mac-arm64-unsigned-*`（未签名 dmg，
  首装需右键打开或 `xattr -dr com.apple.quarantine`）。
- secrets：`MAC_BUILD_SSH_KEY`（mino-agent 部署密钥私钥）、`MAC_BUILD_KNOWN_HOSTS`。
- 注意：新仓/重建后若 workflow 不被 Actions 索引（`total_count:0`），
  改本仓 workflow 文件任意一行再推即可强制重索引（GitHub 已知 bug，
  空 commit 不触发）。
