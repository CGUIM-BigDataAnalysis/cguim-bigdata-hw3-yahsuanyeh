長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
library(rvest) 
```

    ## Loading required package: xml2

``` r
PTT<-"https://www.ptt.cc/bbs/NBA/index.html"
PTT2<-"https://www.ptt.cc/bbs/NBA/index4627.html"
PTT3<-"https://www.ptt.cc/bbs/NBA/index4626.html"
PTT4<-"https://www.ptt.cc/bbs/NBA/index4625.html"
PTT5<-"https://www.ptt.cc/bbs/NBA/index4624.html"
PTT6<-"https://www.ptt.cc/bbs/NBA/index4623.html"
b <- c(PTT,PTT2,PTT3,PTT4,PTT5,PTT6)
frameALL <- NULL

for(n in b){
PTTContent<-read_html(n)
post_title <- PTTContent %>% html_nodes(".title") %>% html_text()
post_title
post_nrec <- PTTContent %>% html_nodes(".nrec") %>% html_text()
post_nrec
post_author <- PTTContent %>% html_nodes(".author") %>% html_text()
post_author


pppt <- data.frame(Title=c(post_title),
                   pushNum=c(post_nrec),
                   Author=c(post_author)
                   )
pppt
frameALL <- rbind(frameALL,pppt)
}
```

爬蟲結果呈現
------------

``` r
knitr::kable (
    frameALL[1:100,c("Title","pushNum","Author")]) 
```

| Title                                             | pushNum | Author       |
|:--------------------------------------------------|:--------|:-------------|
| \[討論\] Curry VS CP3 選誰?                       | 爆      | MrSatan      |
| Re: \[討論\] Rose是不是偷了Lebron的MVP啊          | 14      | FeiWenKing   |
| \[討論\] 勇迷會希望KD早早回歸嗎?                  | 11      | omare        |
| \[情報\] Dennis Smith Jr, Harry Giles 投入選秀會  | 23      | thnlkj0665   |
| \[討論\] 哪些球星算是自帶系統的球星？             | 45      | wmigrant     |
| \[公告\]昨日判罰疑問                              | 48      | namie810303  |
| Re: \[討論\] Curry VS CP3 選誰?                   | 28      | yokann       |
| Re: \[情報\] NBA Standings(2017.03.29)            | 3       | sasolala     |
| \[公告\]水桶                                      | 12      | namie810303  |
| \[花邊\] LeBron James是最難防守的球員? Jimmy Bu   | 2       | hector30618  |
| \[公告\] 板規6.1                                  |         | kadasaki     |
| \[公告\] 違規檢舉區                               | 爆      | kadasaki     |
| \[情報\] 2016-2017 例行賽 (3/27 - 4/3)            | 71      | gap6060      |
| \[公告\] 2017 板主選舉                            | 25      | kadasaki     |
| \[Live\] 勇士 @ 火箭                              | 96      | Rambo        |
| \[新聞\] 年度教練競爭激烈 柯爾力挺丹東尼          | 30      | pneumo       |
| \[討論\] 籃網RHJ這個球員......                    | 22      | ronharper    |
| \[BOX \] Bucks 118:108 Hornets 數據               | 37      | Rambo        |
| \[Live\] 金塊 @ 拓荒者                            | 44      | Rambo        |
| \[BOX \] Timberwolves 115:114 Pacers 數據         | 51      | Rambo        |
| \[BOX \] Sixers 106:101 Nets 數據                 | 91      | Rambo        |
| \[BOX \] Suns 91:95 Hawks 數據                    | 19      | Rambo        |
| \[新聞\] 上場時間決定MVP？　哈登：我從未缺席比    | 26      | zzyyxx77     |
| \[BOX \] Heat 97:96 Pistons 數據                  | 21      | Rambo        |
| \[Live\] 巫師 @ 湖人                              | 34      | Rambo        |
| \[新聞\] 林書豪關鍵走步失誤　籃網惜敗76人         | 29      | jhemezuo     |
| \[BOX \] Warriors 113:106 Rockets 數據            | 爆      | Rambo        |
| \[新聞\] 勇士「浪花兄弟」開轟　火箭哈登熄火吞敗   | 34      | zzzz8931     |
| \[討論\] 沒KD 勇士還是不可小看                    | 13      | feyako       |
| Re: \[討論\] 去年快艇如何守哈登買飯集錦           | 18      | bluestaral   |
| \[情報\] Kerr fastest coach in American sports    | 69      | Angel0724    |
| \[新聞\] 林書豪在場能量加倍 籃網輸球也精彩        | 1       | lcall        |
| \[討論\] 留KD或Curry？                            | 爆      | star1739456  |
| \[討論\] 穩進季後賽的火箭，仍然最多一輪           | X3      | sunnycello   |
| \[討論\]John Wall 算東區第一控了嗎？              | 99      | h1212123tw   |
| Re: \[情報\] 甜瓜：禁藥名單太長，我會選擇中草藥   | 2       | tadshift2    |
| (本文已被刪除) \[MrSatan\]                        | 1       | -            |
| \[新聞\] 好腰高難度空接　Manu：看不懂他怎麼傳     | 69      | zzzz8931     |
| \[新聞\] NBA／尼克將改變策略？ 何納塞克：下季將   | 28      | iam168888888 |
| \[新聞\] 馬刺大勝騎士 雷納德：沒有任何意義        | 59      | ccps970915   |
| \[情報\] 微笑刺客：若Rose最終去了馬刺不會讓我感   | 爆      | tmacor1      |
| Re: \[討論\] 之前有球隊刻意輸比賽 控制對手嗎      | 1       | BBDurant     |
| \[新聞\] 女性總教練？ 主席席佛：希望快點出現      | 44      | Gotham       |
| \[公告\]多人水桶                                  | 爆      | namie810303  |
| Re: \[討論\] NBA球員有拿過大滿貫的?               | 1       | Jachu        |
| \[情報\] 火箭差8顆三分打破單季三分進球數紀錄      | 38      | Wall62       |
| \[討論\] 球員綽號                                 | 20      | ZaneTrout    |
| Re: \[新聞\] 好腰高難度空接　Manu：看不懂他怎麼傳 | 15      | steveparker  |
| \[Live\] 公鹿 @ 黃蜂                              | 4       | Rambo        |
| \[Live\] 灰狼 @ 溜馬                              | 16      | Rambo        |
| \[Live\] 七六人 @ 籃網                            | 爆      | Rambo        |
| \[Live\] 太陽 @ 老鷹                              | 1       | Rambo        |
| \[Live\] 熱火 @ 活塞                              | 12      | Rambo        |
| (已被kadasaki刪除) <HANASUCIA> OP                 | X5      | -            |
| Re: \[討論\] 如果騎士在西區                       | X1      | Turtle100    |
| \[情報\] 甜瓜：禁藥名單太長，我會選擇中草藥       | 57      | Yui5         |
| Re: \[討論\] Lebron被大衛李尻背部受傷???          | 18      | iammatrix    |
| Re: \[情報\] NBA Standings(2017.03.28)            | 19      | cric335      |
| \[討論\] NBA球員有拿過大滿貫的?                   | 28      | chchang0820  |
| \[討論\] 東西勝場差～這些年的西強東弱             | 78      | liusim       |
| \[新聞\] 騎士近況低迷 詹姆斯：得找出解決方法      | 61      | adam7148     |
| \[專欄\] 死豬不怕開水燙 尼克丟臉已成習慣          | 19      | zzyyxx77     |
| Re: \[討論\] NBA球員有拿過大滿貫的?               | 19      | monmo        |
| \[情報\] Kobe：Booker有我想傳承給下一代球員的     | 50      | lovea        |
| (已被namie810303刪除) <OGC789456123>引戰          | X3      | -            |
| Re: \[討論\] 東西勝場差～這些年的西強東弱         | 25      | MK12         |
| (已被kadasaki刪除) <knic52976> 1-2                | X1      | -            |
| (本文已被刪除) \[goodbad\]                        | 15      | -            |
| \[新聞\] 隊友藥檢未 甜瓜：我都呷中藥顧健康        | 56      | royhsu425    |
| Re: \[討論\] NBA球員有拿過大滿貫的?               | 29      | Myosotis     |
| \[花邊\] Steve Francis, Joe Smith 加入BIG3聯賽    | 23      | thnlkj0665   |
| (本文已被刪除) \[hawoo\]                          |         | -            |
| \[花邊\] Kyrie Irving賽後獨自加練                 | 80      | KyrieIrving1 |
| \[情報\] 控衛防守哪家強？ “Wall”成聯盟第一        | 76      | tmac0818     |
| (已被namie810303刪除) <a102203028>引戰退          |         | -            |
| Re: \[討論\] 騎士東區第一的位置是不是不保了       | 4       | j5826497110  |
| \[討論\] 這場結束之後 是不是確定了西強東弱？      | 爆      | tiffanycute  |
| \[討論\] 騎士球隊CP值                             | 21      | t13thbc      |
| \[新聞\] 老大拒絕輪休 卻認為詹皇是例外            | 75      | pttpepe      |
| \[新聞\] 林書豪教得好 隊友會用中文說贏球          | 37      | Assisi       |
| \[討論\] 騎士是不是為了避開熱火或公牛？           | 17      | Max11        |
| \[新聞\] 球迷為搏版面出狠招 不惜拿兒子祭旗        | 14      | abc7360393   |
| \[新聞\] 騎士慘敗給馬刺　跌下東區龍頭寶座         | 26      | JAL96        |
| (本文已被刪除) <AsakuraYume>                      | 18      | -            |
| Re: \[新聞\] 老大拒絕輪休 卻認為詹皇是例外        | 1       | ICHIKOnice   |
| \[BOX \] Pelicans 100:108 Jazz 數據               | 25      | Rambo        |
| \[新聞\] 衛少第37次大三元 致勝一擊逆轉小牛        | 30      | MLbaseball   |
| \[BOX \] Grizzlies 90:91 Kings 數據               | 39      | hungys       |
| \[新聞\] 季中吞大補丸卻慘敗馬刺 詹皇寫一項最難    | 31      | dameontree   |
| \[討論\] 之前有球隊刻意輸比賽 控制對手嗎          | 22      | peace9527    |
| \[情報\] 詹姆斯：我想讓我們能打得更好些           | 32      | knic52976    |
| \[情報\] Kawhi Leonard連續100場得分雙位數         | 37      | jimmy5680    |
| \[討論\] Lebron被大衛李尻背部受傷???              | 99      | chouvincent  |
| Re: \[情報\] NBA Standings(2017.03.28)            | 爆      | kadasaki     |
| \[討論\] 騎馬大戰                                 | 2       | jojoii82     |
| \[Live\] 雷霆 @ 小牛                              | 74      | Rambo        |
| \[情報\] 東西區上週最佳球員：DeRozan, Harden      | 19      | Maxwell5566  |
| \[情報\] 國王有意撤換總管Vlade Divac              | 25      | dragon803    |
| \[花邊\] Duncan：每次在家看到馬刺贏球我都會罵人   | 爆      | Yui5         |
| \[情報\] 湖人Buss家族內鬥結束,Jeanie掌權          | 9       | sezna        |

解釋爬蟲結果
------------

``` r
dim(frameALL) 
```

    ## [1] 114   3

共爬出111篇標題與title，pushnum，author共3個欄位

``` r
table(frameALL$Author)
```

    ## 
    ##   FeiWenKing      gap6060  hector30618     kadasaki      MrSatan 
    ##            1            1            1            4            1 
    ##  namie810303        omare     sasolala   thnlkj0665     wmigrant 
    ##            3            1            1            2            1 
    ##       yokann    Angel0724   bluestaral       feyako     jhemezuo 
    ##            1            1            1            1            1 
    ##        lcall       pneumo        Rambo    ronharper  star1739456 
    ##            1            3           21            1            1 
    ##   sunnycello     zzyyxx77     zzzz8931            -     BBDurant 
    ##            1            2            2           10            1 
    ##   ccps970915       Gotham   h1212123tw iam168888888        Jachu 
    ##            1            1            1            1            1 
    ##  steveparker    tadshift2      tmacor1       Wall62    ZaneTrout 
    ##            1            1            1            1            1 
    ##     adam7148  chchang0820      cric335    iammatrix KyrieIrving1 
    ##            1            1            1            1            1 
    ##       liusim        lovea         MK12        monmo     Myosotis 
    ##            1            1            1            1            1 
    ##    royhsu425     tmac0818    Turtle100         Yui5   abc7360393 
    ##            1            1            2            2            1 
    ##       Assisi  chouvincent   dameontree       hungys   ICHIKOnice 
    ##            1            1            1            1            1 
    ##  j5826497110        JAL96    jimmy5680    knic52976        Max11 
    ##            1            1            1            1            1 
    ##   MLbaseball    peace9527      pttpepe      t13thbc  tiffanycute 
    ##            1            1            1            1            1 
    ##   bigDwinsch     CurryMvp    dragon803     jojoii82  kingrichman 
    ##            1            1            1            1            1 
    ##  Maxwell5566      meiyouo        sezna 
    ##            1            1            1

分析作者的出現次數

學會爬蟲之後發現，不知道為什麼，用貼六次網址，沒辦法爬出最新的6頁，想學怎樣可以正確爬出來~~
