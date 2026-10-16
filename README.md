<!-- markdownlint-disable MD033 MD041 -->
<p align="center">
  <img alt="LOGO" src="https://cdn.jsdelivr.net/gh/MaaAssistantArknights/design@main/v1/icons/maa-logo_512x512.png" width="256" height="256" />
</p>

<div align="center">

# MaaPracticeBoilerplate

</div>

本仓库为 [MaaFramework](https://github.com/MaaXYZ/MaaFramework) 所提供的项目模板，开发者可基于此模板直接创建自己的 MaaXXX 项目。

> **MaaFramework** 是基于图像识别技术、运用 [MAA](https://github.com/MaaAssistantArknights/MaaAssistantArknights) 开发经验去芜存菁、完全重写的新一代自动化黑盒测试框架。
> 低代码的同时仍拥有高扩展性，旨在打造一款丰富、领先、且实用的开源库，助力开发者轻松编写出更好的黑盒测试程序，并推广普及。

## 即刻开始

**请不要直接克隆本仓库！你应该通过模板创建自己的项目！**  

请阅读 [如何开发](./docs/zh_cn/develop/how_to_develop.md)。

向本模板仓库提交改动前，请阅读 [PR 规范](./docs/zh_cn/develop/pull_request_guidelines.md)。

## 项目开发

### 结构介绍

1. ~~.vscode里面有配置文件,settings里面修改了interface.json的可能位置(移动到根目录)，新增了tasks目录的结构验证~~
2. 使用了import的方式导入了其他pi文件，目录在tasks里面，结构参考 deps\tools\interface_import.schema.json
3. 修改了.github/workflows/install.json，注释了on部分的触发，提交不会进行构建，保留了手动构建
4. ~~修改了maatools.config.mts,把interface.json改到根目录了~~
5. 修改了.github/workflows/check.json，注释了on部分的触发，提交不会进行校验，保留了手动构建

### 开发备注

#### 可能会用到的命令

1. 使用uv管理python部分

- 拉取当前项目后

```shell
uv sync
```

1. 本地构建

- 参考 tools\install.py
- 补齐环境

```shell
uv add json-with-comments   # 参考 tools\requirements.txt
git submodule update --init --recursive # 补子仓库 参考 .gitmodules
# 可选   
git submodule update --remote --recursive # 如果子模块有更新


```

- 下载 MaaFramework 到 "deps",地址 <https://github.com/MaaXYZ/MaaFramework/releases> 除了tools全拷贝到deps里面，保证目录结构是deps/bin,然后maa的tools里面多的也可以拷贝到该项目

- 校验

```shell
python tools/validate_schema.py --schema-dir deps/tools --resource-dirs assets/resource --exclude-dirs assets/resource/announcement --interface-files assets/interface.json   --task-dirs tasks
```

- 构建

```shell
python tools/install.py v0.0.1 win x86_64  # 执行构建  产物在install目录
```

install产物需要拷贝到 MFAAvalonia 进行资源加载运行
或者下载好后把MFAAvalonia全拷贝当当前的install目录然后再构建
下载 <https://github.com/MaaXYZ/MFAAvalonia/releases>

#### 初始化的时候使用(已初始化，无需执行，只记录操作)

```shell
uv python pin 3.13
uv init  
uv venv
.\.venv\Scripts\activate
uv add jsonschema==4.26.0 referencing==0.37.0
```

## 生态共建

MAA 正计划建设为一类项目，而非舟的单一软件。

若您的项目依赖于 MaaFramework，我们欢迎您将它命名为 MaaXXX, MXA, MAX 等等。当然，这是许可而不是限制，您也可以自由选择其他与 MAA 无关的名字，完全取决于您自己的想法！

同时，我们也非常欢迎您提出 PR，在 [社区项目列表](https://github.com/MaaXYZ/MaaFramework#%E7%A4%BE%E5%8C%BA%E9%A1%B9%E7%9B%AE) 中添加上您的项目！

## 常见问题

请阅读 [常见问题](./docs/zh_cn/develop/faq.md)。

## 鸣谢

本项目由 **[MaaFramework](https://github.com/MaaXYZ/MaaFramework)** 强力驱动！

感谢以下开发者对本项目作出的贡献（下面链接改成你自己的项目地址）:

[![Contributors](https://contrib.rocks/image?repo=MaaXYZ/MaaFramework&max=1000)](https://github.com/MaaXYZ/MaaFramework/graphs/contributors)
