## SMS API Specification


### API Specification



#### SMS API Specification


##### POST /v1/:app/sms/template

注册一个 application 短信模板信息。由 [Board](https://github.com/arkors/board) 模块通过 UI 界面进行调用。

###### Example Request:
```
POST /v1/233/sms/template HTTP/1.1
Host: sms.arkors.com
X-Arkors-application-Log: 5024442115e7bd738354c1fac662aed5
X-Arkors-application-Client: xxx.xx.xx.xxx,BOARD
Accept: application/json
{
  "template": "你好，欢迎{{.username}}加入csdn,您的验证码为{{.verificationCode}}",
  "description": "验证邮件",
  "name": "verification",
  "tag": "verification"
}
```


###### Example Response

```
HTTP/1.1 201 OK
X-Arkors-application-Log: cb21df532c6647383af7efa0fd8405f2
Content-Type: application/json
{
  "app": 233,
  "id": 1
}
```

###### Status Codes:
* 201 – 创建 application的SMS template 记录成功
* 400 – Errors (invalid json, missing, duplication or invalid fields, etc)


##### GET /v1/:app/template

客户端访问 /v1/:app/sms/template，发送当前运行版本号的ID，获取app的所有邮件模板信息

###### Example Request:
```
GET /v1/233/sms/template HTTP/1.1
Host: sms.arkors.com
X-Arkors-application-Log: 5024442115e7bd738354c1fac662aed5
X-Arkors-application-Client: 3ad3ce877d6c42b131580748603f8d6a,ANDROID
Accept: application/json
```


###### Example Response
```
HTTP/1.1 200 OK
X-Arkors-application-Log: cb21df532c6647383af7efa0fd8405f2
Content-Type: application/json
{
  "templates":[ 
    {
     "id": 1,
     "app": 233,
     "name": "activation",
     "description": "用户激活",
     "tag": "activation",
     "created": "2014-07-16T00:00:00Z",
     "updated": "2014-07-16T00:00:00Z"
    },
    {
     "id": 2,
     "app": 233,
     "name": "family",
     "description": "家庭邮件",
     "tag": "问候",
     "created": "2014-07-16T00:00:00Z",
     "updated": "2014-07-16T00:00:00Z"
    }
  ]
}
```


###### Status Codes:
* 200 - 返回 application 注册SMS模板信息。
* 400 - Errors (invalid json, missing or invalid fields, etc)
* 404 - 没有application的SMS模板信息 


##### GET /v1/:app/sms/template/:id

客户端访问 /v1/:app/sms/template/:id ，获取app邮件的某个模板信息

###### Example Request:
```

GET /v1/233/sms/template/1 HTTP/1.1
Host: sms.arkors.com
X-Arkors-application-Log: 5024442115e7bd738354c1fac662aed5
X-Arkors-application-Client: 3ad3ce877d6c42b131580748603f8d6a,ANDROID
Accept: application/json
```

###### Example Response
```
HTTP/1.1 200 OK
X-Arkors-application-Log: cb21df532c6647383af7efa0fd8405f2
Content-Type: application/json
{
  "id": 1,
  "app": 233,
  "name": "activition",
  "templete": "你好，欢迎{{.username}}加入csdn,您的验证码为{{.verificationCode}}",
  "description": "用户验证",
  "tag": "activition",
  "created": "2014-07-16T00:00:00Z",
  "updated": "2014-07-16T00:00:00Z"
}

```
###### Status Codes:
* 200 - 返回 application 注册SMS模板信息。
* 400 - Errors (invalid json, missing or invalid fields, etc)
* 404 - 没有application的SMS模板信息
