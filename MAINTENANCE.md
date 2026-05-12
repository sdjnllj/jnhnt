<!-- 
  注意：此文件为内部维护文档，不应被搜索引擎索引
  robots.txt 已配置 Disallow: /MAINTENANCE.md
-->

# 济南钧华商砼网站维护说明

## 📋 项目基本信息

- **项目名称**：济南钧华商砼混凝土有限公司官网
- **项目路径**：`C:\inetpub\wwwroot\hunningtu`
- **域名**：www.sdjnhnt.cn
- **GitHub仓库**：https://github.com/sdjnllj/jnhnt
- **服务器**：IIS (Windows Server)
- **最后更新**：2026-03-15

---

## 🗂️ 网站结构

```
hunningtu/
├── index.html                      # 首页
├── articles/                       # 文章目录
│   ├── list.html                  # 文章列表页
│   ├── spring-construction-guide.html      # 春季施工指南（最新）
│   ├── mixing-plant-technology.html        # 搅拌站技术
│   ├── concrete-price-analysis.html        # 价格分析
│   ├── quality-management.html             # 质量管理
│   ├── green-technology.html               # 绿色技术
│   ├── winter-concrete-guide.html          # 冬季施工指南
│   ├── project-case.html                   # 项目案例
│   ├── industry-trend.html                 # 行业趋势
│   ├── technical-guide.html                # 技术指南
│   └── article_template.html               # 文章模板
├── images/                         # 图片资源目录
├── *.jpg                           # 根目录图片
├── web.config                      # IIS配置文件
├── sitemap.xml                     # 站点地图
├── robots.txt                      # 搜索引擎配置
├── .gitignore                      # Git忽略文件配置
└── MAINTENANCE.md                  # 本维护说明文档
```

---

## 🔧 日常维护流程

### 一、发布新文章（标准流程）

#### 步骤1：创建新文章文件

1. 在 `articles/` 目录下创建新的HTML文件
2. 文件名规范：使用小写字母和连字符，如 `new-article-title.html`
3. 参考现有文章结构（推荐使用 `green-technology.html` 作为模板）

**必需包含的元素：**
- ✅ 百度统计代码（`<head>` 中）
- ✅ SEO三要素：`<title>`、`<meta description>`、`<meta keywords>`
- ✅ Font Awesome图标库引用
- ✅ 导航栏（返回首页 + 文章列表）
- ✅ 文章头部（标题、日期、分类）
- ✅ 文章内容（建议3-4个章节，可配图）
- ✅ 相关文章推荐（3-4个链接）
- ✅ 页脚版权信息

**SEO优化要点：**
- 标题格式：`文章主题 - 济南钧华商砼`
- 关键词：包含"济南混凝土"等本地化词汇
- 描述：150-200字，包含核心关键词
- 图片alt属性：描述性文字

#### 步骤2：更新文章列表页

编辑文件：`articles/list.html`

在 `<div class="article-list">` 的最前面添加新文章卡片：

```html
<div class="article-card">
    <img src="../images/xxx.jpg" loading="lazy" alt="文章缩略图" class="article-image">
    <div class="article-info">
        <h2 class="article-title"><a href="新文章文件名.html">文章标题</a></h2>
        <p class="article-excerpt">文章摘要（80-120字）</p>
        <div class="article-meta">
            <span class="category">分类</span>
            <span class="date">YYYY-MM-DD</span>
        </div>
    </div>
</div>
```

#### 步骤3：更新首页最新动态

编辑文件：`index.html`

在 `<div class="news-grid">` 的最前面添加新闻卡片：

```html
<div class="news-card">
    <a href="articles/新文章文件名.html">
        <div class="news-image">
            <img src="images/xxx.jpg" alt="文章标题" loading="lazy">
        </div>
        <div class="news-content">
            <div class="news-tag">分类标签</div>
            <h3 class="news-title">文章标题</h3>
            <p class="news-excerpt">简短摘要（50-80字）</p>
            <div class="news-meta">
                <span class="news-date">YYYY-MM-DD</span>
                <span class="news-read-more">阅读更多 →</span>
            </div>
        </div>
    </a>
</div>
```

**注意**：保持首页展示6篇文章，添加新文章后删除最旧的一篇。

#### 步骤4：更新站点地图

编辑文件：`sitemap.xml`

在 `</urlset>` 之前添加：

```xml
<url>
  <loc>https://www.sdjnhnt.cn/articles/新文章文件名.html</loc>
  <lastmod>YYYY-MM-DDThh:mm:ss+00:00</lastmod>
  <priority>0.80</priority>
</url>
```

#### 步骤5：提交到Git并推送

```powershell
# 1. 查看更改
git status

# 2. 添加所有更改
git add .

# 3. 提交（写清楚修改内容）
git commit -m "新增文章：文章标题"

# 4. 推送到GitHub（自动认证）
git push
```

---

### 二、修改现有内容

#### 修改文章
1. 直接编辑对应的HTML文件
2. 按照上述Git流程提交

#### 修改首页内容
1. 编辑 `index.html`
2. 按照上述Git流程提交

#### 替换图片
1. 将新图片放入 `images/` 目录
2. 确保文件名与HTML中的引用一致
3. 按照上述Git流程提交

---

### 三、Git版本管理

#### 常用命令

```powershell
# 查看状态
git status

# 查看提交历史
git log --oneline

# 查看具体更改
git diff

# 撤销未提交的更改
git checkout -- 文件名

# 回滚到上一个版本（谨慎使用）
git reset --hard HEAD~1
git push --force  # 强制推送
```

#### 分支管理（如需要）

```powershell
# 创建新分支
git branch feature-新功能

# 切换分支
git checkout feature-新功能

# 合并分支
git checkout main
git merge feature-新功能

# 删除分支
git branch -d feature-新功能
```

---

## 📅 内容更新计划建议

### 每月更新频率
- **技术文章**：1-2篇
- **项目案例**：1篇（每季度）
- **行业资讯**：1篇

### 推荐文章主题库

#### 季节性内容
- 春季：混凝土施工质量控制、雨季施工注意事项
- 夏季：高温天气混凝土养护、夏季施工技术
- 秋季：最佳施工季节指南、质量验收要点
- 冬季：冬季施工技术、防冻措施（已有）

#### 技术类
- 不同标号混凝土选型指南
- 大体积混凝土浇筑技术
- 混凝土配合比设计原理
- 新型外加剂应用
- 质量检测方法详解

#### 市场类
- 济南混凝土价格走势分析（季度更新）
- 原材料市场动态
- 行业发展趋势

#### 案例类
- 重点工程项目案例
- 特殊工程解决方案
- 客户见证与评价

---

## 🔐 安全注意事项

### ⚠️ 敏感文件保护

以下文件已加入 `.gitignore`，**不会**上传到GitHub：
- ❌ `*.pfx` - SSL证书文件
- ❌ `pfx-password.txt` - 证书密码
- ❌ `*.log` - 日志文件
- ❌ `Thumbs.db` - Windows缩略图

**重要**：永远不要将这些敏感文件添加到Git！

### 备份策略

1. **Git版本控制**：每次修改都提交到GitHub
2. **本地备份**：定期复制整个网站目录到其他位置
3. **服务器备份**：联系服务器管理员确认备份策略

---

## 🌐 网站技术信息

### SEO配置
- **百度统计ID**：a5988b5014577e4dbdf885ca62672b8b
- **ICP备案**：鲁ICP备17017128号-4
- **Sitemap**：https://www.sdjnhnt.cn/sitemap.xml
- **Robots**：允许所有搜索引擎抓取

### HTTPS配置
- **SSL证书**：已配置（证书文件在根目录，但未上传到Git）
- **重定向规则**：HTTP→HTTPS，非WWW→WWW（见web.config）

### 响应式设计
- 支持PC端和移动端自适应
- 断点：768px（平板）、1024px（桌面）

---

## 📞 联系信息

- **公司名称**：济南钧华商砼混凝土有限公司
- **联系电话**：18668933108
- **服务区域**：济南市历下区、市中区、槐荫区、高新区等
- **搅拌站地址**：
  - 历下区：花园东路
  - 市中区：十六里河
  - 槐荫区：经十西路

---

## 🛠️ 故障排查

### 问题1：Git推送失败 - 网络连接问题

**症状**：
```
fatal: unable to access 'https://github.com/...'
Failed to connect to github.com port 443
```

**解决方法**：
1. 检查网络连接
2. 稍后重试：`git push`
3. 如需代理，配置Git代理：
   ```powershell
   git config --global http.proxy http://proxy-server:port
   git config --global https.proxy http://proxy-server:port
   ```

### 问题2：Git推送失败 - 认证问题

**症状**：
```
Authentication failed
```

**解决方法**：
1. 清除凭证：
   ```powershell
   cmdkey /delete:LegacyGeneric:target=git:https://github.com
   ```
2. 重新推送，会弹出登录窗口
3. 使用GitHub Personal Access Token登录

### 问题3：合并冲突

**症状**：
```
CONFLICT (content): Merge conflict in xxx.html
```

**解决方法**：
1. 打开冲突文件，查找 `<<<<<<<` 和 `>>>>>>>` 标记
2. 手动解决冲突，保留需要的内容
3. 标记为已解决：
   ```powershell
   git add 文件名
   git commit -m "解决合并冲突"
   ```

### 问题4：网站显示异常

**检查清单**：
1. 检查HTML语法是否正确
2. 检查文件路径是否正确（特别是图片路径）
3. 检查浏览器控制台是否有错误
4. 清除浏览器缓存后重试

---

## 📊 性能监控

### 百度统计
- 访问 https://tongji.baidu.com
- 查看访问量、访客来源、热门页面等数据
- 重点关注：
  - 文章页面浏览量
  - 用户停留时间
  - 跳出率

### SEO效果
- 定期在百度搜索"济南混凝土"等关键词
- 检查网站排名变化
- 使用百度搜索资源平台提交sitemap

---

## 📝 更新日志

| 日期 | 版本 | 更新内容 | 操作人 |
|------|------|---------|--------|
| 2026-03-15 | v1.1 | 新增文章《2026年春季混凝土施工质量控制要点》 | AI助手 |
| 2026-03-15 | v1.0 | 初始化Git仓库，首次备份到GitHub | AI助手 |
| 2024-xx-xx | - | 网站初始版本上线 | - |

---

## 💡 最佳实践

1. **定期更新**：保持每月至少1篇新文章，维持网站活跃度
2. **SEO优化**：每篇文章都要做好标题、描述、关键词优化
3. **图片优化**：图片大小控制在200KB以内，使用懒加载
4. **内容质量**：文章要有实际价值，避免空洞内容
5. **及时备份**：每次修改后立即提交Git
6. **测试验证**：发布前在浏览器中预览，确保显示正常
7. **移动优先**：确保手机端显示良好

---

## 🔗 相关资源

- **GitHub仓库**：https://github.com/sdjnllj/jnhnt
- **百度统计**：https://tongji.baidu.com
- **百度搜索资源平台**：https://ziyuan.baidu.com
- **Git官方文档**：https://git-scm.com/doc
- **HTML5参考**：https://developer.mozilla.org/zh-CN/docs/Web/HTML

---

## ❓ 常见问题

### Q: 如何快速创建新文章？
A: 复制 `article_template.html` 或现有文章，修改内容和文件名即可。

### Q: 图片应该放在哪里？
A: 放在 `images/` 目录下，文章中引用时使用 `../images/xxx.jpg`。

### Q: 多久更新一次比较好？
A: 建议每月1-2篇新文章，保持网站活跃度。

### Q: 如果改错了怎么办？
A: 使用Git回滚功能，可以恢复到之前的任何版本。

### Q: 需要懂编程才能维护吗？
A: 只需要基本的HTML知识，大部分工作就是复制粘贴和修改文字。

---

**最后更新**：2026-03-15  
**文档版本**：v1.0  
**维护人员**：济南钧华商砼技术团队
