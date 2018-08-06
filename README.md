## APEC 前端开发工具库

### 基础用法
安装
```
npm install apec-fe-utils
```

全量引入
```
import * as utils from 'apec-fe-utils';

使用示例:
utils.url.getQueryString('date');
```
或者

按需引入
```
import { url, https } from 'apec-fe-utils';

使用示例:
url.getQueryString('date');
```
### 所有方法
##### 日期时间格式化
```
1. formatTime
  /**
   * 时间戳转日期时间 eg: 1505174400000 => 2017-09-12 14:34:23
   * @param  {String} timestamp 时间戳
   * @return {String}           日期时间
   */

2. formatDate
  /**
   * 时间戳转日期 eg: 1505174400000 => 2017-09-12
   * @param  {String} timestamp 时间戳
   * @return {String}           日期
   */

3. formatTimeObj
  /**
   * 时间戳转日期 eg: 1505174400000 => 2017-09-12
   * @param  {String} timestamp 时间戳
   * @return {Object}           时间日期
   */

4. unixTime
  /**
   * 日期转时间戳 eg: 2017-09-12 => 1505174400000
   * @param  {String} datetime 日期字符串
   * @return {number}          时间戳
   */

5. getTimestamp
  /**
   * 获取当前时间戳
   * @return {number} 时间戳
   */

6. getTimeDetailRemain
  /**
   * 根据时间戳返回 距离此时间戳还有多少时分秒【倒计时用】
   * @param  {string} timestamp 时间戳
   * @return {object}           时间对象
   */

```
##### cookie操作
```
1. getCookie
  /**
   * 获取cookie
   * @param  {String} name  cookie名
   * @return {String} value cookie值
   */

2. setCookie
  /**
   * 设置cookie值
   * @param {String} name cookie名
   * @param {String} val  cookie值
   * @param {String} sec  失效时间
   */

3. clearCookie
  /**
   * 清除指定cookie
   * @param {String} name cookie名
   * @return {null}      无
   */

4. clearAllCookie
  /**
   * 清除所有cookie
   * @return {null}      无
   */

5. getValue
  // 获取存在localstorage或者cookie中的值

6. setValue
  /**
   * 将值存入localStorage
   * @param {String} name localStorage名
   * @param {String} val  localStorage值
   */

7. removeValue
  /**
   * 将值从localStorage删除
   * @param {String} name localStorage名
   */

```

##### url操作
```
1. getQueryString
  /**
   * 获取链接中指定键名对应的键值 当url不传时取window.location.href
   * @param  {String} name 键名
   * @param  {String} url  链接地址[可不传]
   * @return {String}      键值
   */

2. getQueryName
  /**
   * getQueryString方法的正则辅助方法
   * @param  {String} name 键名
   * @param  {String} url  链接地址[可不传]
   * @return {String}      键值
   */

3. updateQueryString
  /**
   * 更新链接中某一键值对的值(当匹配不到时往链接中添加该键值对) 当url不传时取window.location.href
   * @param  {String} name  键名
   * @param  {String} value 键值
   * @param  {String} url   链接地址[可不传]
   * @return {String}       链接地址
   */

4. parseURL
  /**
   * 获取链接的属性
   * @param  {String} url 链接地址
   * @return {Object}     链接的属性值
   */

5. getFullPath
  /**
   * 获取url的完整路径
   * @return {String} 完整路径 eg: http://heygeys.cn/test/index.html/#/home => http://heygeys.cn/test/
   */

```

##### 表单校验
```
validator
  /**
    * 表单验证规则：
    * 1. 在js中调用 validator.rule(param)
    *      将rule替换为方法名,param为需要进行验证的参数
    *
    * 2. 运算完后返回布尔值，true为通过，false为不通过
    *
    * 3. 方法名                 与         对应的验证规则如下：
    *      intNum              -----     整数
    *      priceNum            -----     至多两位小数数字（多用于价格和金额）
    *      phone               -----     手机号
    *      email               -----     电子邮箱
    *      confirmPassword     -----     确认密码
    *      amount              -----     金融数字
    *      dateTime            -----     日期时间
    *
    *  **/
```
##### 金额格式化
```
toFinancialNum
  /**
   * 将参数格式化为千分位金额
   * @param  {String | Number} num 待格式化数字
   * @param  {Number} digit = 2 保留小数位数, 默认2位
   * @param  {String} symbol = '￥' 格式化符号, 默认为人民币
   * @return {String} financialNum 格式化后金额 16937.6588 => ￥16,937.66
   */
```

##### 自动文本框
```
autoTextarea
  /**
    * 文本框根据输入内容自适应高度
    * @param                {HTMLElement}            输入框元素
    * @param                {Number}                设置最大高度(可选)
    * @param                {Number}                设置光标与输入框保持的距离(默认0)
    */
```

##### 键值匹配器
```
keyMatcher
  /**
    * 键值匹配器
    * @param {String} val 待匹配原始值
    * @param {Array} list 匹配枚举对象数组
    * @param {String} key = 'key' 对应输入键的字段名
    * @param {String} name = 'name' 对应输出文字的字段名
    * @return {Object} result = {
    *   name,
    *   info: {},
    * }
    * */
```

##### axios基础配置
```
https
  /**
    * 主要用法:
    * https.post(url, param, configs).then(res => {}).catch(err => {})
    * https.get(url, param, configs).then(res => {}).catch(err => {})
    *
    * @param {String} url 请求地址
    * @param {Object} param 请求参数, 直接使用对象即可, 封装方法已帮助JSON.stringify
    * @param {Object} configs 额外配置, 支持axios的所有配置项, 详见axios文档: https://github.com/axios/axios/blob/master/README.md#request-config
    * @return {Promise} 返回Promise链, 用户需自行.then(res => {}).catch(err => {})
    *
    * 备注: 直接then的res为请求响应对象, 后续then需用户自行return res
    * */
```
