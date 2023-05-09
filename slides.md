---
layout: cover
highlighter: shiki
---

<div class="tracking-widest" style="font-size: 40px">
使用 <span style="color: #90a697;font-weight: bold">Next.js</span> 和 <span style="color: #90a697;font-weight: bold">Turbopack</span> 搭建项目
</div>

<div class="uppercase text-sm tracking-widest my-10">
Lzzzs
</div>

---

# 梁振胜

<div class="leading-8 opacity-80">
前端爱好者，喜欢探索新技术<br>
开源爱好者，梦想做全职开源<br>
<strong>unplugin-vue-macros</strong> 中文文档维护者<br>
<br>
</div>

<div class="my-10 grid grid-cols-[40px,1fr] w-min gap-y-4">
  <ri-github-line class="opacity-50"/>
  <div><a href="https://github.com/Lzzzs" target="_blank">Lzzzs</a></div>
  <ri-twitter-line class="opacity-50"/>
  <div><a href="https://twitter.com/lzzzzzzzssssss" target="_blank">lzzzzzzzssssss</a></div>
  <ri-user-3-line class="opacity-50"/>
  <div><a href="http://lzzzs.top" target="_blank">lzzzs.top</a></div>
</div>

## <img src="https://avatars.githubusercontent.com/u/74575471?v=4" class="rounded-full w-40 abs-tr mt-16 mr-12"/>

---

<div class="flex">
  <h1><strong><i>Next.js</i></strong> 是什么？</h1>
  <h1 v-click>✅</h1>
</div>
<div class="flex"  style="margin-top:40px">
  <h1 v-click tracking-widest>为什么选择用 <strong><i>Next.js</i></strong> 而不是 <strong><i>React.js</i></strong> ？</h1>
  <h1 v-click>✅</h1>
</div>
<div class="flex" style="margin-top:40px">
  <h1 v-click><strong><i> Turbopack </i></strong> 是什么？</h1>
  <h1 v-click>✅</h1>
</div>
<div class="flex" style="margin-top:40px">
  <h1 v-click>为什么选择用 <strong><i>Turbopack</i></strong> 而不是 <strong><i>Vite</i></strong> ？</h1>
  <h1 v-click>✅</h1>
</div>

---

# 包管理器的选择

<div class="flex"  style="margin-top:20px">
  <h2 v-click> npm / cnpm </h2>
  <h2 v-click class="ml-6">🙅‍♂️</h2>
</div>

<div class="flex" style="margin-top:40px">
  <h2 v-click> Yarn </h2>
  <h2 v-click style="margin-left: 120px;">🙅‍♂️</h2>
</div>

<img v-click src="/node_modules.webp" class="abs-tr" style="width: 300px;height: 150px;top:100px;right: 20px" />

<div class="flex" style="margin-top:40px">
  <h2 v-click> Bun </h2>
  <h2 v-click class="ml-6" style="margin-left: 125px;">🧪</h2>
</div>

<img v-click src="/Bun.jpg" class="abs-tr" style="top: 43%; left: 40%"  />

<div class="flex" style="margin-top:40px">
  <h2 v-click> pnpm </h2>
  <h2 v-click class="ml-6" style="margin-left: 100px;">💘</h2>
</div>

<img v-click src="/ni.jpg" class="abs-tr" style="width: 300px;height: 250px;top: 50%; right:20px"  />

---

```shell
npm init -y
pnpm add next@latest react@latest react-dom@latest
```

- 推荐 ni

- 添加 script 脚本
  ```json
   "dev": "next dev --turbo",
   "build: "next build",
  ```
- 根目录下创建 pages 文件夹
  - 文件夹下添加 index.tsx
    ```tsx
    export default function Index() {
      return <div>hello world</div>;
    }
    ```
- 集成 tailwindcss

```shell
ni -D tailwindcss postcss autoprefixer
npx tailwindcss init -p # 自动生成tailwind.config.js 和 postcss.config.js
```

- 修改 tailwindcss.js

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    './app/**/*.{js,ts,jsx,tsx,mdx}',
    './pages/**/*.{js,ts,jsx,tsx,mdx}',
    './components/**/*.{js,ts,jsx,tsx,mdx}',
  ],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

- app 文件夹下添加 global.css

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

- app/layout.tsx 中引入 global.css
  import './global.css';

- 运行 `nr dev` 启动项目

---

```shell
ni -D eslint @antfu/eslint-config
```

- 创建 .eslintrc.js

```js
{
  "extends": "@antfu"
}
```

- package.json 中添加 script

```json
{
  "scripts": {
    "lint": "eslint .",
    "lint:fix": "eslint . --fix"
  }
}
```

---

- 代码风格规范 editorconfig
  - 创建.editorconfig 文件

```yml
root = true

[*]
indent_style = space
indent_size = 2
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true

[*.md]
trim_trailing_whitespace = false

[Makefile]
indent_style = tab
```

---

# husky line pre-commit

```shell
ni husky lint-staged -D
```

```json
// change 1: 配置 lint-staged 指令
"scripts": {
// 新增这二行
"lint-staged": "lint-staged",
 "prepare": "husky install",
...
},
// change 2: 配置 lint-staged 的具体任务
  "lint-staged": {
    "*": [
      "eslint . --fix"
    ]
  }
```

- ni 生成.husky

- 添加 git hooks -> pre-commit，运行一下命令创建 git hooks

  ```shell
  npx husky add .husky/pre-commit "pnpm lint-staged"
  ```

---

# commit-msg

- 添加 git hooks -> commit-msg，运行一下命令创建 git hooks

  ```shell
  ni -D @commitlint/config-conventional @commitlint/cli cz-git
  npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'
  ```

- 修改 package.json 添加 config 指定使用的适配器

  ```json
  {
    "scripts": {},
    "config": {
      "commitizen": {
        "path": "node_modules/cz-git"
      }
    }
  }
  ```

- 新建 commitlint.config.js

  ```js
  /** @type {import('cz-git').UserConfig} */
  module.exports = {
    ignores: [(commit) => commit.includes('init')],
    extends: ['@commitlint/config-conventional'],
    rules: {
      // @see: https://commitlint.js.org/#/reference-rules
    },
    prompt: {
      alias: { fd: 'docs: fix typos' },
      messages: {
        type: '选择你要提交的类型 :',
        scope: '选择一个提交范围（可选）:',
        customScope: '请输入自定义的提交范围 :',
        subject: '填写简短精炼的变更描述 :\n',
        body: '填写更加详细的变更描述（可选）。使用 "|" 换行 :\n',
        breaking: '列举非兼容性重大的变更（可选）。使用 "|" 换行 :\n',
        footerPrefixsSelect: '选择关联issue前缀（可选）:',
        customFooterPrefixs: '输入自定义issue前缀 :',
        footer: '列举关联issue (可选) 例如: #31, #I3244 :\n',
        confirmCommit: '是否提交或修改commit ?',
      },
      types: [
        {
          value: 'feat',
          name: 'feat:     🚀  新增功能 | A new feature',
          emoji: '🚀',
        },
        {
          value: 'fix',
          name: 'fix:      🧩  修复缺陷 | A bug fix',
          emoji: '🧩',
        },
        {
          value: 'docs',
          name: 'docs:     📚  文档更新 | Documentation only changes',
          emoji: '📚',
        },
        {
          value: 'style',
          name: 'style:    🎨  代码格式 | Changes that do not affect the meaning of the code',
          emoji: '🎨',
        },
        {
          value: 'refactor',
          name: 'refactor: ♻️   代码重构 | A code change that neither fixes a bug nor adds a feature',
          emoji: '♻️',
        },
        {
          value: 'perf',
          name: 'perf:     ⚡️  性能提升 | A code change that improves performance',
          emoji: '⚡️',
        },
        {
          value: 'test',
          name: 'test:     ✅  测试相关 | Adding missing tests or correcting existing tests',
          emoji: '✅',
        },
        {
          value: 'build',
          name: 'build:    📦️  构建相关 | Changes that affect the build system or external dependencies',
          emoji: '📦️',
        },
        {
          value: 'ci',
          name: 'ci:       🎡  持续集成 | Changes to our CI configuration files and scripts',
          emoji: '🎡',
        },
        {
          value: 'chore',
          name: 'chore:    🔨  其他修改 | Other changes that do not modify src or test files',
          emoji: '🔨',
        },
        {
          value: 'revert',
          name: 'revert:   ⏪️  回退代码 | Revert to a commit',
          emoji: '⏪️',
        },
      ],
      useEmoji: true,
      emojiAlign: 'center',
      themeColorCode: '',
      scopes: [],
      allowCustomScopes: true,
      allowEmptyScopes: true,
      customScopesAlign: 'bottom',
      customScopesAlias: 'custom',
      emptyScopesAlias: 'empty',
      upperCaseSubject: false,
      markBreakingChangeMode: false,
      allowBreakingChanges: ['feat', 'fix'],
      breaklineNumber: 100,
      breaklineChar: '|',
      skipQuestions: [],
      issuePrefixs: [
        // 如果使用 gitee 作为开发管理
        { value: 'link', name: 'link:     链接 ISSUES 进行中' },
        { value: 'closed', name: 'closed:   标记 ISSUES 已完成' },
      ],
      customIssuePrefixsAlign: 'top',
      emptyIssuePrefixsAlias: 'skip',
      customIssuePrefixsAlias: 'custom',
      allowCustomIssuePrefixs: true,
      allowEmptyIssuePrefixs: true,
      confirmColorize: true,
      maxHeaderLength: Infinity,
      maxSubjectLength: Infinity,
      minSubjectLength: 0,
      scopeOverrides: undefined,
      defaultBody: '',
      defaultIssues: '',
      defaultScope: '',
      defaultSubject: '',
    },
  };
  ```

- 添加 commit 脚本
  ```json
  {
    "scripts": {
      ...
      "commit": "git add . && cz"
    },
  }
  ```
