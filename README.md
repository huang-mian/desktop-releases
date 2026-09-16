# desktop-releases

Claude Desktop + Codex Desktop 版本清单与镜像安装包（PingAI 桌面端分发）。

## 目录结构

```
claude/versions.json   # Claude Desktop 版本清单
codex/versions.json    # Codex Desktop 版本清单
```

## versions.json schema

```json
{
  "schema": 1,
  "platforms": {
    "win32-x64": {
      "latest": "1.30096.1",
      "versions": {
        "1.30096.1": {
          "kind": "exe",
          "official": "https://downloads.claude.ai/...",
          "mirror": "https://github.com/.../releases/download/...",
          "sha256": "a255..."
        }
      }
    }
  }
}
```

## CDN 加速

清单文件通过 jsDelivr CDN 分发，香港用户无需直连 GitHub：

https://cdn.jsdelivr.net/gh/huang-mian/desktop-releases@main/claude/versions.json

## 镜像安装包

安装包通过 GitHub Releases 分发。如 HK 网络访问 GitHub Releases 缓慢，桌面端支持环境变量 `PINGAI_DOWNLOAD_MIRROR` 为 GitHub 下载 URL 添加镜像前缀（如 `https://ghproxy.com/`）。

## 安装包上传

```bash
# 1. 计算 SHA256
sha256sum Claude-Setup-x.x.x.exe

# 2. 创建 GitHub Release 并上传
gh release create vx.x.x Claude-Setup-x.x.x.exe --repo huang-mian/desktop-releases

# 3. 更新相应的 versions.json，填入 mirror URL 和 sha256
```
