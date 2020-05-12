# Sign

## Sign generation

Sort the parameters by ASCII code , transfer it into json, get signed by private key, do Base64 encoding and do url encoding. Take Asset balance check for example:

Request parameter：

```
page=1
size=10
api_key=eb4f25dd532c14cee5e9b0301c8d4671

```

Sort the parameters by ASCII code：

```
api_key=eb4f25dd532c14cee5e9b0301c8d4671
page=1
size=10

```

transfer it into json：

```
{"api_key":"eb4f25dd532c14cee5e9b0301c8d4671","page":"1","size":"10"}

```

Input private key, to generate sign by sha1 algorithm. Do Base64 encoding:

```
c6jVyjdQ+KX5oDZGDOr0phH0JZPCZ4lgxva7iwPr2J9cHsCVNhJEmnUzHIYIUlemzSreXzl8Xt39mkQYPaH/Tt8eLqZf8QlUPIigy3MlKzq/BTDzXkJc4vna9ltT42W6ePwNi9q3Otm6FK6gMhiXqWwwUwa7OciHjYYehEomzoo=

```

Note: private key was returned to you with api_key when you applied for API. The private key used here is:

```
-----BEGIN PRIVATE KEY-----
MIICdwIBADANBgkqhkiG9w0BAQEFAASCAmEwggJdAgEAAoGBALSQaafkE4wNY21T
+B2sCydP2FwkTQ6xi+bWLMVeF9bhFKyAZndmwxGgEc9bR6/rur5dAblka7OKpw3n
J27p3b5Ig/kd+dOSj4SfMp9pt96nHWud2KNZdAKUH4ybhg51D8TM0AXL474Gh8Cc
PrRvZspMdnlPM17YyUd6VjKQJs55AgMBAAECgYBF7mBdO8IuTckiQJEpvMYdFZlw
JkcJ182dO3nffs+w0z+Uh64ntE78dogvTOT4x01uCMtwJ+pmgN6uTcZB+KV+NEEC
7298kRZyclUZP4IDyc8qW95ljEHIJnDYwOzLop/IAY3PYwYT3ATJe8ceJ7nan32S
howHKNV+8abiD2yt4QJBANh/II1cF8wtSwVgUxaiKchZwz71GPIMxENRwF+Pgzpf
p61FIw8+If8sR1X036HgyY1+fmuakcqqjg68eF19SC0CQQDVgtOtx8BT9YtPEchv
dChqduHZi7f3IkrMuq7dzkZ9XI5QUdnAhnm8WiW8z8ruKUo32yyxJEWIUGOy6NLi
kqL9AkEAwGvVee7Vc/L5z/B6SQ6exmUJxUZBArnYIuFhc03x3Asy1C0z6RNXUh5/
1OVNcuqBGdLI+Eistg37LxvSe32jjQJAEWnPG9A7xl0zVGqN31Eo7q3tc5GqmlRI
p3PeSSbGpvjCfph+Wu5cxVjQ1RpZYZ0qeW29smDT7u8ngnLsqB/vfQJBAJwsJYVC
8V0D8waVTeDS0zgVcmKtjqHOtuJ3VuFivuSX0BZQALQIq5UlwUhIHwUKimEhffHc
84m43hIAVLHj7eM=
-----END PRIVATE KEY-----

```

Do URL encoding on the result of based64 :

```
c6jVyjdQ%2BKX5oDZGDOr0phH0JZPCZ4lgxva7iwPr2J9cHsCVNhJEmnUzHIYIUlemzSreXzl8Xt39mkQYPaH%2FTt8eLqZf8QlUPIigy3MlKzq%2FBTDzXkJc4vna9ltT42W6ePwNi9q3Otm6FK6gMhiXqWwwUwa7OciHjYYehEomzoo%3D

```

Finally, the API request parameter sent to the server is:

```
page=1
size=10
api_key=eb4f25dd532c14cee5e9b0301c8d4671
sign=c6jVyjdQ%2BKX5oDZGDOr0phH0JZPCZ4lgxva7iwPr2J9cHsCVNhJEmnUzHIYIUlemzSreXzl8Xt39mkQYPaH%2FTt8eLqZf8QlUPIigy3MlKzq%2FBTDzXkJc4vna9ltT42W6ePwNi9q3Otm6FK6gMhiXqWwwUwa7OciHjYYehEomzoo%3D

```

**sign generation example：**

```
<!—php code-->

    //request parameter
    $params = [
        'page' => '1',
        'size' => '10',
        'api_key' => 'eb4f25dd532c14cee5e9b0301c8d4671'
    ];

    //do ascending sort order for the associative array by ASCII code. 
    ksort($params);

    //Transfer to json formet
    $str = json_encode($params);

    //Input private key
    $key = file_get_contents('./private_key.pem');

    //parse private for other functions
    $private_key = openssl_pkey_get_private($key);

    //generate sign
    openssl_sign($str, $sign, $private_key, OPENSSL_ALGO_SHA1);

    //oppenssl private key from RAM
    openssl_free_key($private_key);

    //do base64 encode to the sign
    $sign = base64_encode($sign);

    //do url endode to the sign
    $sign = urlencode($sign);

    //add sign into the parameter array
    $params['sign'] = $sign;
<?php

```

```
#python code

# -*- coding: utf-8 -*-

    import base64
    import collections
    import json
    import requests
    from requests import Session

    #first need to install: pip install pyOpenSSL
    from OpenSSL import crypto

    try:
        import urllib.parse as _urlencode    # Python 3
    except ImportError:
        import urllib as _urlencode          # Python 2

    params = {
        'page' : '1',
        'size' : '10',
        'api_key' : 'eb4f25dd532c14cee5e9b0301c8d4671',
        }

    secret = '''-----BEGIN PRIVATE KEY-----
    MIICdwIBADANBgkqhkiG9w0BAQEFAASCAmEwggJdAgEAAoGBALSQaafkE4wNY21T+B2sCydP2FwkTQ6xi+bWLMVeF9bhFKyAZndmwxGgEc9bR6/rur5dAblka7OKpw3nJ27p3b5Ig/kd+dOSj4SfMp9pt96nHWud2KNZdAKUH4ybhg51D8TM0AXL474Gh8CcPrRvZspMdnlPM17YyUd6VjKQJs55AgMBAAECgYBF7mBdO8IuTckiQJEpvMYdFZlwJkcJ182dO3nffs+w0z+Uh64ntE78dogvTOT4x01uCMtwJ+pmgN6uTcZB+KV+NEEC7298kRZyclUZP4IDyc8qW95ljEHIJnDYwOzLop/IAY3PYwYT3ATJe8ceJ7nan32ShowHKNV+8abiD2yt4QJBANh/II1cF8wtSwVgUxaiKchZwz71GPIMxENRwF+Pgzpfp61FIw8+If8sR1X036HgyY1+fmuakcqqjg68eF19SC0CQQDVgtOtx8BT9YtPEchvdChqduHZi7f3IkrMuq7dzkZ9XI5QUdnAhnm8WiW8z8ruKUo32yyxJEWIUGOy6NLikqL9AkEAwGvVee7Vc/L5z/B6SQ6exmUJxUZBArnYIuFhc03x3Asy1C0z6RNXUh5/1OVNcuqBGdLI+Eistg37LxvSe32jjQJAEWnPG9A7xl0zVGqN31Eo7q3tc5GqmlRIp3PeSSbGpvjCfph+Wu5cxVjQ1RpZYZ0qeW29smDT7u8ngnLsqB/vfQJBAJwsJYVC8V0D8waVTeDS0zgVcmKtjqHOtuJ3VuFivuSX0BZQALQIq5UlwUhIHwUKimEhffHc84m43hIAVLHj7eM=
-----END PRIVATE KEY-----'''

    query = collections.OrderedDict(sorted(params.items(), key=lambda t: t[0]))
    json_str = json.dumps(query, separators=(',', ':'))
    key = crypto.load_privatekey(crypto.FILETYPE_PEM, secret)
    signature_base64 = base64.b64encode(crypto.sign(key, bytes(json_str, encoding = "utf8"), 'RSA-SHA1'))
    signature_str_tmp = str(signature_base64, encoding='utf-8')
    query['sign'] = _urlencode.quote(signature_str_tmp, safe="~()*!.'")
    body = json.dumps(query, separators=(',', ':'))
    print (body)
    print ()
    #{"api_key":"eb4f25dd532c14cee5e9b0301c8d4671","page":"1","size":"10","sign":"c6jVyjdQ%2BKX5oDZGDOr0phH0JZPCZ4lgxva7iwPr2J9cHsCVNhJEmnUzHIYIUlemzSreXzl8Xt39mkQYPaH%2FTt8eLqZf8QlUPIigy3MlKzq%2FBTDzXkJc4vna9ltT42W6ePwNi9q3Otm6FK6gMhiXqWwwUwa7OciHjYYehEomzoo%3D"}

    url = 'https://api.ebx.kz/api_market/getBalance'
    headers = {
        'Content-Type': 'application/json',
    }

    r = requests.post(url, headers=headers, data=body)

    print (r)
    #<Response [200]>

    print (r.text)
    #{"code":0,"msg":"\u64cd\u4f5c\u6210\u529f","data":{"count":5,"data":[{"user_id":352,"org_id":9,"token":"EOS","usable":"0","locked":"0","total":"0","token_as":"EOS"},{"user_id":352,"org_id":9,"token":"ETH","usable":"0","locked":"0","total":"0","token_as":"ETH"},{"user_id":352,"org_id":9,"token":"ONT","usable":"0","locked":"0","total":"0","token_as":"ONT"},{"user_id":352,"org_id":9,"token":"QTUM","usable":"0","locked":"0","total":"0","token_as":"QTUM"},{"user_id":352,"org_id":9,"token":"USDT","usable":"162449.02927762","locked":"2615.345","total":"165064.37427762","token_as":"USDT"}]}}

```

```
//NodeJs code
var http = require('http');
var fs = require('fs');
var crypto = require('crypto');
var urlencode = require('urlencode');
var qs = require('querystring');

const privateKey = fs.readFileSync('./private_key.pem').toString();

var params = {
    api_key:'eb4f25dd532c14cee5e9b0301c8d4671',
    page:'1',
    size:'10'
}

var options = {
    hostname: 'api.ebx.kz',
    path: '/api_market/getBalance',
    method: 'POST',
    headers: {
        'Content-Type':'application/json',
    }
};

var req = http.request(options, function (res) {
    console.log('STATUS: ' + res.statusCode);
    //console.log('HEADERS: ' + JSON.stringify(res.headers));
    res.setEncoding('utf8');
    res.on('data', function (chunk) {
        console.log('BODY: ' + chunk);
    });
});

req.on('error', function (e) {
    console.log('problem with request: ' + e.message);
});

req.write(qs.stringify(sign(params)));

req.end();

function sign(data) {
    data = objKeySort(data);
    var sign = crypto.createSign('sha1');
    sign.update(JSON.stringify(data));
    var sig = sign.sign(privateKey, 'base64');
    sigData =  urlencode(sig);
    data.sign = sigData;
    return data;
}

function objKeySort(arys) {
    var newkey = Object.keys(arys).sort();
    var newObj = {};
    for(var i = 0; i < newkey.length; i++) {
        newObj[newkey[i]] = arys[newkey[i]];
    }
    return newObj;
}

```
