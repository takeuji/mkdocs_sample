---
title: WMS
---

# OMS

## 連携仕様

### ■API仕様  
リクエスト  

| 項目 | 説明 |
| :------------- | :------------ |
| type | "authorization"：新規にアクセストークンを発行します。<br>"refresh"：refresh_tokenを元にアクセストークンを再発行します。|
| code | 認可要求で取得した認可コード。※type：refreshの場合は不要。|
| redirect_uri | コールバックURL。<br>https://XXXXXX/customer/receive/token |

レスポンス  
redirect_uriへのリダイレクト処理。

| 項目 | 説明 |
| :------------- | :------------ |
| access_token | アクセストークン。有効期限30日。|
| limit_time | 有効期限残り秒数。|
