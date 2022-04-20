# README

1. Super Linter
2. Husky + Lint Staged
3. Commit Msg Check

## Super Linter

[![GitHub Super-Linter](https://github.com/hzz780/super-linter-demo/workflows/Lint%20Code%20Base/badge.svg)](https://github.com/marketplace/actions/super-linter)

### [Super-linter Lint Docs](https://github.com/github/super-linter)

for GitHub Action, 用来做提交后代码检查

### 配置顺序
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
2. 组内默认使用less [22.04.20 目前stylelint暂时不支持less 和 prettier，等PR反馈]
3. 默认会检查 Markdown

## Husky + Lint Staged

1. 首先先确认已经按最新的要求配置了 eslint 和 stylelint
2. npx mrm@2 lint-staged
```json
  {
    "lint-staged": {
      "*.{js,jsx,ts,tsx}": "eslint --cache --fix",
      "*.{css,less}": "stylelint --fix"
    }
  }
```

注意：
node 我们团队node版本使用的是 12、14、16，一直在更新

## Commit Msg Check

0. Copy scripts/verify-commit-msg.js, 记得配一下.eslintignore
1. ```yarn add -D @commitlint/{cli,config-conventional}```
2. ```echo "module.exports = { extends: ['@commitlint/config-conventional'] };" > commitlint.config.js```
3. ```yarn husky add .husky/commit-msg 'yarn commitlint --edit $1'```
4. 确认已经配置了husky

