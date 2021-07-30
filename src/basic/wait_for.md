# 等待元素出现

用`page`的`wait_for_selector`

## 举例

### 等待百度搜索结果页显示

```python
    SearchFoundWordsSelector = 'span.nums_text'
    page.wait_for_selector(SearchFoundWordsSelector, state="visible")
```

效果：可以找到后续元素了

![wait_for_selector_after_found_element](../assets/img/wait_for_selector_after_found_element.png)

### 等待google搜索结果页显示

代码：

```python
    # 底部 Goooooooogle 多页面导航的部分，确保出现 -》 避免页面加载不完整，后续搜索结果只有2个，而不是完整的个数（一般是8/9/10个）
    # <table class="AaVjTc" style="border-collapse:collapse;text-align:left" role="presentation">
    bottomNaviPageSelector = "table[role='presentation']"
    page.wait_for_selector(bottomNaviPageSelector, state="visible")
```

页面：

![playwright_waitfor_google_result](../assets/img/playwright_waitfor_google_result.png)

即可实现希望的效果：

* 确保底部多页导航部分也的确显示了
* 确保了页面全部已加载完毕

-> 后续搜索结果就正常了：可以找到全部的结果，一般是8，9，10个。


## 官网资料

* 相关资料
  * [page.wait_for_event(event, **kwargs)](https://playwright.dev/python/docs/api/class-page#pagewait_for_eventevent-kwargs)
  * [page.wait_for_function(expression, **kwargs)](https://playwright.dev/python/docs/api/class-page#pagewait_for_functionexpression-kwargs)
  * [page.wait_for_load_state(**kwargs)](https://playwright.dev/python/docs/api/class-page#pagewait_for_load_statekwargs)
  * [page.wait_for_selector(selector, **kwargs)](https://playwright.dev/python/docs/api/class-page#pagewait_for_selectorselector-kwargs)
  * [page.wait_for_timeout(timeout)](https://playwright.dev/python/docs/api/class-page#pagewait_for_timeouttimeout)
