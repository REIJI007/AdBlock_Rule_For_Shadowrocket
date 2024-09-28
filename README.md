[![GPL 3.0 license](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](https://github.com/REIJI007/AdBlock_Rule_For_Loon/blob/main/LICENSE-GPL3.0)
[![CC BY-NC-SA 4.0 license](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://github.com/REIJI007/AdBlock_Rule_For_Loon/blob/main/LICENSE-CC%20BY-NC-SA%204.0)
<!-- 居中的大标题 -->
<h1 align="center" style="font-size: 70px; margin-bottom: 20px;">AdBlock_Rule_For_Loon</h1>

<!-- 居中的副标题 -->
<h2 align="center" style="font-size: 30px; margin-bottom: 40px;">适用于Loon的广告域名拦截规则,每20分钟更新一次</h2>

<!-- 徽章（根据需要调整） -->
<p align="center" style="margin-bottom: 40px;">
    <img src="https://img.shields.io/badge/last%20commit-today-brightgreen" alt="last commit" style="margin-right: 10px;">
    <img src="https://img.shields.io/github/forks/REIJI007/AdBlock_Rule_For_Loon" alt="forks" style="margin-right: 10px;">
    <img src="https://img.shields.io/github/stars/REIJI007/AdBlock_Rule_For_Loon" alt="stars" style="margin-right: 10px;">
    <img src="https://img.shields.io/github/issues/REIJI007/AdBlock_Rule_For_Loon" alt="issues" style="margin-right: 10px;">
    <img src="https://img.shields.io/github/license/REIJI007/AdBlock_Rule_For_Loon" alt="license" style="margin-right: 10px;">
</p>

**一、从多个广告过滤器中提取拦截域名条目，删除重复项，并将它们转换为兼容loon的列表格式，其中列表的每一项都写成了Matcher Ruleset格式数组，一行仅一条规则。该列表可以用作loon的Matcher Ruleset列表以阻止广告域名， powershell脚本每20分钟自动执行并将生成的文件发布在release中,下面是九个规则集文件地址.**

<hr>
<table border="1" style="border-collapse: collapse; width: 100%;">
  <tr>
    <td>订阅地址:</td>
  </tr>
  <tr>
    <td>CONF</td>
    <td>
      <strong><a href="https://raw.githubusercontent.com/REIJI007/AdBlock_Rule_For_Loon/main/adblock_reject_loon.conf">原始链接</a></strong> | 
      <strong><a href="https://adblockproxy.miyajimareji007.workers.dev/loon_adblock.conf">Cloudflare加速链接</a></strong>
    </td>
  </tr>
  <tr>
    <td>TXT</td>
    <td>
      <strong><a href="https://raw.githubusercontent.com/REIJI007/AdBlock_Rule_For_Loon/main/adblock_reject_loon.txt">原始链接</a></strong> | 
      <strong><a href="https://adblockproxy.miyajimareji007.workers.dev/loon_adblock.txt">Cloudflare加速链接</a></strong>
    </td>
  </tr>
</table>

<hr>

## 警告:本过滤器订阅有可能破坏某些网站的功能，也有可能封禁某些色情、赌博网站，使用前请斟酌考虑，如有误杀请积极向上游issue反馈，本仓库仅提供去重、筛选、合并功能

<hr>

**二、理论上任何代理拦截域名且符合广告过滤器过滤语法的列表订阅URL都可加入此powershell脚本处理，请自行酌情添加过滤器订阅URL至adblock_rule_generator_loon.ps1脚本中进行处理，你可将该脚本代码复制到本地文本编辑器制作成.ps1后缀的文件运行在powershell上，注意修改生成文件的路径，最后在loon的配置中实现调用本地生成的规则集文件，[Rule]配置字段写成类似于如下例子**
<br>
<br>
*简而言之就是可以让你DIY出希望得到的拦截域名Matcher Ruleset列表，缺点是此做法只适合本地定制使用，当然你也可以像本仓库一样部署到GitHub上面，见仁见智*
<br>

**三、本仓库引用多个广告过滤器，从这些广告过滤器中提取了被拦截条目的域名，剔除了非拦截项并去重，最后做成rule_set规则集，虽无法做到面面俱到但能减少广告带来的困扰，请自行斟酌考虑使用。碍于Loon的路由行为且秉持着尽可能不误杀的原则，本仓库采取域名完全匹配策略，即匹配命中于拦截列表上的域名完全一致时触发拦截，除此之外的情况给予放行。尽管这会有许多漏网之鱼的广告被放行**
<br>
<br>

**四、关于本仓库使用方式：**

  *使用方式一：下载releases中的文件，修改loon配置中的[rule]字段作为拦截规则,可直接复制粘贴adblock_reject_loon.txt的内容（需要手动下载更新）*

  *使用方式二：将下面对应格式的配置文件中[Remote Rule]字段内容添加到你的配置文件充当远程规则集，需要特别注意配置文件的缩进和对齐（同步本仓库的云端部署的远程规则集配置)*
<hr>

```conf
# 适用于Loon的外部远程广告域名拦截规则
[Remote Rule]
https://raw.githubusercontent.com/REIJI007/AdBlock_Rule_For_Loon/main/adblock_reject_loon.conf, adblock, interval=120, policy=REJECT, auto=true, enabled=true
```

<hr>


  *使用方式三:下载规则集adblock_reject_loon.conf保存本地作为本地规则集，修改配置如下进行引用*


<hr>

```conf
# 适用于Loon的外部本地广告域名拦截规则
[Rule]
# 广告域名拦截规则文件路径
RULE-SET,/path/to/your/file.conf, REJECT
```
<hr>



**五、关于本仓库的使用效果为什么没有普通广告过滤器效果好的疑问解答：**
<br>
*因为普通的广告过滤器包含域名过滤（拦截广告域名）、路径过滤（例如拦截URL路径中包含/ads/的所有请求）、正则表达式过滤（例如拦截所有包含ads.js或ad.js的URL）、类型过滤（例如只拦截图片资源）、隐藏元素等等多因素作用下使得在广告拦截测试网站中可以取得高分。**但碍于loon的路由行为（可参考相关文档）**，本仓库仅提取了被拦截域名进行域名匹配过滤，换言之，本仓库就是一个“删减版”的广告过滤器（仅保留了域名匹配过滤功能，规则数在280万条左右），所以最终效果没有广告过滤器效果好*
<br>
<br>



**六、本仓库引用的广告过滤规则来源请查看```Referencing rule sources.txt```，后续考虑添加更多上游规则列表进行处理整合（目前446个来源）。至于是否误杀域名完全取决于这些处于上游的广告过滤器的域名拦截行为，若不满意的话可按照第二条使用adblock_rule_generator_loon.ps1脚本进行DIY本地定制化，亦或可以像本仓库一样DIY定制后部署到github上面，或者fork本仓库自行DIY**


**七、特别鸣谢**

<br>
1、loon
(https://nsloon.app/LoonManual/#/)<br>
2、anti-AD
(https://github.com/privacy-protection-tools/anti-AD)<br>
3、easylist
(https://github.com/easylist/easylist)<br>
4、oisd
(https://github.com/sjhgvr/oisd)<br>
5、cjxlist
(https://github.com/cjx82630/cjxlist)<br>
6、uniartisan
(https://github.com/uniartisan/adblock_list)<br>
7、Cats-Team
(https://github.com/Cats-Team/AdRules)<br>
8、217heidai
(https://github.com/217heidai/adblockfilters)<br>
9、GOODBYEADS
(https://github.com/8680/GOODBYEADS)<br>
10、AWAvenue-Ads-Rule
(https://github.com/TG-Twilight/AWAvenue-Ads-Rule)<br>
11、uBlockOrigin
(https://github.com/uBlockOrigin/uAssets)<br>
12、ADguardTeam
(https://github.com/AdguardTeam/AdGuardFilters)<br>
13、HyperADRules
(https://github.com/Lynricsy/HyperADRules)<br>
14、xinggsf
(https://github.com/xinggsf/Adblock-Plus-Rule)<br>
15、hoshsadiq
(https://github.com/hoshsadiq/adblock-nocoin-list)<br>
16、malware-filter
(https://gitlab.com/malware-filter)<br>
17、abp-filters
(https://gitlab.com/eyeo/anti-cv/abp-filters-anti-cv)<br>
18、banbendalao
(https://github.com/banbendalao/ADgk)<br>
19、yokoffing
(https://github.com/yokoffing/filterlists)<br>
20、Spam404
(https://github.com/Spam404/lists)<br>
21、brave
(https://github.com/brave/adblock-lists)<br>
22、Peter Lowe
(https://pgl.yoyo.org/adservers/)<br>
23、DandelionSprout
(https://github.com/DandelionSprout/adfilt)<br>
24、blocklistproject
(https://github.com/blocklistproject/Lists)<br>
25、reek
(https://github.com/reek/anti-adblock-killer)<br>
26、durablenapkin
(https://github.com/durablenapkin/scamblocklist)<br>
27、Perflyst
(https://github.com/Perflyst/PiHoleBlocklist)<br>
28、hagezi
(https://github.com/hagezi/dns-blocklists)<br>
29、neodevpro
(https://github.com/neodevpro/neodevhost)<br>
30、damengzhu
(https://github.com/damengzhu/banad)<br>
31、hectorm
(https://github.com/hectorm/hblock)<br>
32、badmojr
(https://github.com/badmojr/1Hosts)<br>
33、paulgb
(https://github.com/paulgb/BarbBlock)<br>
34、Adblocker
(https://adblockultimate.net/filters)<br>
35、RPiList
(https://github.com/RPiList/specials)<br>



## LICENSE
- [CC-BY-SA-4.0 License](https://github.com/REIJI007/AdBlock_Rule_For_Loon/blob/main/LICENSE-CC%20BY-NC-SA%204.0)
- [GPL-3.0 License](https://github.com/REIJI007/AdBlock_Rule_For_Loon/blob/main/LICENSE-GPL3.0)

