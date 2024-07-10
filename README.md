## 🌶PG节奏熊猫：接口

![photo_2024-05-29_20-53-25](https://github.com/alantang1977/pg/assets/107459091/7520d9d9-e4ba-472a-8a73-21fd5ad693e5)

![IMG_0113](https://github.com/alantang1977/pg/assets/107459091/a69f166c-07c8-4159-b442-bcf93983938c)

:star:把zip文件解壓縮到安卓設備的/sdcard/tvbox/JS/目錄<br>
複製lib/tokentemplate.json成爲lib/tokenm.json，并填寫必要的内容<br>
---
:name_badge:特別提示：發現影视壳并不能加载最新的jar，如果遇到jar表現異常，或者最新的jar承諾的功能改進沒有實現，請清除播放殼app的緩存后强杀播放壳后再試，清除方法1：在殼app的設置裏點擊“緩存”，清除方法2：設備的應用管理中，清除殼app的數據及緩存。<br>
:phone:特别警告：迅雷云盘限制极为严格，不要尝试单token多用户异地使用，或多线程使用，随时可能封号。<br> 
可以透过配置中的“網盤及彈幕配置”的視頻源來實現快捷方便的獲取32位token及opentoken的功能。在“網盤及彈幕配置”中掃過任何一個OpenToken后，會自動激活“轉存原畫”功能<br> 
---
:a:提示：如果遇到極速GO原畫反復快速報錯，不一定是被封號，可嘗試殺掉播放器重啓，或重啓整個播放設備解決。<br> 
:b:提示2：如果遇到“轉存原畫”速度被限制在2M左右，那麽請嘗試在阿里云盤APP裏退出登錄，然後重新登錄，然後刪除播放設備SD卡的TV目錄，在播放器上重新掃碼登錄。<br> 
:ab:提示3：zip包内預置的aliproxy從jar内的assets改爲zip内的aliproxy.gz，可以減少jar包對播放器内存的消耗，但因爲aliproxy.gz的釋出需要使用到殼上的proxy功能，所以如果播放設備安裝了多個類似的播放器，可能導致aliproxy釋放出錯或運行出錯。不要嘗試在同一個播放設備上運行多個播放殼，也不要嘗試把本jar加載到同一個播放設備的不同播放殼上。<br>
--- 
> tokenm.json格式説明：<br>
{<br>
"use_internal_storage":false, //如果播放設備（比如某些智能電視機）沒有SD卡讀寫權限，則把本項目設置爲true可以正常處理緩存<br>
"token":"這裏填寫阿里云盤的32位token，也可以不填寫，在播放阿里云盤内容時會彈出窗口，點擊QrCode，用阿里云盤app掃碼",<br>
"open_token":"這裏填寫通過alist或其他openapi提供方申請的280位aliyun openapi token，也可以不寫，會自動隱藏轉存原畫",<br>
"thread_limit":32, //這裏是阿里云盤的GO代理的并發協程數或java代理的并發綫程數，若遇到賬號被限制并發數，請將此數值改爲10<br>
"is_vip":true, //是否是阿里云盤的VIP用戶，設置為true后，使用vip_thread_limit設置的數值來并發加速。如本設置項目不是true，則自動隱藏“轉存原畫”<br>
"vip_thread_limit":10, //這裏是阿里云盤的轉存原畫(OpenToken)并發綫程數，若遇到賬號被限制并發數，請將此數值改爲10<br>
"quark_thread_limit":32, //這裏是夸克網盤GO代理的并發協程數或java代理的并發綫程數，若遇到賬號被限制並發數，請將此數值改爲10<br>
"quark_vip_thread_limit":16, //這裏是夸克網盤設置quark_is_vip:true之後的并發綫程數，若遇到賬號被限制并發數，請將此數值改爲10<br>
"quark_is_vip":false, //是否是夸克網盤的VIP用戶，設置為true后，綫程數受quark_vip_thread_limit控制<br>
"vod_flags":"4k|4kz|auto", //這裏是播放阿里雲的畫質選項，4k代表不轉存原畫（GO原畫），4kz代表轉存原畫,其他都代表預覽畫質,可選的預覽畫質包括qhd,fhd,hd,sd,ld，<br>
"quark_flags":"4kz|auto", //這裏是播放夸克網盤的畫質選項，4kz代表轉存原畫（GO原畫），其他都代表轉碼畫質,可選的預覽畫質包括4k,2k,super,high,low,normal<br>
"uc_thread_limit":0,<br>
"uc_is_vip":false,<br>
"uc_flags":"4kz|auto",<br>
"uc_vip_thread_limit":0,<br>
"thunder_thread_limit":0,<br>
"thunder_is_vip":false,<br>
"thunder_vip_thread_limit":0,<br>
"thunder_flags":"4k|4kz|auto",<br>
"aliproxy":"這裏填寫外部的加速代理，用於在盒子性能不夠的情況下，使用外部的加速代理來加速播放，可以不填寫",<br>
"proxy":"這裏填寫用於科學上網的地址，連接openapi或某些資源站可能會需要用到，可以不填寫",<br>
"open_api_url":"https://api.xhofe.top/alist/ali_open/token", //這是alist的openapi接口地址，也可使用其他openapi提供商的地址。<br>
"danmu":true,//是否全局開啓阿里云盤所有csp的彈幕支持，聚合類CSP仍需單獨設置，例如Wogg, Wobg<br>
"quark_danmu":true,//是否全局開啓夸克網盤的所有csp的彈幕支持, 聚合類CSP仍需單獨設置，例如Wogg, Wobg<br>
"quark_cookie":"這裏填寫通過https://pan.quark.cn網站獲取到的cookie，會很長，全數填入即可。"<br>
"uc_cookie":"這裏填寫通過https://drive.uc.cn網站登錄獲取的cookie",<br>
"thunder_username":"這裏填入用戶名或手機號，如果是手機號，記得是類似'+86 139123457'這樣的格式，+86后有空格才對",<br>
"thunder_password":"密碼",<br>
"thunder_captchatoken":"首次使用迅雷網盤時，需要使用app彈出的登陸地址去接碼登錄，並獲取captchaToken，具體方法參考alist網站的文檔:https://alist.nn.ci/zh/guide/drivers/thunder.html",<br>
"pikpak_username":"PikPak網盤的用戶名",<br>
"pikpak_password":"PikPak網盤的密碼",<br>
"pikpak_flags":"4k|auto",<br>
"pikpak_thread_limit":2,<br>
"pikpak_vip_thread_limit":2,<br>
"pikpak_proxy":"用於科學上網連接PikPak網盤的代理服務器地址",<br>
"pikpak_proxy_onlyapi":false<br>
}


![photo_2024-04-09_06-39-11](https://github.com/alantang1977/pg/assets/107459091/738ccf7a-9900-44f1-8bbc-2dfb8acff704)

[回到顶部](#readme)
