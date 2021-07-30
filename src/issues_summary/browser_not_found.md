# browser was not found

代码：

```python
browser = p.chromium.launch(**browserConfig)
```

报错：

```bash
发生异常: Error
================================================================================
"chromium" browser was not found.
Please complete Playwright installation via running
    "python -m playwright install"
```

**错误原因**：没有找到Playwright所安装的，此处用到的，底层的driver浏览器：chromium

**背景**：但是其实之前已在当前Mac中全局安装过

`playwright install`

安装到了：

`/Users/limao/Library/Caches/ms-playwright/chromium-888113`

对应chromium二进制路径是：

`/Users/limao/Library/Caches/ms-playwright/chromium-888113/chrome-mac/Chromium.app/Contents/MacOS/Chromium>`

但是此处竟然找不到。

**根本原因**：估计是此处是某Python项目的虚拟环境，导致没检测到，之前Python全局安装的chromium？

**解决办法**：只需，只能，重新安装一次即可

**具体步骤**：

```bash
python -m playwright install
```

**附录**：

正常启动输出：

```bash
curBrowserType=<BrowserType name=chromium executable_path=/Users/limao/Library/Caches/ms-playwright/chromium-901522/chrome-mac/Chromium.app/Contents/MacOS/Chromium>
browser=<Browser type=<BrowserType name=chromium executable_path=/Users/limao/Library/Caches/ms-playwright/chromium-901522/chrome-mac/Chromium.app/Contents/MacOS/Chromium> version=93.0.4576.0>
```
