# README

1. Super Linter
2. Husky + Lint Staged
3. commitlint

## 1. Super Linter

[![GitHub Super-Linter](https://github.com/hzz780/super-linter-demo/workflows/Lint%20Code%20Base/badge.svg)](https://github.com/marketplace/actions/super-linter)

### [Super-linter Docs](https://github.com/github/super-linter)

for GitHub Action, 用来做提交后代码检查

### 配置顺序
如果遇到错误或问题，直接参考 super-lint官方文档。这个case 我目前给组内同学看的

1. 复制 .github/workflows/linter.yml
2. 在github仓库的 Settings-Secrets-Actions，点击 New repository secret 添加的 GITHUB_TOKEN
   1. GITHUB_TOKEN 生成 [Personal access tokens](https://github.com/settings/tokens)
   2. 添加Actions secrets 的地方 ``https://github.com/[name]/[repo]/settings/secrets/actions``
3. 确认自己有配置.eslint.json 的配置。 linter.yml的 env的参数 TYPESCRIPT_ES_CONFIG_FILE 需要引用这个参数
4. 在README中添加
   1. ``[![GitHub Super-Linter](https://github.com/[name]/[repo]/workflows/Lint%20Code%20Base/badge.svg)](https://github.com/marketplace/actions/super-linter)``

注意：
1. 默认 git push 只处理非main master分支，main和master分支处理pull request, 可以再 linter.yml中修改
2. 组内默认使用less
3. 默认会检查 Markdown

更多配置可以看linter.yml

### stylelint 团队配置

```text
   yarn add -D stylelint stylelint-config-standard stylelint-config-prettier postcss-less
   
   # .stylelintrc.json
   {
     "extends": ["stylelint-config-standard", "stylelint-config-prettier"],
     "customSyntax": "postcss-less"
   }
```

## 2. Husky + Lint Staged

如果遇到问题，请直接查阅官方文档 [lint-staged](https://www.npmjs.com/package/lint-staged)

1. 首先先确认已经按最新的要求配置了 ESLint 和 stylelint
2. npx mrm@2 lint-staged # 会自动配置好husky和lint-staged
```json
  {
    "lint-staged": {
      "*.{js,jsx,ts,tsx}": "eslint --cache --fix",
      "*.{css,less}": "stylelint --fix"
    }
  }
```

注意：
Node.js 我们团队node版本使用的是 12、14、16，一直在更新

## 3. commitlint

如果有问题，请查看最新的 [commitlint](https://commitlint.js.org/#/guides-local-setup)

推荐使用 [git-cz](https://www.npmjs.com/package/git-cz) 提交代码以确保提交格式正常

0. 确认已经配置了husky
1. ```yarn add -D @commitlint/{cli,config-conventional}```
2. ```echo "module.exports = { extends: ['@commitlint/config-conventional'] };" > commitlint.config.js```
3. ```yarn husky add .husky/commit-msg 'yarn commitlint --edit $1'```


