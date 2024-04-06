# CLI Template

这是一个由 TypeScript 作为主要开发语言的 CLI 应用程序项目模板，方便您快速的搭建一个 CLI 应用程序项目, 它的开发模式是免 `watch` 和 `build` 的, 您不需要使用其他任何构建工具对 `ts` 代码进行构建监听。

[English](https://github.com/hacxy/cli-template/blob/main/README.md) | 简体中文

## 先决条件

需要 Node.js 版本 18+、20+

## 将模板创建至本地

### 使用 [create-ts-frame](https://github.com/hacxy/create-ts-frame) 创建项目至本地

执行创建命令时可以通过选项指定项目名称和模板名称

```sh
# npm 7+, 需要额外的双破折号:
npm create ts-frame@latest my-cli-app -- --template cli

# yarn
yarn create ts-frame my-cli-app --template cli

# pnpm
pnpm create ts-frame my-cli-app --template cli

# Bun
bun create ts-frame my-cli-app --template cli
```

## 安装依赖

```sh
cd my-cli-project
npm install
```

## 快速开始

默认情况下, 当您执行 `npm run dev` 时, 将使用 [unbuild](https://github.com/unjs/unbuild) 对 `dist` 文件夹进行存根, 您可以前往[jiti](https://github.com/unjs/jiti)了解这个模式，之后即使您修改了代码, 也无需再执行 `dev` 命令, 或者使用其他构建工具的 `watch` 模式来对 `ts` 代码重新编译。当您需要修改 `unbuild` 配置时, 您可以在 `build.config.ts` 文件中对 `unbuild` 做[其他配置](https://github.com/unjs/unbuild/blob/main/src/types.ts)。

- 开发模式

```sh
npm run dev
```

- 构建生产环境代码

```sh
npm run build
```

- 输出包含 sourcemap 的构建产物至 out 文件夹中

```sh
npm run build:out
```

- 类型检查。

```sh
npm run typecheck
```

## 调试程序运行

因为我使用 `vscode` 来开发 CLI 应用程序, 所以提供了其对应的 debug 配置文件: `.vscode/launch.json`, 当您需要调试这个项目时, 首先添加断点, 之后可以按 `F5` 键来启动 Debugger 模式, 当您的 CLI 应用程序执行结束时, Debugger 模式会自动退出.

> [!TIP]
> 运行 Debugger 模式时会自动执行 `tsc` 命令并将用于 debug 的构建产物输出至 `out` 目录下  
> 之后将自动运行应用程序

### 全局链接包:

您还可以为这个包建立一个全局链接, 方便您使用真实环境来测试或者调试代码:

```sh
npm link
```

之后您就可以在终端的任意路径下去执行命令: `hello-cli`, 这个命令对应的是该项目下的 `package.json` 文件中 `bin` 选项的值.

当您不需要这个全局链接时, 您还可以手动移除它, 在项目下执行:

```sh
npm unlink -g
```

## 解决方案

为了方便您顺利的开发脚手架应用程序, 我还贴心的为您补充了一些在脚手架应用程序开发中, 您可能需要的解决方案, 这些第三方库可以帮助您实现更强大更实用更美观的脚手架应用程序, 它们都经过了此项目模板的实际应用和测试, 您可以放心的使用:

- [commander.js](https://github.com/tj/commander.js) - 完整的 node.js 命令行解决方案。

- [kolorist](https://github.com/marvinhagemeister/kolorist) - 将颜色添加到标准输入/输出的微型库

- [prompts](https://github.com/terkelg/prompts) - 轻巧、美观且友好的交互提示工具

> [!TIP] 在这个模板项目中, 默认内置了以下这些第三方库
>
> - [kolorist](https://github.com/marvinhagemeister/kolorist)
> - [commander.js](https://github.com/tj/commander.js)
> - [prompts](https://github.com/terkelg/prompts)
>
> 您无需再安装并且可以直接使用它们, 即使您不使用它们, 您也无需在意这些包, 因为它们并不会打包到您的生产环境代码中, 而且它们都属于开发时依赖, 所以用户在安装您的 CLI 应用程序时也不会将这些包下载至它们的本地.