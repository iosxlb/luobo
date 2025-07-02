# GitHub 防红跳转系统（luobofh）

## 用途

本项目用于防止微信、QQ等社交平台屏蔽外链，通过本项目生成跳转链接可绕过平台检测。

## 使用方法

1. 将目标网址（如 `http://abc.com`）用 base64 编码，例如：  
   `http://abc.com` → `aHR0cDovL2FiYy5jb20=`

2. 拼接跳转链接：  
   `https://iosxlb.github.io/luobofh/?c=编码结果`

   例如：  
   `https://iosxlb.github.io/luobofh/?c=aHR0cDovL2FiYy5jb20=`

3. 打开该链接即可自动跳转到目标网址。

## 自动生成工具

可将以下代码保存为 `generate.html`，本地打开自动生成跳转链接：

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>防红跳转链接生成器</title>
</head>
<body>
  <h2>防红跳转链接自动生成</h2>
  <p>跳转系统地址（如 https://iosxlb.github.io/luobofh/）</p>
  <input type="text" id="baseUrl" value="https://iosxlb.github.io/luobofh/" size="50"><br><br>
  <p>目标网址（如 http://abc.com）</p>
  <input type="text" id="targetUrl" value="http://abc.com" size="50"><br><br>
  <button onclick="makeLink()">生成跳转链接</button>
  <p>结果：</p>
  <input type="text" id="result" size="80" readonly>
  <script>
    function makeLink() {
      var base = document.getElementById('baseUrl').value;
      var target = document.getElementById('targetUrl').value;
      if (!base.endsWith('/')) base += '/';
      var encoded = btoa(target);
      document.getElementById('result').value = base + '?c=' + encoded;
    }
  </script>
</body>
</html>
```

---

## GitHub Pages 部署方法

1. 进入仓库 `Settings` → `Pages`
2. 选择 `Deploy from a branch`，分支选 `main`，目录选 `/ (root)`
3. 保存后，几分钟后即可通过  
   `https://iosxlb.github.io/luobofh/` 访问跳转页

如遇问题，欢迎随时咨询！