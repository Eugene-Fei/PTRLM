# PetRealm（PTRLM）静态网站使用说明

本文件夹包含 PetRealm 完整的外贸 B2B 静态网站，以及一套可重复使用的产品详情页系统。网站可部署到 EdgeOne Pages、Cloudflare Pages、Netlify、GitHub Pages、普通云服务器，也可以直接在本地查看。

## 一、网站页面

- `index.html`：首页
- `products.html`：批发产品列表
- `product-detail.html?product=raincoat`：产品详情页模板
- `oem.html`：OEM 与定制服务
- `about.html`：公司介绍
- `contact.html`：联系方式与完整询盘表单
- `thank-you.html`：询盘提交成功后的感谢页面

## 二、产品详情页

目前九款产品全部使用同一套静态详情页模板。网址中的 `product` 参数决定显示哪一款产品，例如：

```text
product-detail.html?product=raincoat
product-detail.html?product=cat-tower
```

产品资料和六种语言的详情页文案存放在：

```text
js/product-detail.js
```

其中：

- `PRODUCTS`：产品名称、款号、图片、材质、MOQ、交期、包装、尺寸等资料
- `DETAIL_LANGS`：详情页公共内容的六语言翻译

每个产品详情页包含以下模块：

1. HERO 产品主视觉
2. 产品简短介绍
3. 产品图片画廊
4. 产品规格表
5. 材质与护理说明
6. 尺寸表和测量方式
7. 认证及合规文件预留位置
8. OEM / ODM 定制能力
9. 工厂图片和质检视频位置
10. 采购商常见问题
11. 产品询盘表单和 WhatsApp 按钮

## 三、以后新增产品

每增加一款产品，需要同时完成以下操作：

1. 在 `products.html` 中新增产品卡片。
2. 为产品卡片设置详情页链接，例如：

```text
product-detail.html?product=新产品英文标识
```

3. 在 `js/product-detail.js` 的 `PRODUCTS` 中新增一组产品资料。
4. 添加英文、中文、西班牙语、法语、德语、日语产品文案。
5. 将产品图片放入 `images` 文件夹并填写对应路径。
6. 检查款号、材质、MOQ、交期、包装、重量和尺寸信息。
7. 测试产品询盘，确认 Forminit 邮件中包含产品名称和款号。

网站中的 `OEM`、`ODM`、`MOQ`、`FOB`、`TFPIA`、`OEKO-TEX`、`Prop 65` 等专业术语保留英文，其他面向客户的内容跟随客户选择的语言。

## 四、替换图片和视频

所有图片和视频统一存放在：

```text
images/
```

可以使用以下两种方式替换：

1. 使用新图片覆盖原文件，并保持原文件名不变。
2. 修改 HTML 或 `js/product-detail.js` 中的 `images/文件名` 路径。

推荐尺寸：

- 产品图片：竖版 4:5，建议不低于 1200 × 1500 px
- 工厂和团队图片：横版，建议不低于 1600 × 1100 px
- 首页视频：MP4、H.264 编码，建议 1920 × 1080，尽量控制在 20–30 MB 以内

当前首页视频路径：

```text
images/hero-dog-raincoat.mp4
```

为了提升网站速度，建议产品图片使用 WebP 格式并尽量控制在 300 KB 以内。

## 五、Forminit 询盘表单

网站已经连接 Forminit 表单：

```text
https://forminit.com/f/l3ywq1fd67d
```

Forminit 表单 ID：

```text
l3ywq1fd67d
```

Forminit 接收邮箱：

```text
sales@ptrlm.com
```

网站使用 Forminit 官方 SDK 提交询盘，字段名称已经按照 `fi-` 格式设置。产品详情页提交时，会自动附带产品款号和产品名称。

WhatsApp 号码必须使用国际格式，例如：

```text
+8617766177091
```

建议在 Forminit 后台将提交成功跳转地址设置为：

```text
https://www.ptrlm.com/thank-you.html
```

附件大小限制取决于当前 Forminit 套餐。

## 六、认证文件说明

网站目前没有展示任何未经确认的认证声明。

产品详情页中的 `OEKO-TEX Standard 100`、`Prop 65` 和其他市场合规文件均为待添加位置，PDF 下载按钮暂时不可点击。

只有在证书或检测报告满足以下条件后才可以正式展示：

- 文件真实有效
- 适用于对应产品或准确材料
- 证书编号和有效期已经核实
- PDF 文件已经上传到网站

后续获得真实认证资料时，需要同时更新：

1. 对应产品详情页的认证文件和下载链接。
2. 首页合适位置的认证实力展示模块。

## 七、修改网站配色

打开：

```text
css/style.css
```

修改文件开头的颜色变量：

```css
:root {
  --ink: #20211f;
  --paper: #f4f2eb;
  --white: #fbfaf6;
  --khaki: #c8c0aa;
  --line: #d8d5cc;
  --muted: #6e706b;
}
```

对应关系：

- `--ink`：炭黑色文字和深色按钮
- `--paper`：网站米白背景
- `--white`：浅色内容区域
- `--khaki`：浅卡其辅助色
- `--line`：边框和分隔线
- `--muted`：次要文字颜色

## 八、修改文字和语言

网站支持：

- 英文
- 中文
- 西班牙语
- 法语
- 德语
- 日语

公共页面翻译存放在：

```text
js/main.js
```

产品详情页翻译存放在：

```text
js/product-detail.js
```

客户选择语言后，网站会将选择记录在客户浏览器中，进入其他页面时继续使用该语言。

修改文案时，需要同步检查六种语言，避免菜单、小标题、表单、下拉选项或产品信息遗漏翻译。

## 九、部署到 EdgeOne

可以将整个 `petrealm-website` 文件夹上传到 EdgeOne，也可以直接使用已经生成的：

```text
petrealm-website.zip
```

部署时必须保持原有文件夹结构，不能将 `css`、`js`、`images` 中的文件移动到其他位置。

网站入口文件为：

```text
index.html
```

部署完成后建议检查：

1. 首页视频是否正常播放。
2. 图片是否正常加载。
3. 六种语言是否能够切换。
4. 九款产品是否能够进入对应详情页。
5. 手机端是否存在错位或横向滚动。
6. Forminit 询盘是否能够提交。
7. 企业邮箱是否收到通知邮件。
8. 提交后是否进入 `thank-you.html`。

## 十、EdgeOne 后台方案

关于 GitHub、EdgeOne Pages 和 Decap CMS 的后台管理方案，请查看：

```text
EDGEONE-CMS-PLAN.md
```

CMS 登录功能需要 GitHub OAuth。只有在 GitHub 仓库和最终域名确认后，才建议正式配置后台登录。
