 
为多设备平台提供共统一的鉴权验证入口和服务入口

签名格式
   Authorization android username:password
各组成内容说明

android   固定字符，与 username 之间以空格间隔
user	 操作用户帐号
password	 签名内容


签名内容生成
   md5(METHOD&URI&DATE&CONTENT_LENGTH&md5(PASSWORD)) 
各组成内容说明

&	 字符串连接符
METHOD	 本次请求的方式
URI	 URI,必须 http 协议标准(中文文件名或目录，需进行 rawurlencode 编码 RFC1738)
DATE	 日期格式：Wed, 24 Aug 2011 09:13:05 GMT (RFC 1123)格式。请注意服务器时间必须跟世界时间一致,否则签名失败,并返回 Date offset error 错误。
CONTENT_LENGTH	 content 长度,需与请求 header 中 Content­Length 一致 (GET 方法,长度为 0)
md5(PASSWORD)	 帐号密码进行 md5 加密
注：请统一使用 UTF-8 编码格式。 

请求方法
> GET /demobucket/ HTTP/1.1
> Host: test.com
> Authorization: andord username:62c428533830d84fd8bc77bf402512fc
> Date: Wed, 24 Aug 2011 07:33:47 GMT
