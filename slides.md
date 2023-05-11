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
<strong><a href="https://vue-macros.sxzz.moe/zh-CN/" target="_blank">unplugin-vue-macros</a></strong> 中文文档编写者<br>
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

# 语言选择

<h3 v-click>
 ?? JavaScript ??
</h3>

<h3 v-click style="margin-top: 30px;">
<strong><span style="color: red;">Type</span>Script</strong> !!!
</h3>

<ul style="padding-left: 20px; padding-top: 20px;">
  <li v-click>强类型，支持静态和动态类型（<u>更容易写出<strong>健壮性</strong>高的代码</u>）</li>
  <li v-click>在编译期间可以检测和修复错误</li>
  <li v-click>支持模块、泛型和接口</li>
  <li v-click>...</li>
</ul>

<h1 v-click style="margin-top: 30px;">
  <div>↑</div>
  <span style="color: green;">any</span>Script🤡
</h1>

---

# 集成 Next.js

<div v-click>

- 创建文件夹

</div>

<div v-click>

- 初始化 `package.json`

```shell
# 进入刚创建的文件夹下打开终端
npm init -y
```

</div>

<div v-click>

- 安装依赖

```shell
pnpm add next@latest react@latest react-dom@latest
# 或使用ni安装依赖包，后面默认都使用ni
ni next@latest react@latest react-dom@latest
```

</div>

<div v-click>

- 在 `package.json` 中添加 scripts 脚本

```json
{
  ...
  "scripts": {
    "dev": "next dev --turbo",
    "build": "next build",
  }
  ...
}
```

</div>

---

- 根目录下创建 **app** 文件夹
- 在 **app** 文件夹分别创建 **layout.tsx** 和 **page.tsx**

```tsx {1|2-8|all}
// layout.tsx
export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  );
}
```

```tsx {1|2-4|all}
// page.tsx
export default function Page() {
  return <h1>Hello World</h1>;
}
```

<div v-click style="margin-top: 20px;">
至此，项目已经可以通过 <code>nr dev</code> 跑起来了
<img src="/hello-world.jpg" style="margin-top: 20px;" />
</div>

---

# 集成 tailwindcss

<div v-click>

- 安装 tailwindcss

```shell
ni -D tailwindcss postcss autoprefixer
npx tailwindcss init -p # 自动生成tailwind.config.js 和 postcss.config.js
```

</div>

<div v-click>

- 修改 tailwind.config.js

```js
// tailwind.config.js
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

</div>

---

- app 文件夹下添加 global.css

```css {all|1|2|3|4|all}
/* global.css */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

- 在 app/layout.tsx 中引入 global.css

```tsx {all|1|2|all}
// layout.tsx
import './global.css';
```

---

# 编辑器代码风格统一

<div v-click>

- 根目录下创建 **_.editorconfig_** 文件

```yml
# .editorconfig
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

</div>

---

# Eslint 保证代码风格统一

<div v-click>

- 安装依赖

```shell
ni -D eslint @antfu/eslint-config
```

</div>

<div v-click>

- 根目录下创建 .eslintrc.js

```js
{
  "extends": "@antfu"
}
```

</div>

<div v-click>

- package.json 中添加 scripts 脚本

```json
{
  ...
  "scripts": {
    ...
    "lint": "eslint .",
    "lint:fix": "eslint . --fix"
  }
  ...
}
```

</div>

---

# 同事关系润滑剂

<div v-click>

- 安装 `husky` 和 `lint-staged`

```shell
ni husky lint-staged -D
```

</div>

<div v-click>

- 修改 **package.json**

```json
// step 1: 新增 lint-staged prepare 脚本
"scripts": {
  ...
  // 新增这二行
  "lint-staged": "lint-staged",
  "prepare": "husky install",
  ...
},

// step 2: 配置 lint-staged
{
  ...
  "lint-staged": {
    "*": [
      "eslint . --fix"
    ]
  }
}
```

</div>

---

<div>

- 终端执行 `ni` 命令自动生成 **.husky** 文件

</div>

<div v-click>

- 添加 git hooks -> pre-commit，运行命令创建 git hooks

```shell
npx husky add .husky/pre-commit "pnpm lint-staged"
```

</div>

<div v-click>

- 至此，我们执行 `git add .`之前，就会自动执行 `eslint . --fix` 了。那么在 git 暂存区的代码就是符合 我们定义的 eslint 规范的代码了

</div>

---

# 规范 commit-message

<div v-click>

- 安装规范 commit-message 所需的依赖包

```shell
ni -D @commitlint/config-conventional @commitlint/cli cz-git
```

</div>

<div v-click>

- 添加 git hooks -> commit-msg，运行一下命令创建 git hooks

```shell
npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'
```

</div>

<div v-click>

- 修改 **package.json** 添加 config 指定使用的适配器，以及 **commit** 脚本

```json
{
  "scripts": {
    ...
    "commit": "git add . && cz"
  },
  "config": {
    "commitizen": {
      "path": "node_modules/cz-git"
    }
  }
}
```

</div>

---

- 根目录下新建 **commitlint.config.js** (太长了，放不下)

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

---

# Vitest

<div v-click>

- 安装依赖

```shell
ni -D vitest @vitejs/plugin-react jsdom
```

</div>

<div v-click>

- 在根目录下创建 `vitest.config.ts`

```ts
/// <reference types="vitest" />

import { defineConfig } from 'vitest/config';
import react from '@vitejs/plugin-react';

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
  test: {
    environment: 'jsdom',
  },
});
```

</div>

---

- **package.json** 添加 **scripts** 脚本

```json {all|5|all}
{
  ...
  "scripts": {
    ...
    "test": "vitest"
  }
}
```

<div v-click>

- 之后就可以编写测试代码，通过执行 `nr test` 进行测试

</div>
