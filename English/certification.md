# Certification

For security concerns, all requests of APIs except market APIs must run the signature algorithm. A legal request should include these parts:

*   Method request address It is the access server address followed by method name, such as api.ebx.kz/api_market/getBalance。
*   Required and optional parameters. There is a group of required and optional parameter which can be used to define API. These parameters and their meanings can be checked in the introduction of each method.
*   API_key: the api_key returned to you when you applied for api.
*   sign: used to verify that whether the parameters has been tampered by the third party.
