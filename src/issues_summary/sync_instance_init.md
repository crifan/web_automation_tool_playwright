# 初始化Sync的playwright的实例

Playwright的代码，初始化Playwright实例：

之前的常见的with写法是

```python
from playwright.sync_api import sync_playwright

with sync_playwright() as p:
    for browser_type in [p.chromium, p.firefox, p.webkit]:
        browser = browser_type.launch()
        ...
```

此处希望初始化一个全局的playwright的实例，供后续使用。

所以就去掉with，改为普通赋值：

```python
    p = sync_playwright()
```

报错：

**错误原因**：不是很懂。

**解决办法**：找到了规避的办法：

参考官网和别人例子，加上`.start()`：

```python
p = sync_playwright().start()
```

即可。
