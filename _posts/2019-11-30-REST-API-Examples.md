
## MY IP Example

PC'nin IPsini öğrenip nereye kayıtlı olduğu bilgisini aldık.


```python
import requests, json

ip = requests.get('http://icanhazip.com/').text.strip()
print(ip)

geoip_info = json.loads(requests.get('http://ip-api.com/json/' + ip).text)
print(geoip_info['query'], geoip_info['country'], geoip_info['city'], geoip_info['as'])

```

    176.43.218.125
    176.43.218.125 Turkey Ankara AS34984 TELLCOM ILETISIM HIZMETLERI A.S.
    

**res.json() ve json.loads(res.text) her ikisi de dict formatını veriyor.**


```python
import requests, json

ips = ['1.1.1.1', '8.8.8.8', '9.9.9.9']

for ip in ips:
    res = requests.get('http://ip-api.com/json/' + ip)
    print(res.json())

    geoip_info = json.loads(res.text)
    print(geoip_info['query'], geoip_info['country'], geoip_info['city'], geoip_info['as'])
    
    print()
```

    {'status': 'success', 'country': 'Australia', 'countryCode': 'AU', 'region': 'NSW', 'regionName': 'New South Wales', 'city': 'Sydney', 'zip': '1001', 'lat': -33.8688, 'lon': 151.209, 'timezone': 'Australia/Sydney', 'isp': 'Cloudflare, Inc.', 'org': '', 'as': 'AS13335 Cloudflare, Inc.', 'query': '1.1.1.1'}
    1.1.1.1 Australia Sydney AS13335 Cloudflare, Inc.
    
    {'status': 'success', 'country': 'United States', 'countryCode': 'US', 'region': 'VA', 'regionName': 'Virginia', 'city': 'Ashburn', 'zip': '20149', 'lat': 39.0438, 'lon': -77.4874, 'timezone': 'America/New_York', 'isp': 'Level 3', 'org': 'Google LLC', 'as': 'AS15169 Google LLC', 'query': '8.8.8.8'}
    8.8.8.8 United States Ashburn AS15169 Google LLC
    
    {'status': 'success', 'country': 'United States', 'countryCode': 'US', 'region': 'CA', 'regionName': 'California', 'city': 'Berkeley', 'zip': '94709', 'lat': 37.8806, 'lon': -122.268, 'timezone': 'America/Los_Angeles', 'isp': 'Quad9', 'org': 'Quad9', 'as': 'AS19281 Quad9', 'query': '9.9.9.9'}
    9.9.9.9 United States Berkeley AS19281 Quad9
    
    

## Cookies and Sessions


```python
import requests

res = requests.get('http://phr.arjang.ac.ir/app/index.php')
# print(res.status_code)
# print(res.headers['content-length'])

for header in res.headers:
    print('{}: {}'.format(header, res.headers[header]))

phpsessid = res.cookies['PHPSESSID']
```

    Date: Sat, 30 Nov 2019 20:06:37 GMT
    Server: Apache
    Vary: Host
    Set-Cookie: PHPSESSID=ls1rj627em41cian7l6shs58f7; path=/
    Expires: Thu, 19 Nov 1981 08:52:00 GMT
    Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
    Pragma: no-cache
    Content-Length: 248
    Connection: close
    Content-Type: text/html; charset=UTF-8
    


```python
res = requests.post('http://phr.arjang.ac.ir/app/login.php',
                   cookies={'PHPSESSID': phpsessid},
                   data={'username': 'Sara', 'password': 'foobar'})

for header in res.headers:
    print('{}: {}'.format(header, res.headers[header]))

# print(res.text)
```

    Date: Sat, 30 Nov 2019 20:06:48 GMT
    Server: Apache
    Vary: Host
    Expires: Thu, 19 Nov 1981 08:52:00 GMT
    Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
    Pragma: no-cache
    Content-Length: 64
    Keep-Alive: timeout=5, max=100
    Connection: Keep-Alive
    Content-Type: text/html; charset=UTF-8
    


```python
res = requests.get('http://phr.arjang.ac.ir/app/index.php',
                   cookies={'PHPSESSID': phpsessid})

print(res.text)
```

    
    <!doctype html>
    <html lang="en"><head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <title>
    App
    </title>
    <link rel="stylesheet" href="style.css">
    </head>
    
    <body>
    
    <h1 class="demo-title">App</h1>
    
    <h2>Welcome Sara</h2>
    
    <p>This is a restricted area your secret code is <strong>4733a44073c81970cccbca6e1ede188b</strong></p>
    
    <h3>Your request</h3>
    <pre>
    Host: phr.arjang.ac.ir
    User-Agent: python-requests/2.18.4
    Accept-Encoding: gzip, deflate
    Accept: */*
    Connection: keep-alive
    Cookie: PHPSESSID=ls1rj627em41cian7l6shs58f7
    </pre>
    <p><a href="logout.php">Logout</a></p>
    </body>
    </html>
    
    

## POST Method


```python
import requests

res = requests.post('http://phr.arjang.ac.ir/app/testpost.php',
                    data={'eee': '6666'})
print(res.text)
```

    OK, you are using POST method
    
    Array
    (
        [eee] => 6666
    )
    
    

## Weather Example


```python
import requests
from time import localtime, strftime

city = 'Ankara'
apikey = 'd9018602f134baf49774b75cc467706e'

baseurl = 'http://api.openweathermap.org/data/2.5/forecast/daily'
url = baseurl + '?appid=' + apikey + '&q=' + city + '&units=metric&cnt=16'

res = requests.get(url)
weather = res.json()

for day in weather['list']:
    print('{} {} {}'.format(strftime('%Y-%m-%d', localtime(day['dt'])), day['temp']['min'], day['temp']['max']))
```

    2019-11-30 7.55 8.75
    2019-12-01 1.71 7.28
    2019-12-02 -0.85 5.05
    2019-12-03 -0.19 8.43
    2019-12-04 -2.02 3.75
    2019-12-05 -3.35 2.2
    2019-12-06 -2.69 4.92
    2019-12-07 -0.15 6.69
    2019-12-08 0.08 5.8
    2019-12-09 -1.52 6.78
    2019-12-10 3.37 6.36
    2019-12-11 3.32 4.23
    2019-12-12 1.84 7.53
    2019-12-13 1.72 9.69
    2019-12-14 6.97 13
    2019-12-15 0.66 10.21
    


```python
import requests, json

cities = ['Istanbul','Ankara','Erzurum', 'Antalya', 'Tehran',
          'kars', 'toronto', 'helsinki', 'yakutsk', 'accra']

apikey = 'd9018602f134baf49774b75cc467706e'
baseurl = 'https://api.openweathermap.org/data/2.5/weather'

for city in cities:
    url = baseurl + '?appid=' + apikey + '&q=' + city + '&units=metric'

    res = requests.get(url)
    weather = json.loads(res.text)

    print(city, str(weather['main']['temp']) + '\u2103')
```

    Istanbul 13.72℃
    Ankara 8.75℃
    Erzurum 1℃
    Antalya 15℃
    Tehran 10.11℃
    kars 0.45℃
    toronto -1.58℃
    helsinki -4.01℃
    yakutsk -32℃
    accra 28℃
    

## Daytime 


```python
import requests, json
from time import localtime, strftime
```


```python
import time
```


```python
time.time()
```




    1575145769.216275




```python
time.strftime('%Y', localtime(1572533315) )
```




    '2019'




```python
print(localtime(1572533315))
```

    time.struct_time(tm_year=2019, tm_mon=10, tm_mday=31, tm_hour=17, tm_min=48, tm_sec=35, tm_wday=3, tm_yday=304, tm_isdst=0)
    


```python
time.strftime('%Y/%m/%d', localtime(1))
```




    '1970/01/01'




```python
time.strftime('%Y/%m/%d', localtime())
```




    '2019/11/30'




```python
time.strftime('%Y/%m/%d---%H:%M:%S', localtime())
```




    '2019/11/30---23:36:33'




```python
time.strftime('%Y/%B/%b/%d/---%H:%M:%S', localtime())
```




    '2019/November/Nov/30/30---23:39:10'


