# 所有页面加载都超时

**背景**

之前代码：

```python
page.goto(eachShorLink)
```

报错：`Exception Timeout 10ms exceeded`

然后调试其余其他页面url，结果都报此错误。

**错误原因**：Playwright的页面超时参数的单位是**毫秒**。之前误以为秒，传入了：

```python
curPageLoadTimeout = 10
page.set_default_navigation_timeout(curPageLoadTimeout)
page.set_default_timeout(curPageLoadTimeout)
```

导致：所有页面都报超时的错误

因为：都加载时间都超过10毫秒

**解决办法**：传入参数改为毫秒值即可

**具体做法**：

```python
    curPageLoadTimeout = configDict["pageLoadTimeout"]
    curPageLoadTimeoutMilliSec = curPageLoadTimeout * 1000

        page.set_default_navigation_timeout(curPageLoadTimeoutMilliSec)
        page.set_default_timeout(curPageLoadTimeoutMilliSec)
```

详见：

官网文档：[Page | Playwright Python](https://playwright.dev/python/docs/api/class-page#page-set-default-timeout)

> page.set_default_timeout(timeout)
> 
> * `timeout` `<float>` Maximum time in **milliseconds**
