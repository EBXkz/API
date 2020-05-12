# Error Code

## HTTP error request code

| Error code | meaning | discription |
| --- | --- | --- |
| 200 | succeed |  |
| 403 | invalid resource | header wrong information or incomplete |
| 404 | resources not found | url error |
| 405 | wrong method request | GET、POST replacement |
| 500 | server error | please contact customer service |

## interface feedback data code

| Error code | meaning | discription |
| --- | --- | --- |
| 0 | secceed |  |
| 1000 | insufficient parameter or wrong parameter type | please refer to the document parameter |
| 1200 | no legal api key was found | no api key in the request parameter |
| 1201 | authentification failed | signature authentication failed |
| 1206 | api interface missing parameter sign | no sign was found in the request parameter |
| 24001 | api data was not found | api_key error |
