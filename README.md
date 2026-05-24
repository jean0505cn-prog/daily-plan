# 我的一日计划

一个可以发布到 GitHub Pages、添加到 iPhone 主屏幕使用的一日计划网页应用。

## 使用方式

1. 在 GitHub Pages 发布本仓库。
2. 用 iPhone Safari 打开发布后的地址。
3. 点分享按钮，选择“添加到主屏幕”，并打开“作为网页 App 打开”。
4. 在 Mac 上打开同一个 GitHub Pages 地址。

## iCloud 私有同步

页面默认仍可使用本机保存；配置 CloudKit 后，会同步到当前登录 Apple Account 的 CloudKit private database。

1. 打开 CloudKit Console，创建或选择一个 iCloud container。
2. 创建 API Token，并把 Allowed Origins 限定为 GitHub Pages origin，例如 `https://jean0505cn-prog.github.io`。
3. 创建 `DailyPlan` record type，并添加字段：
   - `date`: String，开启 Queryable。
   - `payload`: String。
   - `updatedAt`: Double。
4. 复制 `cloudkit-config.example.js` 的结构到 `cloudkit-config.js`，填入真实 `containerIdentifier` 和 `apiToken`。
5. 访问页面并登录 iCloud，首次检测到本机记录时可以同步到 iCloud。

## 数据说明

个人填写内容不会提交到 GitHub。GitHub Pages 只托管静态页面代码；计划内容保存在浏览器本机和登录用户自己的 CloudKit private database 中。
