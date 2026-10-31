# danvric GitHub Profile 更新包：部署说明

本包用于你现有的公开仓库：`https://github.com/danvric/danvric`。不需要新建仓库。

## 包含内容

- `README.md`：完整个人主页，英文展示，包含五个公开项目、兴趣方向、统计与赞助说明。
- `assets/profile-banner.jpg`：全球、科技、金融主题横幅。
- `.github/workflows/update-profile-cards.yml`：每日生成统计卡和语言分布卡；统计卡会显示真实的第三方 Rank（可能是 A+，也可能是其他等级）。
- `.github/workflows/generate-snake.yml`：生成浅色和深色贡献蛇 SVG，发布到 `output` 分支。
- `.github/FUNDING.template.yml`：未啟用的贊助設定範本；確認收款資格與收款頁可用後才改名為 `FUNDING.yml`。
- `profile/.gitkeep`：确保用于保存统计卡的目录存在。

## 部署方法（推荐：本地覆盖现有仓库）

1. 打开 `https://github.com/danvric/danvric`，确认默认分支为 `main`。
2. 将仓库克隆到电脑：

   ```bash
   git clone https://github.com/danvric/danvric.git
   ```

3. 解压本包，把包内文件和文件夹复制到克隆仓库的根目录，允许覆盖同名文件。
4. 在该仓库目录执行：

   ```bash
   git add README.md assets .github/workflows profile
   git commit -m "Redesign GitHub profile"
   git push
   ```

5. 打开仓库的 **Actions** 页面，分别手动运行 `Update Profile Cards` 和 `Generate Contribution Snake`。
6. 第一个工作流成功后，检查 `profile/stats.svg` 和 `profile/top-langs.svg` 是否生成；第二个工作流成功后，检查是否出现 `output` 分支，以及其中是否有 `github-snake.svg` 和 `github-snake-dark.svg`。
7. 打开 `https://github.com/danvric` 查看主页。

## GitHub Actions 权限

在仓库 **Settings → Actions → General → Workflow permissions** 中，选择允许工作流读写仓库内容的权限（`Read and write permissions`）。工作流文件也声明了 `contents: write`。

## A+ 评级是什么

统计工作流使用 GitHub Readme Stats Action。统计卡默认显示算法评级，不再使用旧版本的 `hide_rank=true`。A+ 不是 GitHub 官方认证；评级根据公开 GitHub 活动指标计算。当前账号数据不足或贡献较少时，可能显示较低等级，这是正常且真实的结果。不要手动把评级改成 A+。

## GitHub Achievements

官方 Achievements 由 GitHub 根据实际活动授予，并显示在 GitHub 个人资料页面。README 只链接到个人资料，不把第三方 Trophy 卡片冒充官方徽章。

## Support Me / 赞助入口

README 已加入可以立即使用的非金钱支持入口：Star、Issue、Pull Request、分享项目。

金融赞助按钮暂时没有绑定到未经验证的收款页面。原因是 GitHub Sponsors 和 Buy Me a Coffee 的收款地区均有限制：GitHub Sponsors 当前支持收款地区名单包括香港、澳门、法国等，但不包括中国大陆；Buy Me a Coffee 的 Stripe 收款名单同样没有中国大陆。若你的法律居住地、税务资料和收款银行位于受支持地区，可以按平台要求申请；仅仅短期身处某个国家不等于满足收款资格。

官方资料：

- GitHub Sponsors 地区与资格：https://docs.github.com/en/sponsors/getting-started-with-github-sponsors/about-github-sponsors
- GitHub Sponsors 个人账户设置：https://docs.github.com/en/sponsors/receiving-sponsorships-through-github-sponsors/setting-up-github-sponsors-for-your-personal-account
- Buy Me a Coffee 收款地区：https://help.buymeacoffee.com/en/articles/6258038-supported-countries-for-payouts-on-buy-me-a-coffee
- GitHub FUNDING.yml 说明：https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/displaying-a-sponsor-button-in-your-repository

确认支付平台能让你合法收款后，把 `.github/FUNDING.template.yml` 复制为 `.github/FUNDING.yml`，配置实际的 `github`、`ko_fi`、`buy_me_a_coffee` 或 `custom` 用户名/链接，并在 README 中加上对应的赞助按钮。不要使用虚假地区或他人收款账号绕过审核。

## 调整方式

- 更换横幅：替换 `assets/profile-banner.jpg`，并保持相同路径；也可以修改 README 中的图片路径。
- 更改统计卡颜色：编辑 `.github/workflows/update-profile-cards.yml` 中的 `title_color`、`text_color`、`icon_color`、`border_color`。
- 如果你的默认分支不是 `main`：同时调整 `generate-snake.yml` 中 `push.branches`。
