获取cookies的手段

1. 浏览器手动请求之后，将cookies复制下来

2. selenium模拟浏览器请求，获取cookies
from selenium import webdriver
driver = webdriver.Chrome()
driver.get(url)
# 获得cookie信息
cookie= driver.get_cookies()

3. 适用cookiejar获取cookie
import http.cookiejar, urllib.request
cookie = http.cookiejar.CookieJar()
opener = urllib.request.build_opener(urllib.request.HTTPCookieProcesser(cookie))
r = opener.open(url)#打开网址后cookie就会保存到cookie变量中，此处使用open方法是urllib自带的open
cookie.save('cookie.txt')

使用cookies
cookies可以通过urllib库或者requests构建请求，发送到服务器.

urllib
urllib中使用cookie要先构建一个带有cookie的opener，然后使用这个opener打开网页：
opennr = urllib.request.build_opener(cookie)
urllib.request.install_opener(opener)
urllib.request.urlopen(url)

requests
urllib库适用cookies比较麻烦，不推荐使用。
使用requests的话，代码简单得多。
如果要求代码中的所有请求都适用Cookies的话，需要创建session对象,然后将cookies传入session对象中：
s = requests.Session()
s.cookies =cookies
s.headers = headers
s.get(url)
