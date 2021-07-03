# 查找元素

从页面中`寻找`=`定位`=`获取`元素的函数是：

* element_handle
  * `element_handle.query_selector(selector)`
    * https://playwright.dev/python/docs/api/class-elementhandle#element_handlequery_selectorselector
  * `element_handle.query_selector_all(selector)`
    * https://playwright.dev/python/docs/api/class-elementhandle#element_handlequery_selector_allselector
* page
  * `page.query_selector(selector)`
    * https://playwright.dev/python/docs/api/class-page#pagequery_selectorselector
  * `page.query_selector_all(selector)`
    * https://playwright.dev/python/docs/api/class-page#pagequery_selector_allselector
      * 注：返回的是`JSHandle`的`list`

## 举例

```python
    resultASelector = "h3[class^='t'] a"
    searchResultAList = page.query_selector_all(resultASelector)
    print("searchResultAList=%s" % searchResultAList)
```

输出：

```bash
searchResultAList=[<JSHandle preview=JSHandle@<a target="_blank" href="http://www.baidu.com/link?…>在路上on the way - 走别人没走过的路,让别人有路可走</a>>, <JSHandle preview=JSHandle@node>, <JSHandle preview=JSHandle@node>, <JSHandle preview=JSHandle@node>, <JSHandle preview=JSHandle@node>, <JSHandle preview=JSHandle@node>, <JSHandle preview=JSHandle@node>, <JSHandle preview=JSHandle@node>, <JSHandle preview=JSHandle@node>, <JSHandle preview=JSHandle@node>]
```

![playwright_query_all_jshandle](../assets/img/playwright_query_all_jshandle.png)
