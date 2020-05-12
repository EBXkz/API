# 注意事项

*   如请求返回403状态码，请在header中设置User-Agent为：User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/39.0.2171.71 Safari/537.36。
*   文档中所有接口参数中出现的'symbol'，需使用交易对替换，symbol 规则： 基础币种+计价币种。如BTC/USDT，symbol为BTC_USDT。
*   文档中所提及的market与token，值分别为交易区、交易币种。如BTC/USDT，则market值为USDT，token值为BTC。
*   请求需page、size参数的接口，返回值中包含 count 字段，其值为符合条件的所有数据条目数，并不代表本次返回数据条目数。

