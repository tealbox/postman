# Postman <<>> Tips & Tricks
1). Extract Cookie from response and set as global variable.

===========================================================
Url = https://10.10.20.90
POST {{Url}}/j_security_check
header 'Content-Type: application/x-www-form-urlencoded'
payload = 'j_username=admin&j_password=C1sco12345'
body: >> x-www-form-urlencoded create two keys:
j_username=admin
j_password=C1sco12345
in the Tests write following code to get JSESSIONID in cookie
pm.environment.set('cookie', pm.cookies.get('JSESSIONID'))
===========================================================
GET {{Url}}/dataservice/client/token
in Headers set key "Cookie" to {{cookie}}
in Tests put following code:
pm.environment.set("X-XSRF-TOKEN", pm.response.text())
===========================================================

