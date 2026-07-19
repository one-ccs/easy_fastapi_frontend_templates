# Art Design Pro 模板文件映射

> 本文件标注模板中每个目录/文件的用途，帮助判断哪些是示例代码（可删）、
> 哪些是框架核心（须保留）。AI 开发时可参考对应示例的写法。

---

## 🔴 示例代码（可按需删除或替换）

这些是 Art Design Pro 的演示页面和模拟数据，展示了组件用法但不含真实业务逻辑。
删除后不影响框架运行，但会失去写法参考。

### 页面视图

| 路径 | 说明 | 参考价值 |
|------|------|----------|
| `src/views/dashboard/` | 仪表盘（analysis/console/ecommerce 三种风格） | 图表卡片、统计组件组合方式 |
| `src/views/article/` | 文章管理（列表/详情/发布/评论） | CRUD 页面完整示例，含表格+搜索+弹窗 |
| `src/views/template/` | 模板展示（banners/cards/charts/map/chat/pricing/calendar） | 各类组件实际用法 |
| `src/views/widgets/` | 小组件展示（拖拽/图标/二维码/视频/编辑器/水印等） | 单组件独立用法 |
| `src/views/safeguard/` | 服务器监控示例 | ECharts 地图+实时数据 |
| `src/views/result/` | 结果页（成功/失败） | 结果页布局 |
| `src/views/change/` | 更新日志 | 时间线组件用法 |
| `src/views/system/nested/` | 嵌套菜单示例 | 多级路由+嵌套布局 |

### 模拟数据

| 路径 | 说明 | 参考价值 |
|------|------|----------|
| `src/mock/temp/` | 模拟业务数据（文章列表/评论/表单） | API 层 mock 结构，对接真实 API 后删除 |
| `src/mock/json/chinaMap.json` | 中国地图 GeoJSON | 地图图表需要，如不用地图可删 |
| `src/mock/upgrade/changeLog.ts` | 更新日志数据 | 随更新日志页面删除 |

### 路由模块（示例）

| 路径 | 说明 | 参考价值 |
|------|------|----------|
| `src/router/modules/dashboard.ts` | 仪表盘路由定义 | **保留**：路由定义模式参考 |
| `src/router/modules/article.ts` | 文章管理路由 | CRUD 路由定义参考 |
| `src/router/modules/examples.ts` | 示例路由 | 删除示例页时同步删除 |
| `src/router/modules/template.ts` | 模板展示路由 | 删除模板页时同步删除 |
| `src/router/modules/widgets.ts` | 小组件路由 | 删除小组件页时同步删除 |
| `src/router/modules/safeguard.ts` | 服务器监控路由 | 删除监控页时同步删除 |
| `src/router/modules/help.ts` | 帮助页路由 | 可删 |
| `src/router/modules/result.ts` | 结果页路由 | 保留或按需删 |

### 图片资源（示例用）

| 路径 | 说明 |
|------|------|
| `src/assets/images/3d/` | 仪表盘 3D 图标（8 张） |
| `src/assets/images/avatar/` | 示例头像（11 张） |
| `src/assets/images/cover/` | 示例封面（10 张） |
| `src/assets/images/ceremony/` | 节日装饰图片 |
| `src/assets/images/draw/` | 抽奖活动图片 |
| `src/assets/images/safeguard/` | 服务器监控图片 |

---

## 🟢 框架核心（不要删）

这些是 Art Design Pro 的核心架构，删除后系统无法正常运行。

### 入口与配置

| 路径 | 说明 |
|------|------|
| `src/main.ts` | 应用入口 |
| `src/App.vue` | 根组件 |
| `src/env.d.ts` | TypeScript 环境声明 |
| `src/config/` | 全局配置（setting/component/fastEnter/headerBar/festival） |
| `src/enums/` | 枚举常量（appEnum/formEnum） |
| `src/plugins/` | 插件注册（echarts 等） |
| `src/locales/` | 国际化（zh.json/en.json） |
| `.env` / `.env.development` / `.env.production` | 环境变量 |
| `vite.config.ts` | Vite 配置（含 API 代理） |
| `tsconfig.json` / `tsconfig.app.json` / `tsconfig.node.json` | TypeScript 配置 |

### 路由系统

| 路径 | 说明 |
|------|------|
| `src/router/index.ts` | 路由入口 |
| `src/router/core/` | 路由核心（ComponentLoader/RouteRegistry/MenuProcessor/RoutePermissionValidator 等） |
| `src/router/guards/` | 路由守卫（beforeEach/afterEach） |
| `src/router/routes/` | 路由表（asyncRoutes/staticRoutes） |
| `src/router/routesAlias.ts` | 路由别名常量 |
| `src/router/modules/index.ts` | 路由模块聚合导出 |
| `src/router/modules/system.ts` | **系统路由**（用户/角色/菜单管理，需保留并对接后端） |
| `src/router/modules/exception.ts` | 异常页路由（403/404/500） |

### 状态管理

| 路径 | 说明 |
|------|------|
| `src/store/index.ts` | Pinia 入口 |
| `src/store/modules/user.ts` | **用户状态**（登录/令牌/登出，需对接后端 auth） |
| `src/store/modules/menu.ts` | 菜单状态（动态菜单加载） |
| `src/store/modules/setting.ts` | 主题/布局设置 |
| `src/store/modules/worktab.ts` | 工作标签页 |
| `src/store/modules/table.ts` | 表格状态 |

### API 层

| 路径 | 说明 |
|------|------|
| `src/api/auth.ts` | **认证 API**（登录/获取用户信息，需对接后端 `/auth/*`） |
| `src/api/system-manage.ts` | **系统管理 API**（用户/角色/菜单列表，需对接后端） |
| `src/utils/http/` | HTTP 封装（axios 实例/拦截器/错误处理/状态码） |

### 工具库

| 路径 | 说明 |
|------|------|
| `src/utils/index.ts` | 通用工具函数 |
| `src/utils/http/` | HTTP 请求封装 |
| `src/utils/form/` | 表单工具（校验/响应式） |
| `src/utils/navigation/` | 导航工具（路由跳转/标签页） |
| `src/utils/constants/` | 常量定义 |
| `src/utils/ui/` | UI 工具（动画/颜色/加载状态/图标） |
| `src/utils/table/` | 表格工具 |

### Hooks

| 路径 | 说明 |
|------|------|
| `src/hooks/index.ts` | Hooks 入口 |
| `src/hooks/core/useTable.ts` | **表格 Hook**（核心能力，CRUD 页面必用） |
| `src/hooks/core/useTableColumns.ts` | 表格列定义 Hook |
| `src/hooks/core/useTableHeight.ts` | 表格高度自适应 |
| `src/hooks/core/useAuth.ts` | 权限判断 Hook |
| `src/hooks/core/useTheme.ts` | 主题 Hook |
| `src/hooks/core/useChart.ts` | ECharts Hook |
| `src/hooks/core/useCommon.ts` | 通用 Hook |
| `src/hooks/core/useLayoutHeight.ts` | 布局高度 Hook |
| `src/hooks/core/useCeremony.ts` | 节日效果 Hook |
| `src/hooks/core/useFastEnter.ts` | 快捷入口 Hook |
| `src/hooks/core/useHeaderBar.ts` | 顶栏 Hook |
| `src/hooks/core/useAppMode.ts` | 应用模式 Hook |

### 组件

| 路径 | 说明 |
|------|------|
| `src/components/core/layouts/` | **布局组件**（侧边栏/顶栏/面包屑/标签页/设置面板/锁屏/通知） |
| `src/components/core/views/` | **通用页面**（登录/异常/结果页） |
| `src/components/core/tables/` | **表格组件**（art-table/art-table-header） |
| `src/components/core/forms/` | **表单组件**（art-form/art-search-bar/art-excel-import/export） |
| `src/components/core/charts/` | 图表组件（9 种 ECharts 封装） |
| `src/components/core/cards/` | 卡片组件（8 种数据展示卡片） |
| `src/components/core/banners/` | 横幅组件 |
| `src/components/core/base/` | 基础组件（logo/svg-icon/回到顶部） |
| `src/components/core/media/` | 媒体组件（图片裁剪/视频播放器） |
| `src/components/core/others/` | 其他组件（右键菜单/水印） |
| `src/components/core/text-effect/` | 文字效果组件 |
| `src/components/core/theme/` | 主题组件 |
| `src/components/core/widget/` | 小部件（图标按钮） |
| `src/components/business/` | 业务组件（评论组件） |

### 指令

| 路径 | 说明 |
|------|------|
| `src/directives/core/auth.ts` | 权限指令 `v-auth` |
| `src/directives/core/roles.ts` | 角色指令 `v-roles` |
| `src/directives/business/highlight.ts` | 高亮指令 |
| `src/directives/business/ripple.ts` | 波纹效果指令 |

### 类型

| 路径 | 说明 |
|------|------|
| `src/types/` | TypeScript 类型定义（API/组件/路由/Store/配置） |

### 样式

| 路径 | 说明 |
|------|------|
| `src/assets/styles/core/` | 核心样式（重置/主题/动画/Element Plus 主题覆盖） |
| `src/assets/styles/index.scss` | 样式入口 |
| `src/assets/styles/custom/` | 自定义样式 |

### 关键页面（须保留并改造）

| 路径 | 说明 |
|------|------|
| `src/views/auth/login/` | **登录页**（须对接后端 `/auth/login`） |
| `src/views/auth/register/` | 注册页（按需保留） |
| `src/views/auth/forget-password/` | 忘记密码页（按需保留） |
| `src/views/system/user/` | **用户管理页**（须对接后端用户 CRUD） |
| `src/views/system/role/` | **角色管理页**（须对接后端角色 CRUD） |
| `src/views/system/menu/` | **菜单管理页**（须对接后端菜单） |
| `src/views/system/user-center/` | 个人中心 |
| `src/views/exception/` | 异常页（403/404/500） |
| `src/views/index/` | 首页布局 |

---

## 🟡 需改造对接后端

这些文件目前使用 Mock 数据，需改为调用 `api-sdk` 或直接调后端 API。

| 路径 | 当前状态 | 改造方向 |
|------|----------|----------|
| `src/api/auth.ts` | 调用 `/api/auth/login`、`/api/user/info` | 对接 `efa` 后端 `/auth/*` 路由 |
| `src/api/system-manage.ts` | 调用 `/api/user/list`、`/api/role/list`、`/api/v3/system/menus` | 对接 `efa` 后端用户/角色/菜单路由 |
| `src/store/modules/user.ts` | 存储 accessToken/refreshToken | 适配 `efa` 后端 Token 响应格式 |
| `src/utils/http/index.ts` | axios 拦截器 + 401 处理 | 确认与 `efa` 后端 401 响应格式一致 |
| `src/router/guards/beforeEach.ts` | 登录验证 + 动态路由 | 菜单数据格式须与后端对齐 |
| `src/views/system/user/` | 演示数据 | 改为真实后端数据 |
| `src/views/system/role/` | 演示数据 | 改为真实后端数据 |

---

## 📝 快速参考：开发新页面时看哪些文件

| 需求 | 参考文件 |
|------|----------|
| 新建 CRUD 页面 | `src/views/system/user/` + `src/router/modules/system.ts` + `src/hooks/core/useTable.ts` |
| 新建带搜索的列表 | `src/views/article/list/` + `src/components/core/forms/art-search-bar/` |
| 新建弹窗表单 | `src/views/system/role/modules/role-edit-dialog.vue` |
| 新建带图表的仪表盘 | `src/views/dashboard/analysis/` |
| 添加新 API 方法 | `src/api/system-manage.ts`（参考模式） |
| 添加新路由模块 | `src/router/modules/system.ts`（参考模式） |
| 自定义表格列 | `src/hooks/core/useTableColumns.ts` |
| 权限控制 | `src/directives/core/auth.ts` + `src/hooks/core/useAuth.ts` |
| HTTP 请求 | `src/utils/http/index.ts`（已封装 axios） |
