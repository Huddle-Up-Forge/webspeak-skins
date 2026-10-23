# WebSpeak Skin Store

WebSpeak 官方皮肤分发索引。管理员在 `/admin/skins` 的“皮肤商店”安装，并管理当前实例向访客提供的皮肤。

Official distribution index for the WebSpeak skin store. Administrators install skins at `/admin/skins` and manage which skins their instance offers to visitors.

## 索引 / Index

[`index.json`](index.json) 使用 schemaVersion 1。每一项只记录皮肤稳定 ID 与公开 GitHub 仓库地址：

```json
{
  "schemaVersion": 1,
  "skins": [
    {
      "id": "community.discord-voice",
      "repository": "https://github.com/Huddle-Up-Forge/webspeak-skin-discord-voice"
    }
  ]
}
```

Each entry records a stable skin ID and its public GitHub repository. The index does not contain skin implementations. The first distributed skin is [Discord Voice](https://github.com/Huddle-Up-Forge/webspeak-skin-discord-voice).

## 添加皮肤 / Add a skin

1. 在独立公开仓库维护源码和许可证，构建标准 `.wskin` 包并在 WebSpeak 验证。
2. 在默认分支根目录提供 `skin.json`，声明名称、版本、作者、许可证、最低 WebSpeak 版本，以及归档的 tag/commit、路径和 SHA-256。
3. 将最终归档提交到版本 tag 对应的提交中；不要移动已发布 tag。
4. 提交 PR，将稳定 ID 和仓库地址加入本索引。同 ID 不允许重复。

Maintain the skin source and license in an independent public repository. Publish a validated `.wskin` archive at an immutable version tag or commit. Put `skin.json` on the repository's default branch, then propose its ID and repository URL in `index.json`. Future updates only change the skin repository's metadata; no index update is needed.

The gateway downloads from GitHub's public raw-file service, verifies SHA-256 and manifest identity, checks application compatibility, and runs its normal package importer. Installation does not change the instance default or grant permissions on behalf of visitors. Updates retain the enabled state. A repository outage does not affect installed skins.

完整格式 / Full contract: [Skin development guide](https://github.com/EchoSixHIYA/WebSpeak-client-for-TeamSpeak/blob/master/docs/SKIN_DEVELOPMENT.md).

Packages remain subject to their individual repository licenses.
