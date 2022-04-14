# README

[![GitHub Super-Linter](https://github.com/hzz780/super-linter-demo/workflows/Lint%20Code%20Base/badge.svg)](https://github.com/marketplace/actions/super-linter)

## [Super-linter Lint](https://github.com/github/super-linter)

for GitHub Action, 用来做提交后代码检查

## 配置顺序
如果遇到错误或问题，直接参考 super-lint官方文档。这个case 我目前给组内同学看的

1. 复制 .github/workflows/linter.yml
2. 在github仓库的 Settings-Secrets-Actions，点击 New repository secret 添加的 GITHUB_TOKEN
   1. GITHUB_TOKEN 生成 [Personal access tokens](https://github.com/settings/tokens)
   2. 添加Actions secrets 的地方 ``https://github.com/[name]/[repo]/settings/secrets/actions``
3. 确认自己有配置.eslint.json的配置。 linter.yml的 env的参数 TYPESCRIPT_ES_CONFIG_FILE 需要引用这个参数
4. 在README中添加
   1. ``[![GitHub Super-Linter](https://github.com/[name]/[repo]/workflows/Lint%20Code%20Base/badge.svg)](https://github.com/marketplace/actions/super-linter)``

注意：
1. git push 只处理非main master分支，main和master分支处理pull request
2. 不检查CSS，组内默认使用less
3. 会检查 markdown





