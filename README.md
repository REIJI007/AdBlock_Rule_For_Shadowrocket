[![GPL 3.0 license](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](https://github.com/REIJI007/AdBlock_Rule_For_Clash/blob/main/LICENSE-GPL3.0)
[![CC BY-NC-SA 4.0 license](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://github.com/REIJI007/AdBlock_Rule_For_Clash/blob/main/LICENSE-CC%20BY-NC-SA%204.0)
<!-- 居中的大标题 -->
<h1 align="center" style="font-size: 70px; margin-bottom: 20px;">AdBlock_Rule_For_Shadowrocket</h1>

<!-- 居中的副标题 -->
<h2 align="center" style="font-size: 30px; margin-bottom: 40px;">一个适用于Shadowrocket的广告域名拦截规则集,每20分钟更新一次</h2>

<!-- 徽章（根据需要调整） -->
<p align="center" style="margin-bottom: 40px;">
    <img src="https://img.shields.io/badge/last%20commit-today-brightgreen" alt="last commit" style="margin-right: 10px;">
    <img src="https://img.shields.io/github/forks/REIJI007/AdBlock_Rule_For_Shadowrocket" alt="forks" style="margin-right: 10px;">
    <img src="https://img.shields.io/github/stars/REIJI007/AdBlock_Rule_For_Shadowrocket" alt="stars" style="margin-right: 10px;">
    <img src="https://img.shields.io/github/issues/REIJI007/AdBlock_Rule_For_Shadowrocket" alt="issues" style="margin-right: 10px;">
    <img src="https://img.shields.io/github/license/REIJI007/AdBlock_Rule_For_Shadowrocket" alt="license" style="margin-right: 10px;">
</p>

**一、从多个广告过滤器中提取拦截域名条目，删除重复项，并将它们转换为兼容Shadowrocket的列表格式，其中列表的每一项都写成了Matcher Ruleset格式数组，一行仅一条规则。该列表可以用作Shadowrocket的RULE-SET以阻止广告域名， powershell脚本每20分钟自动执行并将生成的文件发布在release中.**
<br>
*1、适用于Shadowrocket的外部远程域名CONF格式拦截RULE-SET规则集 adblock_reject_shadowrocket_ruleset.conf* 
<br>
*https://raw.githubusercontent.com/REIJI007/AdBlock_Rule_For_Shadowrocket/main/adblock_reject_shadowrocket_ruleset.conf*
<br>
*https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Shadowrocket@main/adblock_reject_shadowrocket_ruleset.conf*
<br>
<br>
*2、适用于Shadowrocket的外部远程域名LIST格式拦截RULE-SET规则集 adblock_reject_shadowrocket_ruleset.list* 
<br>
*https://raw.githubusercontent.com/REIJI007/AdBlock_Rule_For_Shadowrocket/main/adblock_reject_shadowrocket_ruleset.list*
<br>
*https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Shadowrocket@main/adblock_reject_shadowrocket_ruleset.list*
<br>
<br>
*3、适用于Shadowrocket的外部远程域名TXT格式拦截RULE-SET规则集 adblock_reject_shadowrocket_ruleset.txt* 
<br>
*https://raw.githubusercontent.com/REIJI007/AdBlock_Rule_For_Shadowrocket/main/adblock_reject_shadowrocket_ruleset.txt*
<br>
*https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Shadowrocket@main/adblock_reject_shadowrocket_ruleset.txt*
<br>
<br>
*4、适用于Shadowrocket的外部远程域名YAML格式拦截RULE-SET规则集 adblock_reject_shadowrocket_ruleset.yaml* 
<br>
*https://raw.githubusercontent.com/REIJI007/AdBlock_Rule_For_Shadowrocket/main/adblock_reject_shadowrocket_ruleset.yaml*
<br>
*https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Shadowrocket@main/adblock_reject_shadowrocket_ruleset.yaml*
<br>



**二、理论上任何代理拦截域名且符合广告过滤器过滤语法的列表订阅URL都可加入此powershell脚本处理，请自行酌情添加过滤器订阅URL至powershell脚本中进行处理，你可将该脚本代码复制到本地文本编辑器制作成.ps1后缀的文件运行在powershell上，注意修改生成的yaml文件路径，最后在surge的配置中实现调用本地生成的规则集文件，且shadowrocket的【rule】配置字段写成类似于如下例子**
<br>
<br>
*简而言之就是可以让你DIY出希望得到的拦截域名Matcher Ruleset列表，缺点是此做法只适合本地定制使用，当然你也可以像本仓库一样部署到GitHub上面，见仁见智*


```conf
#适用于Shadowrocket的外部本地拦截域名规则集
[Rule]
RULE-SET,C:\Users\YourUsername\Documents\file.conf,REJECT  #你的外部本地拦截域名conf规则集文件保存路径
```
```conf
#适用于Shadowrocket的外部本地拦截域名规则集
[Rule]
RULE-SET,C:\Users\YourUsername\Documents\file.list,REJECT  #你的外部本地拦截域名list格式规则集文件保存路径
```
```conf
#适用于Shadowrocket的外部本地拦截域名规则集
[Rule]
RULE-SET,C:\Users\YourUsername\Documents\file.txt,REJECT  #你的外部本地拦截域名txt格式规则集文件保存路径
```
```conf
#适用于Shadowrocket的外部本地拦截域名规则集
[Rule]
RULE-SET,C:\Users\YourUsername\Documents\file.yaml,REJECT  #你的外部本地拦截域名yaml格式规则集文件保存路径
```




**三、本仓库引用多个广告过滤器，从这些广告过滤器中提取了被拦截条目的域名，剔除了非拦截项并去重，最后做成Matcher Ruleset列表，虽无法做到面面俱到但能减少广告带来的困扰，请自行斟酌考虑使用。碍于surge的路由行为且秉持着尽可能不误杀的原则，本仓库采取域名完全匹配策略，即匹配命中于拦截列表上的域名完全一致时触发拦截，除此之外的情况给予放行。尽管这会有许多漏网之鱼的广告被放行**
<br>
<br>

**四、关于本仓库使用方式：**

  *使用方式一：下载releases中的adblock_reject_surge_ruleset.txt文件或者adblock_reject_surge_domainset.txt，里面的内容可直接粘贴到Surge的配置中的[rules]字段下作为拦截规则（需要手动下载更新）*



  *使用方式二：将下面对应格式的配置文件中[rule]字段内容添加到你的配置文件充当远程规则集，需要特别注意配置文件的缩进和对齐（同步本仓库的云端部署的远程规则集配置)*

```conf
#适用于Shadowrocket的conf格式RULE-SET
[Rule]
RULE-SET,https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Shadowrocket@main/adblock_reject_shadowrocket_ruleset.conf,REJECT
```
```conf
#适用于Shadowrocket的list格式RULE-SET
[Rule]
RULE-SET,https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Shadowrocket@main/adblock_reject_shadowrocket_ruleset.list,REJECT
```
```conf
#适用于Shadowrocket的txt格式RULE-SET
[Rule]
RULE-SET,https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Shadowrocket@main/adblock_reject_shadowrocket_ruleset.txt,REJECT
```
```conf
#适用于Shadowrocket的yaml格式RULE-SET
[Rule]
RULE-SET,https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Shadowrocket@main/adblock_reject_shadowrocket_ruleset.yaml,REJECT
```



**五、关于本仓库的使用效果为什么没有普通广告过滤器效果好的疑问解答：**
<br>
*因为普通的广告过滤器包含域名过滤（拦截广告域名）、路径过滤（例如拦截URL路径中包含/ads/的所有请求）、正则表达式过滤（例如拦截所有包含ads.js或ad.js的URL）、类型过滤（例如只拦截图片资源）、隐藏元素等等多因素作用下使得在广告拦截测试网站中可以取得高分。**但碍于shadowrocket的路由行为（可分别参考相关文档）**，本仓库仅提取了被拦截域名进行域名完全匹配过滤，换言之，本仓库就是一个“删减版”的广告过滤器（仅保留了域名完全匹配过滤功能，规则数在70万条左右），所以最终效果没有广告过滤器效果好*




**六、本仓库引用的广告过滤规则来源请查看Referencing rule sources.txt，后续考虑添加更多上游规则列表进行处理整合（目前33个来源）。至于是否误杀域名完全取决于这些处于上游的广告过滤器的域名拦截行为，若不满意的话可按照第二条在本地脚本进行DIY本地定制化，亦或可以像本仓库一样DIY定制后部署到github上面，或者fork本仓库自行DIY**


**七、特别鸣谢**

1、anti-AD (https://github.com/privacy-protection-tools/anti-AD)

2、easylist (https://github.com/easylist/easylist)

3、cjxlist (https://github.com/cjx82630/cjxlist)

4、uniartisan (https://github.com/uniartisan/adblock_list)

5、Cats-Team (https://github.com/Cats-Team/AdRules)

6、217heidai (https://github.com/217heidai/adblockfilters)

7、GOODBYEADS (https://github.com/8680/GOODBYEADS)

8、AWAvenue-Ads-Rule (https://github.com/TG-Twilight/AWAvenue-Ads-Rule)

9、Bibaiji (https://github.com/Bibaiji/ad-rules/)

10、uBlockOrigin (https://github.com/uBlockOrigin/uAssets)

11、ADguardTeam (https://github.com/AdguardTeam/AdGuardFilters)

12、HyperADRules (https://github.com/Lynricsy/HyperADRules)

13、guandasheng (https://github.com/guandasheng/TheBestAdrules)

## License

GNU GENERAL PUBLIC LICENSE Version 3

Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)


