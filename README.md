# 怎么制作一个静态网站

## 效果预览

[http://book_template.icopy.site](http://book_template.icopy.site)


##  如何制作电子书/内容站

1. 以本仓库为模板创建仓库
   
2. 克隆到本地，修改配置文件
   
3. 在docs目录下创建目录和markdown文件  

4. 发布网站
   
5. 绑定自己的域名


## 详细步骤

### 1. 使用模板创建仓库


### 2. 克隆仓库，修改配置文件

#### mkdocs.yml 修改说明

```yml

site_name: 模板  # 网站名称
site_url: https://template.icopy.site/  # 域名
theme:
  font: false
  name: material
  custom_dir: overrides
  palette:  # 主题颜色选择
    primary: black
    accent: white
  language: zh  # 语言
  features:
    - navigation.top

extra_css:
  - stylesheets/extra.css
extra_javascript:
  - javascripts/extra.js

plugins:
  - search:
      prebuild_index: true
      lang: ja   #不支持中文，凑合用日语规则
markdown_extensions:
  - pymdownx.superfences
  - pymdownx.details
  - admonition
  - toc:
      toc_depth: 3  #右侧toc显示到几级标题
      permalink: true

```

#### overrides/partials/integrations/disqus.html

```html
{# 替换disqus块的位置，最终会插入到每个页面正文最下方#}

<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<ins class="adsbygoogle"
     style="display:block; text-align:center;"
     data-ad-layout="in-article"
     data-ad-format="fluid"
     data-ad-client="ca-pub-XXXXXXXXXXX"
     data-ad-slot="XXXXXXX"></ins>
<script>
     (adsbygoogle = window.adsbygoogle || []).push({});
</script>

```

#### overrides/partials/integrations/analytics/google.html

```html
{# 替换google统计位置，最终插入每个页面的 head块内#}
<script>
var _hmt = _hmt || [];
(function() {
  var hm = document.createElement("script");
  hm.src = "https://hm.baidu.com/hm.js?XXXXXXXXXXXXXXX";
  var s = document.getElementsByTagName("script")[0]; 
  s.parentNode.insertBefore(hm, s);
})();
</script>

```

#### docs/CNAME
修改成你自己的域名
```html
book_template.icopy.site
```

### 3. docs下创建markdown内容

mkdocs会从markdown文件中找到1级标题作为文件名

自动生成的目录顺序是按照文件名的字符顺序

如果需要自定义顺序，在mkdocs.yml 增加nav配置，手工设置目录，举例如下：
```yml
nav:
  - 首页: "index.md"
  - 第一章:
    - 第一节: "第一章/第一节.md"
    - 第二节: "第一章/第二节.md"
    - 第三节: "第一章/第三节.md"
    - 第四节: "第一章/第四节.md"
```


### 3. 发布网站

仓库改动提交到github，会自动构建


#### 3.1 发布到github pages

1. github pages设置，指定网站html对应的分支和根目录


2. 绑定自己的域名


#### 3.2 发布到vercel

与github pages 配置类似，可以网上搜索教程，国内访问速度更快

仓库已经包含发布到vercel所需的配置文件，vercel直接默认选项就能发布

