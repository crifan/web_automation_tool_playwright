# 给playwright加代理

此处给playwright（的chromium）加上代理的方式是：

* 给全局加代理

```python
from playwright.sync_api import sync_playwright

googleHomeUrl = "https://www.google.com/"

PROXY_HTTP = "http://127.0.0.1:58591"
# PROXY_SOCKS5 = "socks5://127.0.0.1:51837"

browserLaunchOptionDict = {
    "headless": False,
    "proxy": {
        "server": PROXY_HTTP,
    }
}

with sync_playwright() as p:
    chromiumBrowserType = p.chromium

    browser = chromiumBrowserType.launch(**browserLaunchOptionDict)

    page = browser.new_page()

    page.goto(googleHomeUrl)
```

即可实现：全局所有页面，自动用上代理 -》 可以正常打开google
