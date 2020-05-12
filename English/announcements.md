# Announcements

*   If the request returns a 403 status code, set the User-Agent to: User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/39.0.2171.71 Safari/537.36 in the header
*   The 'symbol' that appears in all interface parameters in the document needs to be replaced with a transaction pair, symbol rule: Base currency + pricing currency. For example, BTC/USDT, symbol is BTC_USDT.
*   The market and token mentioned in the document are trading area and trading currency respectively. For example, BTC/USDT, the market value is USDT, and the token value is BTC.
*   When request for the interface which needs page’size, the return value has ‘count’ field. The value represents the number of eligible data, not the number of return value.

