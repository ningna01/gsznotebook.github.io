# Chirpy 主题自定义指南

## 目录结构说明

对于 Chirpy 主题（gem 主题），你可以通过以下方式自定义：

### 1. 配置文件：`_config.yml`
**用途**：修改网站基本信息、主题配置
**常用配置项**：
- `title`: 网站标题
- `description`: 网站描述
- `url` / `baseurl`: 网站URL
- `theme`: 主题名称
- 其他主题特定配置（参考 Chirpy 文档）

### 2. 主页内容：`index.markdown`
**用途**：控制主页显示的内容
**当前文件位置**：项目根目录的 `index.markdown`
**可以修改**：
- Front Matter（YAML前置元数据）
- 在 `layout: home` 下添加自定义内容

### 3. 覆盖布局文件：`_layouts/`
**用途**：覆盖主题的布局模板
**创建方式**：
```
_layouts/
  ├── home.html      # 主页布局
  ├── post.html      # 文章布局
  ├── page.html      # 页面布局
  └── default.html   # 默认布局
```

**注意**：需要从主题的 gem 包中复制原始文件，然后修改。可以使用：
```bash
bundle show jekyll-theme-chirpy
```
来查找主题文件位置。

### 4. 覆盖包含文件：`_includes/`
**用途**：覆盖主题的组件模板
**常用文件**：
```
_includes/
  ├── header.html      # 头部
  ├── footer.html      # 页脚
  ├── sidebar.html     # 侧边栏
  └── ...
```

### 5. 自定义样式：`_sass/` 和 `assets/css/`
**用途**：添加自定义CSS样式
**推荐方式**：

**方法1：创建自定义CSS文件（推荐）**
```
assets/css/
  └── custom.scss      # 你的自定义样式
```

然后在 `_config.yml` 中添加：
```yaml
sass:
  sass_dir: _sass
```

**方法2：使用 `_sass/` 目录**
```
_sass/
  └── custom.scss      # 自定义样式
```

### 6. 数据文件：`_data/`
**用途**：存储可被布局和包含文件使用的数据
**示例**：
```
_data/
  ├── navigation.yml   # 导航菜单
  └── social.yml       # 社交媒体链接
```

## 快速开始

### 修改主页布局

1. **简单方式**：修改 `index.markdown`
   ```markdown
   ---
   layout: home
   ---
   
   这里可以添加你的主页内容（Markdown格式）
   ```

2. **高级方式**：覆盖 `_layouts/home.html`
   - 需要从主题复制原始文件
   - 创建 `_layouts/home.html`
   - 进行修改

### 添加自定义CSS

1. 创建 `assets/css/custom.scss`：
   ```scss
   ---
   # 空的前置元数据，让Jekyll处理此文件
   ---
   
   // 你的自定义样式
   .custom-class {
     color: #your-color;
   }
   ```

2. 或者创建 `_sass/custom.scss` 并在主样式文件中导入

### 修改网站基本信息

直接编辑 `_config.yml`：
```yaml
title: 你的网站标题
description: 你的网站描述
# ... 其他配置
```

## 注意事项

1. **主题更新**：覆盖主题文件后，主题更新时可能需要手动合并更改
2. **优先级**：项目中的文件优先级高于主题gem包中的文件
3. **Chirpy特定配置**：Chirpy主题有自己的配置选项，建议查看官方文档

## 参考资源

- Chirpy主题文档：https://github.com/cotes2020/jekyll-theme-chirpy
- Jekyll文档：https://jekyllrb.com/docs/




