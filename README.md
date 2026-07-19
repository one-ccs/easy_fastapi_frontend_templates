# Easy FastAPI 前端模板仓库

本仓库为 [easy-fastapi](https://github.com/one-ccs/easy_fastapi) 脚手架提供远程前端模板。

`efa create` 创建项目时，可从此仓库拉取前端模板并自动集成到生成的项目中。

## 可用模板

| 模板 ID | 名称 | 技术栈 | 要求 |
|---------|------|--------|------|
| `admin-art-design` | 管理后台（Art Design Pro） | Vue 3 + Element Plus + Tailwind CSS | frontend + auth + database |
| `client-h5` | H5 移动客户端 | Vue 3 + Vant | frontend |

## 使用方式

```bash
# 交互模式（向导中选择模板）
efa create myapp

# 非交互模式
efa create myapp --frontend --auth --database --orm tortoise --templates admin-art-design --no-interactive

# 多模板
efa create myapp --frontend --auth --database --orm tortoise --templates admin-art-design,client-h5 --no-interactive
```

## 模板开发

每个模板是独立的 Vite 项目，可单独运行调试：

```bash
# 1. 克隆本仓库
git clone https://github.com/one-ccs/easy_fastapi_frontend_templates
cd easy_fastapi_frontend_templates/templates/admin-art-design

# 2. 启动后端（另一个终端）
efa create test-backend --frontend --database --auth --orm tortoise --no-interactive
cd test-backend/backend
efa db sync
efa run --reload

# 3. 启动前端
pnpm install
pnpm dev
```

模板的 `vite.config.ts` 已配置开发代理，自动将 API 请求转发到 `http://localhost:8000`。

## 模板结构

```
templates/
  {template-id}/
    template.yaml      # 模板清单（CLI 读取，不复制到生成项目）
    package.json.j2    # Jinja2 模板，渲染后替换 package_name
    vite.config.ts     # Vite 配置（含开发代理）
    src/               # 源码目录
    ...
```

- `.j2` 文件经 Jinja2 渲染，可使用 `{{ options.package_name }}` 等变量
- 非 `.j2` 文件原样复制
- `template.yaml` 仅声明元数据，不会复制到生成项目

## template.yaml Schema

```yaml
id: "模板唯一标识"           # 匹配 ^[a-z][a-z0-9-]*$
display_name:
  zh: "中文显示名"
  en: "English display name"
description:
  zh: "中文描述"
  en: "English description"
version: "1.0.0"
stack:
  framework: "vue3"         # 技术栈标识
  ui_library: "element-plus"
  language: "typescript"
  build_tool: "vite"
tags: ["admin"]
requires:                    # 前置条件（AND 语义）
  frontend: true
  auth: true
  database: true
  orm: ["tortoise", "sqlalchemy", "sqlmodel"]  # ORM 白名单
install_name: "admin"        # 放入 frontend/apps/ 下的目录名
post_messages:               # 安装后提示
  zh:
    - "提示信息"
  en:
    - "Hint message"
```

## License

MIT
