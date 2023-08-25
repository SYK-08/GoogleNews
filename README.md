# GoogleNews

[![Build Status](https://app.travis-ci.com/Iceloof/GoogleNews.svg)](https://app.travis-ci.com/github/Iceloof/GoogleNews)
[![Coverage Status](https://coveralls.io/repos/github/Iceloof/GoogleNews/badge.svg)](https://coveralls.io/github/Iceloof/GoogleNews)
[![PyPI](https://img.shields.io/pypi/v/GoogleNews)](https://pypi.org/project/GoogleNews/)
[![PyPI - Downloads](https://img.shields.io/pypi/dm/GoogleNews)](https://pypistats.org/packages/googlenews)
![PyPI - Python Version](https://img.shields.io/pypi/pyversions/GoogleNews)
![PyPI - Wheel](https://img.shields.io/pypi/wheel/GoogleNews)
![GitHub contributors](https://img.shields.io/github/contributors/Iceloof/GoogleNews)
![GitHub issues](https://img.shields.io/github/issues-raw/Iceloof/GoogleNews)
![GitHub Action](https://github.com/Iceloof/GoogleNews/workflows/GitHub%20Action/badge.svg)
![GitHub](https://img.shields.io/github/license/Iceloof/GoogleNews)

## Install
```
pip install GoogleNews
```
or
```
pip install --upgrade GoogleNews
```
## Usage
- Initializing
```
from GoogleNews import GoogleNews
googlenews = GoogleNews()
```
- Check version
```
print(googlenews.getVersion())
```
- Enable to throw an exception
```
googlenews.enableException(True)
```
- Optional choose language
```
googlenews = GoogleNews(lang='en')
```
or
```
googlenews = GoogleNews(lang='en', region='US')
```
- Optional choose period (period and custom day range should not be set together)
```
googlenews = GoogleNews(period='7d')
```
- Optional choose custom day range (mm/dd/yyyy)
```
googlenews = GoogleNews(start='02/01/2020',end='02/28/2020')
```
- Optional set encode
```
googlenews = GoogleNews(encode='utf-8')
```
or
```
googlenews.set_lang('en')
googlenews.set_period('7d')
googlenews.set_time_range('02/01/2020','02/28/2020')
googlenews.set_encode('utf-8')
```
- **news.google.com** search sample
```
googlenews.get_news('APPLE')
```
- **google.com** section news search sample
```
googlenews.search('APPLE')
```

Default return first-page result, you don't need to get the first page again, otherwise you might get a duplicate result. To get other pages of search results:

```
googlenews.get_page(2)
```
- If you only want to get a specific page
```
result = googlenews.page_at(2)
```
- If you want to get the total result number of the search(this is an approximate number, not the exact number, it is the number showing on the Google search page) (Note: this function is not available for `googlenews.search()`)
```
googlenews.total_count()
```
- Get results will return the list, `[{'title': '...', 'media': '...', 'date': '...', 'datetime': '...', 'desc': '...', 'link': '...', 'img': '...'}]`
```
googlenews.results()
```
if `googlenews.results(sort=True)` the tool will try to order the results in chronologically reversed order

- Get texts will return the list of news titles
```
googlenews.get_texts()
```
- Get links returns the list of news links
```
googlenews.get_links()
```
- Clear the result list before doing another search with the same object
```
googlenews.clear()
```
## Issue
The image is not working in the latest version, it can only return the default Google loading gif

The date range is not always working as Google may return the result in random order or out-of-date range.

Google may recognize the program as an automated robot and block the IP, using a cloud server and fetching data with high frequency will get a higher chance of being blocked. 
