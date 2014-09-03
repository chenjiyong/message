API Specification



Email API Specification


POST /v1/auth/:app
注册一个 application 账户信息。由 Board 模块通过 UI 界面进行调用。



Example Request:POST /v1/auth/233 HTTP/1.1
Host: auth.arkors.com
X-Arkors-application-Log: 5024442115e7bd738354c1fac662aed5
X-Arkors-application-Client: xxx.xx.xx.xxx,BOARD
Accept: application/json
{
  "user_name":"wlw",
  "name":"aw",
  "passwd":"wlw123"
}




Example Response:HTTP/1.1 201 OK
X-Arkors-application-Log: cb21df532c6647383af7efa0fd8405f2
Content-Type: application/json
{
  "app": 233,
  "id": 1
}




Status Codes:•201 – 创建 auth的账户信息成功
•400 – Errors 



POST /v1/:app/auth


Example Request:POST /v1/233/auth HTTP/1.1
Host: email.arkors.com
X-Arkors-application-Log: 5024442115e7bd738354c1fac662aed5
X-Arkors-application-Client: 3ad3ce877d6c42b131580748603f8d6a,ANDROID
Accept: application/json
{
  "user_name":"wlw",
  "passwd":"wlw123"
}




Example ResponseHTTP/1.1 201 OK
X-Arkors-application-Log: cb21df532c6647383af7efa0fd8405f2
Content-Type: application/json
{
  "id":1,
  "app": 233,
  "name":"aw"
}




Status Codes:•201 – 登陆成功
•400 – Errors 
•404 - 没有该账户信息 
