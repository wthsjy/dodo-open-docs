# 消息


## 消息内容

MessageBody


### 文字消息

#### 消息类型

1

#### 消息内容

MessageBodyText

|字段|类型|必传|说明|
|:---------------|:-----|:-----|:---------------|
|content|string|是|文字内容，限制10000个字符，频道文字消息支持多种 [消息语法](#消息语法)|


### 图片消息


#### 消息类型

2

#### 消息内容

MessageBodyPicture

|字段|类型|必传|说明|
|:---------------|:-----|:-----|:---------------|
|url|string|是|图片链接，必须是官方的链接，通过[上传资源图片](./resource.md#上传资源图片)接口可获得图片链接|
|width|int|是|图片宽度|
|height|int|是|图片高度|
|isOriginal|int|否|是否原图，0：压缩图，1：原图|


### 视频消息

#### 消息类型

3

#### 消息内容

MessageBodyVideo

|字段|类型|必传|说明|
|:---------------|:-----|:-----|:---------------|
|url|string|是|视频链接，必须是官方的链接，**后期会提供视频上传接口，前期可通过DoDo群内上传视频，从[消息事件](../event/channel-text.md#消息事件)内获得视频链接**|
|coverUrl|string|否|封面链接，必须是官方的链接，通过[上传资源图片](./resource.md#上传资源图片)接口可获得图片链接|
|duration|long|否|视频时长|
|size|long|否|视频大小|


### 分享消息

#### 消息类型

4

#### 消息内容

MessageBodyShare

|字段|类型|必传|说明|
|:---------------|:-----|:-----|:---------------|
|jumpUrl|string|是|跳转链接|


### 文件消息

#### 消息类型

5

#### 消息内容

MessageBodyFile

|字段|类型|必传|说明|
|:---------------|:-----|:-----|:---------------|
|url|string|是|文件链接|
|name|string|是|文件名称|
|size|long|是|文件大小|


<!-- ### 卡片消息

#### 消息类型

6

#### 消息内容

MessageBodyCard

|字段|类型|必传|说明|
|:---------------|:-----|:-----|:---------------|
|card|string|是|卡片数据，限制10000个字符，支持多种 [卡片结构](./card.md)| -->

## 消息模型

MessageModel

#### 个人信息

MessageModelPersonal

|字段|类型|说明|
|:---------------|:-----|:---------------|
|nickName|string|DoDo昵称|
|avatarUrl|string|头像|
|sex|int|性别，-1：保密，0：女，1：男|

#### 成员信息

MessageModelMember

|字段|类型|说明|
|:---------------|:-----|:---------------|
|nickName|string|群昵称|
|joinTime|string|加群时间|

#### 回复信息

ReferenceModelMember

|字段|类型|说明|
|:---------------|:-----|:---------------|
|messageId|string|被回复消息ID|
|dodoId|string|被回复者DoDo号|
|nickName|string|被回复者群昵称|

#### 反应对象

MessageModelReactionTarget

|字段|类型|说明|
|:---------------|:-----|:---------------|
|type|int|对象类型，0：消息|
|id|string|对象ID，若对象类型为0，则代表消息ID|


## 消息语法

机器人频道文字消息支持多种消息语法，具体语法内容如下

#### Markdon语法

|名称|语法|效果|
|:------|:---------------|:---------------|
|粗体|\*\*粗体\*\*|**粗体**|
|斜体|\*斜体\*|*斜体*|
|底线|\_\_底线\_\_|__底线__|
|链接|\[链接\]\(https://imdodo.com\)|[链接](https://imdodo.com)|
|删除线|\~\~删除线\~\~|~~删除线~~|
|防剧透|\|\|防剧透\|\||DoDo内发送可见|
|引用|\>引用|DoDo内发送可见|
|代码块|\`\`\`代码块\`\`\|DoDo内发送可见|


#### 菱形语法

|名称|语法|示例|效果|
|:------|:------|:---------------|:---------------|
|艾特用户|<@!DoDO号>|<@!666666>|DoDo内发送可见|
|跳转频道|<#频道ID>|<#1000101>|DoDo内发送可见|


## 消息表情

#### 表情内容

MessageModelEmoji

|字段|类型|说明|
|:---------------|:-----|:---------------|
|type|int|表情类型，1：[Emoji](#emoji)|
|id|string|表情ID|

#### Emoji

**Emoji的表情ID由表情的Unicode代码点生成，可以反向编码回去**

|表情|表情ID|对应Unicode码|
|:-------|:----------|:----------|
|	😄	|	128516	|	\uD83D\uDE04	|
|	😁	|	128513	|	\uD83D\uDE01	|
|	😆	|	128518	|	\uD83D\uDE06	|
|	😍	|	128525	|	\uD83D\uDE0D	|
|	😘	|	128536	|	\uD83D\uDE18	|
|	😅	|	128517	|	\uD83D\uDE05	|
|	🤣	|	129315	|	\uD83E\uDD23	|
|	😂	|	128514	|	\uD83D\uDE02	|
|	🙂	|	128578	|	\uD83D\uDE42	|
|	🙃	|	128579	|	\uD83D\uDE43	|
|	😉	|	128521	|	\uD83D\uDE09	|
|	😊	|	128522	|	\uD83D\uDE0A	|
|	😇	|	128519	|	\uD83D\uDE07	|
|	🤩	|	129321	|	\uD83E\uDD29	|
|	😚	|	128538	|	\uD83D\uDE1A	|
|	😜	|	128540	|	\uD83D\uDE1C	|
|	🤑	|	129297	|	\uD83E\uDD11	|
|	🤭	|	129325	|	\uD83E\uDD2D	|
|	🤫	|	129323	|	\uD83E\uDD2B	|
|	🤔	|	129300	|	\uD83E\uDD14	|
|	🤐	|	129296	|	\uD83E\uDD10	|
|	🤨	|	129320	|	\uD83E\uDD28	|
|	😑	|	128529	|	\uD83D\uDE11	|
|	😶	|	128566	|	\uD83D\uDE36	|
|	😏	|	128527	|	\uD83D\uDE0F	|
|	🙄	|	128580	|	\uD83D\uDE44	|
|	😬	|	128556	|	\uD83D\uDE2C	|
|	🤤	|	129316	|	\uD83E\uDD24	|
|	😴	|	128564	|	\uD83D\uDE34	|
|	😷	|	128567	|	\uD83D\uDE37	|
|	🤕	|	129301	|	\uD83E\uDD15	|
|	🤢	|	129314	|	\uD83E\uDD22	|
|	🤮	|	129326	|	\uD83E\uDD2E	|
|	🥵	|	129397	|	\uD83E\uDD75	|
|	🥶	|	129398	|	\uD83E\uDD76	|
|	😵	|	128565	|	\uD83D\uDE35	|
|	🥳	|	129395	|	\uD83E\uDD73	|
|	😎	|	128526	|	\uD83D\uDE0E	|
|	🧐	|	129488	|	\uD83E\uDDD0	|
|	☹️	|	9785	|	\u2639\uFE0F	|
|	😲	|	128562	|	\uD83D\uDE32	|
|	😳	|	128563	|	\uD83D\uDE33	|
|	🥺	|	129402	|	\uD83E\uDD7A	|
|	😧	|	128551	|	\uD83D\uDE27	|
|	😢	|	128546	|	\uD83D\uDE22	|
|	😭	|	128557	|	\uD83D\uDE2D	|
|	😱	|	128561	|	\uD83D\uDE31	|
|	😖	|	128534	|	\uD83D\uDE16	|
|	😓	|	128531	|	\uD83D\uDE13	|
|	😤	|	128548	|	\uD83D\uDE24	|
|	😡	|	128545	|	\uD83D\uDE21	|
|	🤬	|	129324	|	\uD83E\uDD2C	|
|	😈	|	128520	|	\uD83D\uDE08	|
|	💀	|	128128	|	\uD83D\uDC80	|
|	🤡	|	129313	|	\uD83E\uDD21	|
|	💯	|	128175	|	\uD83D\uDCAF	|
|	💋	|	128139	|	\uD83D\uDC8B	|
|	❤️	|	10084	|	\u2764\uFE0F	|
|	💔	|	128148	|	\uD83D\uDC94	|
|	👄	|	128068	|	\uD83D\uDC44	|
|	💩	|	128169	|	\uD83D\uDCA9	|
|	👀	|	128064	|	\uD83D\uDC40	|
|	🔒	|	128274	|	\uD83D\uDD12	|
|	💥	|	128165	|	\uD83D\uDCA5	|
|	💦	|	128166	|	\uD83D\uDCA6	|
|	💣	|	128163	|	\uD83D\uDCA3	|
|	🍭	|	127853	|	\uD83C\uDF6D	|
|	🍺	|	127866	|	\uD83C\uDF7A	|
|	🍻	|	127867	|	\uD83C\uDF7B	|
|	🙏	|	128591	|	\uD83D\uDE4F	|
|	💪	|	128170	|	\uD83D\uDCAA	|
|	👈	|	128072	|	\uD83D\uDC48	|
|	👉	|	128073	|	\uD83D\uDC49	|
|	☝	|	9757	|	\u261D\uFE0F	|
|	👆	|	128070	|	\uD83D\uDC46	|
|	👇	|	128071	|	\uD83D\uDC47	|
|	✌	|	9996	|	\u270C\uFE0F	|
|	✋	|	9995	|	\uD83E\uDD1A	|
|	👌	|	128076	|	\uD83D\uDC4C	|
|	👍	|	128077	|	\uD83D\uDC4D	|
|	👎	|	128078	|	\uD83D\uDC4E	|
|	✊	|	9994	|	\u270A	|
|	👊	|	128074	|	\uD83D\uDC4A	|
|	👏	|	128079	|	\uD83D\uDC4F	|
|	🚫	|	128683	|	\uD83D\uDEAB	|
|	🔞	|	128286	|	\uD83D\uDD1E	|
|	0️⃣	|	48	|	\u0030\uFE0F\u20E3	|
|	1️⃣	|	49	|	\u0031\uFE0F\u20E3	|
|	2️⃣	|	50	|	\u0032\uFE0F\u20E3	|
|	3️⃣	|	51	|	\u0033\uFE0F\u20E3	|
|	4️⃣	|	52	|	\u0034\uFE0F\u20E3	|
|	5️⃣	|	53	|	\u0035\uFE0F\u20E3	|
|	6️⃣	|	54	|	\u0036\uFE0F\u20E3	|
|	7️⃣	|	55	|	\u0037\uFE0F\u20E3	|
|	8️⃣	|	56	|	\u0038\uFE0F\u20E3	|
|	9️⃣	|	57	|	\u0039\uFE0F\u20E3	|
|	🆙	|	127385	|	\uD83C\uDD99	|
|	🆕	|	127381	|	\uD83C\uDD95	|
|	🈲	|	127538	|	\uD83C\uDE32	|
|	🉑	|	127569	|	\uD83C\uDE51	|
|	🌈	|	127752	|	\uD83C\uDF08	|
|	⬆️	|	11014	|	\u2B06\uFE0F	|
|	➡️	|	10145	|	\u27A1\uFE0F	|
|	⬇️	|	11015	|	\u2B07\uFE0F	|
|	⬅️	|	11013	|	\u2B05\uFE0F	|
|	⭕	|	11093	|	\u2B55\uFE0F	|
|	❌	|	10060	|	\u274C	|
|	✅	|	9989	|	\u2705	|
|	❎	|	10062	|	\u274E	|
|	⚠️	|	9888	|	\u26A0\uFE0F	|
|	🙈	|	128584	|	\uD83D\uDE48	|
|	🙉	|	128585	|	\uD83D\uDE49	|
|	🙊	|	128586	|	\uD83D\uDE4A	|
|	🧸	|	129528	|	\uD83E\uDDF8	|
|	🐶	|	128054	|	\uD83D\uDC36	|
|	😾	|	128574	|	\uD83D\uDE3E	|
|	🐴	|	128052	|	\uD83D\uDC34	|
|	🐮	|	128046	|	\uD83D\uDC2E	|
|	🐷	|	128055	|	\uD83D\uDC37	|
|	🐽	|	128061	|	\uD83D\uDC3D	|
|	🐾	|	128062	|	\uD83D\uDC3E	|
|	🐬	|	128044	|	\uD83D\uDC2C	|
|	🐟	|	128031	|	\uD83D\uDC1F	|
|	🐛	|	128027	|	\uD83D\uDC1B	|
|	🌙	|	127769	|	\uD83C\uDF19	|
|	⚡	|	9889	|	\u26A1\uFE0F	|
|	💥	|	128165	|	\uD83D\uDCA5	|
|	🏆	|	127942	|	\uD83C\uDFC6	|
|	🚑	|	128657	|	\uD83D\uDE91	|
|	🚀	|	128640	|	\uD83D\uDE80	|
|	🙅	|	128581	|	\uD83D\uDE45	|
|	🙆	|	128582	|	\uD83D\uDE46	|
|	🙋	|	128587	|	\uD83D\uDE4B	|
|	💊	|	128138	|	\uD83D\uDC8A	|
|	👅	|	128069	|	\uD83D\uDC45	|
|	👻	|	128123	|	\uD83D\uDC7B	|
|	🍌	|	127820	|	\uD83C\uDF4C	|
|	🌊	|	127754	|	\uD83C\uDF0A	|