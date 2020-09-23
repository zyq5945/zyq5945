通过对估计康复率数值的分析，来发现了COVID-19康复情况的规律
==================================================================

这里我们先定义三个数值计算方式：

估计康复率：康复数除以康复数与死亡数之和，该数值越高表明康复情况就越好

估计死亡率：死亡数除以康复数与死亡数之和，该数值越高表明康复情况就越差

估计置信度：康复数与死亡数之和除以确诊病例数，该数值表明上述两个数值的可信任程度，该数值越高表明这两个数值越接近真实值，并最终等于真实值


估计康复率不会受到短期确诊激增案例数影响，只会跟踪在经过一段时间的治疗后确诊患者要么死亡，要么康复，才会反映到该数值。在排除数据较少该数值数据波动大和在大数据的情况下，比如大于100的康复数或者死亡数的情况下，这个数值会比现在的康复率或者死亡率计算方式，能更快更早反映疾病的治疗情况。根据中国疫情的经验，在大数据的情况下，这个数值中期会处于低值，然后随着患者的减少，该数值会逐渐增大。

在大数据的情况下，分析这三个数值我们就会发现，该数值与天气温度有很大关联，天气温度较高且适宜（温度不能太高，温度太高人容易中暑），则康复情况较好，我们就会发现许多非洲大陆国家的情况甚至可能比美国要好。

比如我们以6月1日为分界，单单看美国死亡增长数据，也能得出在这之前的死亡情况要比这之后的要坏很多，使用上述数值计算方式对美国整体，各州和各地区的分段数据进行分析，也能得出同样的结果，这里还能发现疾病的另一个特征表现，在这之前的疾病病症较容易出现重症患者，而且表现病症都比较严重，之后容易出现轻症患者，甚至比之前更多的无症患者，症状的表现轻重程度，这也在某种程度上反应出患者身体免疫系统能力的高低。

以6月1日为分界对季节处于相反状况的澳大利亚的大数据进行分析，却得出了康复情况有些变糟糕的情况，这和全球趋势变好走了截然不同的道路。

当然假如能得到地区详细疫情情况，在大数据情况下，并分开统计在不同天气温度情况下，不同年龄段患者的康复时长与死亡时长，也可以得出同样的结果。


天气温度影响COVID-19疾病的情况，同样的现象甚至在SARS疾病表现更加得明显，假如我们针对其他很多疾病也做类似分析，也能得出同样的结果：在天气温度较高且适宜的情况康复情况好，在寒冷天气情况下康复情况差。

个人认为造成这些原因的是：天气温度会影响人体体温，人体体温和身体免疫系统能力有很大关联关系，天气温度对疾病数据的影响有一定的滞后性，人体对环境温度的舒适程度反应就表明了，我们的生活对环境温度是有明确且程度不同的生物需求。

我们以天气温度的角度分析COVID-19的数据的时候，会发现一些有意思的特例，比如新加坡的康复情况很好，这个可以解释为天气温度较好和患者年龄平均年龄普遍不高。但是冰岛作为一个疫情发生时的寒冷国家，不符合上述所说的天气温度规律，也取得了一个很好的成绩，假如冰岛的数据没有错误，我们或许能从冰岛找到针对疫情进行处理的好办法。


下面是针对2020年9月21日的[CSSEGISandData的COVID19](https://github.com/CSSEGISandData/COVID-19.git)数据分析：

表格字段说明：

| 名称            | 说明                         | 值                                                                                         |
|---------------|----------------------------|-------------------------------------------------------------------------------------------|
| 0530Confirmed | 2020年5月30日确诊数              |                                                                                           |
| 0530Deaths    | 2020年5月30日死亡数              |                                                                                           |
| 0530Recovered | 2020年5月30日康复数              |                                                                                           |
| Before\-EC    | 2020年5月30日的估计置信度           | =\(0530Deaths\+0530Recovered\)/0530Confirmed                                              |
| Before\-EDR   | 2020年5月30日的估计死亡率           | =0530Deaths/\(0530Deaths\+0530Recovered\)                                                 |
| Before\-ERR   | 2020年5月30日的估计康复率           | =0530Recovered/\(0530Deaths\+0530Recovered\)                                              |
| 0921Confirmed | 2020年9月21日确诊数              |                                                                                           |
| 0921Deaths    | 2020年9月21日死亡数              |                                                                                           |
| 0921Recovered | 2020年9月21日康复数              |                                                                                           |
| After\-EC     | 2020年6月1日至2020年9月21日的估计置信度 | =\(0921Confirmed\-0921Deaths\-0921Recovered\)/\(0921Confirmed\-0530Deaths\-0530Recovered） |
| After\-EDR    | 2020年6月1日至2020年9月21日的估计死亡率 | =\(0921Deaths\-0530Deaths\)/\(0921Deaths\+0921Recovered\-0530Deaths\-0530Recovered）       |
| After\-ERR    | 2020年6月1日至2020年9月21日的估计康复率 | =\(0921Recovered\-0530Recovered\)/\(0921Deaths\+0921Recovered\-0530Deaths\-0530Recovered） |
| ERR\-Changed  | 估计康复率提升率                   | 之后的估计康复率减去之前的估计康复率                                                                        |

注：最好针对After-EC和Before-EC都较高且是大数据的地区进行分析，尤其针对那些Before-EC小于20%的数据进行分析的价值不大，有的数据肯定是有误的，这个也需要考虑。

下面是国家确诊数超过1000，按After-EC从高往低排序情况：

| Name                   | 0530Confirmed | 0530Deaths | 0530Recovered | Before\-EC | Before\-EDR | Before\-ERR | 0921Confirmed | 0921Deaths | 0921Recovered | After\-EC | After\-EDR | After\-ERR | ERR\-Changed |
|------------------------|---------------|------------|---------------|------------|-------------|-------------|---------------|------------|---------------|-----------|------------|------------|--------------|
| Djibouti               | 3194          | 22         | 1286          | 40\.95%    | 1\.68%      | 98\.32%     | 5404          | 61         | 5336          | 99\.83%   | 0\.95%     | 99\.05%    | 0\.73%       |
| Singapore              | 34366         | 23         | 20727         | 60\.38%    | 0\.11%      | 99\.89%     | 57606         | 27         | 57241         | 99\.08%   | 0\.01%     | 99\.99%    | 0\.10%       |
| Ghana                  | 7768          | 35         | 2540          | 33\.15%    | 1\.36%      | 98\.64%     | 46062         | 297        | 45258         | 98\.83%   | 0\.61%     | 99\.39%    | 0\.75%       |
| Zambia                 | 1057          | 7          | 779           | 74\.36%    | 0\.89%      | 99\.11%     | 14175         | 331        | 13629         | 98\.39%   | 2\.46%     | 97\.54%    | \-1\.57%     |
| Pakistan               | 66457         | 1395       | 24131         | 38\.41%    | 5\.47%      | 94\.53%     | 306886        | 6424       | 293159        | 97\.40%   | 1\.84%     | 98\.16%    | 3\.63%       |
| Qatar                  | 55262         | 36         | 25839         | 46\.82%    | 0\.14%      | 99\.86%     | 123604        | 211        | 120540        | 97\.08%   | 0\.18%     | 99\.82%    | \-0\.05%     |
| Congo \(Kinshasa\)     | 2966          | 69         | 428           | 16\.76%    | 13\.88%     | 86\.12%     | 10519         | 271        | 9952          | 97\.05%   | 2\.08%     | 97\.92%    | 11\.81%      |
| Belarus                | 41658         | 229        | 17964         | 43\.67%    | 1\.26%      | 98\.74%     | 75898         | 785        | 73301         | 96\.86%   | 0\.99%     | 99\.01%    | 0\.26%       |
| Cote d'Ivoire          | 2799          | 33         | 1385          | 50\.66%    | 2\.33%      | 97\.67%     | 19327         | 120        | 18630         | 96\.78%   | 0\.50%     | 99\.50%    | 1\.83%       |
| Chile                  | 94858         | 997        | 40431         | 43\.67%    | 2\.41%      | 97\.59%     | 447468        | 12298      | 421111        | 96\.54%   | 2\.88%     | 97\.12%    | \-0\.48%     |
| Kazakhstan             | 10382         | 38         | 5220          | 50\.65%    | 0\.72%      | 99\.28%     | 107374        | 1671       | 102064        | 96\.44%   | 1\.66%     | 98\.34%    | \-0\.94%     |
| Mexico                 | 14334         | 1148       | 11213         | 86\.24%    | 9\.29%      | 90\.71%     | 77232         | 8964       | 65162         | 95\.21%   | 12\.65%    | 87\.35%    | \-3\.37%     |
| Azerbaijan             | 5246          | 61         | 3327          | 64\.58%    | 1\.80%      | 98\.20%     | 39280         | 576        | 36836         | 94\.80%   | 1\.51%     | 98\.49%    | 0\.29%       |
| Saudi Arabia           | 83384         | 480        | 58883         | 71\.19%    | 0\.81%      | 99\.19%     | 330246        | 4512       | 311499        | 94\.74%   | 1\.57%     | 98\.43%    | \-0\.76%     |
| China                  | 84128         | 4638       | 79386         | 99\.88%    | 5\.52%      | 94\.48%     | 90381         | 4737       | 85257         | 93\.91%   | 1\.66%     | 98\.34%    | 3\.86%       |
| Kyrgyzstan             | 1722          | 16         | 1113          | 65\.56%    | 1\.42%      | 98\.58%     | 45471         | 1063       | 41682         | 93\.85%   | 2\.52%     | 97\.48%    | \-1\.10%     |
| Cameroon               | 5904          | 191        | 3568          | 63\.67%    | 5\.08%      | 94\.92%     | 20598         | 416        | 19124         | 93\.72%   | 1\.43%     | 98\.57%    | 3\.66%       |
| Guinea                 | 3706          | 23         | 2030          | 55\.40%    | 1\.12%      | 98\.88%     | 10344         | 65         | 9757          | 93\.70%   | 0\.54%     | 99\.46%    | 0\.58%       |
| Egypt                  | 23449         | 913        | 5693          | 28\.17%    | 13\.82%     | 86\.18%     | 102141        | 5787       | 90332         | 93\.70%   | 5\.45%     | 94\.55%    | 8\.38%       |
| Uzbekistan             | 3546          | 14         | 2783          | 78\.88%    | 0\.50%      | 99\.50%     | 52070         | 437        | 48369         | 93\.38%   | 0\.92%     | 99\.08%    | \-0\.42%     |
| Sri Lanka              | 1620          | 10         | 781           | 48\.83%    | 1\.26%      | 98\.74%     | 3299          | 13         | 3100          | 92\.58%   | 0\.13%     | 99\.87%    | 1\.14%       |
| Oman                   | 10423         | 42         | 2396          | 23\.39%    | 1\.72%      | 98\.28%     | 94051         | 853        | 85781         | 91\.90%   | 0\.96%     | 99\.04%    | 0\.76%       |
| South Africa           | 30967         | 643        | 16116         | 54\.12%    | 3\.84%      | 96\.16%     | 661936        | 15992      | 591208        | 91\.52%   | 2\.60%     | 97\.40%    | 1\.24%       |
| Equatorial Guinea      | 1306          | 12         | 200           | 16\.23%    | 5\.66%      | 94\.34%     | 5002          | 83         | 4509          | 91\.44%   | 1\.62%     | 98\.38%    | 4\.04%       |
| Guatemala              | 4739          | 102        | 706           | 17\.05%    | 12\.62%     | 87\.38%     | 85681         | 3124       | 75172         | 91\.30%   | 3\.90%     | 96\.10%    | 8\.72%       |
| Armenia                | 8927          | 127        | 3317          | 38\.58%    | 3\.69%      | 96\.31%     | 47552         | 936        | 42637         | 90\.98%   | 2\.02%     | 97\.98%    | 1\.67%       |
| Kuwait                 | 26192         | 205        | 10156         | 39\.56%    | 1\.98%      | 98\.02%     | 99964         | 585        | 90930         | 90\.57%   | 0\.47%     | 99\.53%    | 1\.51%       |
| Australia              | 7192          | 103        | 6614          | 93\.40%    | 1\.53%      | 98\.47%     | 26942         | 854        | 24155         | 90\.44%   | 4\.11%     | 95\.89%    | \-2\.57%     |
| Gabon                  | 2655          | 17         | 722           | 27\.83%    | 2\.30%      | 97\.70%     | 8704          | 54         | 7875          | 90\.27%   | 0\.51%     | 99\.49%    | 1\.79%       |
| Brazil                 | 498440        | 28834      | 200892        | 46\.09%    | 12\.55%     | 87\.45%     | 4558040       | 137272     | 3993432       | 90\.13%   | 2\.78%     | 97\.22%    | 9\.77%       |
| Japan                  | 16716         | 894        | 14267         | 90\.70%    | 5\.90%      | 94\.10%     | 79462         | 1518       | 70970         | 89\.15%   | 1\.09%     | 98\.91%    | 4\.81%       |
| Bahrain                | 10793         | 17         | 5826          | 54\.14%    | 0\.29%      | 99\.71%     | 65752         | 224        | 58626         | 88\.48%   | 0\.39%     | 99\.61%    | \-0\.10%     |
| Canada                 | 91681         | 7159       | 48517         | 60\.73%    | 12\.86%     | 87\.14%     | 147583        | 9279       | 127684        | 88\.44%   | 2\.61%     | 97\.39%    | 10\.25%      |
| Ecuador                | 38571         | 3334       | 19190         | 58\.40%    | 14\.80%     | 85\.20%     | 126711        | 11095      | 102852        | 87\.75%   | 8\.49%     | 91\.51%    | 6\.31%       |
| Iran                   | 148950        | 7734       | 116827        | 83\.63%    | 6\.21%      | 93\.79%     | 425481        | 24478      | 361523        | 86\.88%   | 6\.40%     | 93\.60%    | \-0\.20%     |
| Afghanistan            | 14525         | 249        | 1303          | 10\.69%    | 16\.04%     | 83\.96%     | 39074         | 1444       | 32576         | 86\.53%   | 3\.68%     | 96\.32%    | 12\.36%      |
| Colombia               | 26734         | 891        | 6935          | 29\.27%    | 11\.39%     | 88\.61%     | 770435        | 24397      | 640900        | 86\.21%   | 3\.58%     | 96\.42%    | 7\.81%       |
| North Macedonia        | 2164          | 131        | 1535          | 76\.99%    | 7\.86%      | 92\.14%     | 16780         | 700        | 13949         | 85\.90%   | 4\.38%     | 95\.62%    | 3\.48%       |
| Nigeria                | 9855          | 273        | 2856          | 31\.75%    | 8\.72%      | 91\.28%     | 57437         | 1100       | 48674         | 85\.89%   | 1\.77%     | 98\.23%    | 6\.95%       |
| Maldives               | 1672          | 5          | 406           | 24\.58%    | 1\.22%      | 98\.78%     | 9770          | 34         | 8390          | 85\.62%   | 0\.36%     | 99\.64%    | 0\.85%       |
| United Arab Emirates   | 33896         | 262        | 17546         | 52\.54%    | 1\.47%      | 98\.53%     | 85595         | 405        | 75086         | 85\.09%   | 0\.25%     | 99\.75%    | 1\.22%       |
| Venezuela              | 1459          | 14         | 302           | 21\.66%    | 4\.43%      | 95\.57%     | 67443         | 555        | 56726         | 84\.86%   | 0\.95%     | 99\.05%    | 3\.48%       |
| Tajikistan             | 3807          | 47         | 1865          | 50\.22%    | 2\.46%      | 97\.54%     | 9388          | 73         | 8152          | 84\.44%   | 0\.41%     | 99\.59%    | 2\.05%       |
| Croatia                | 2246          | 103        | 2063          | 96\.44%    | 4\.76%      | 95\.24%     | 14992         | 253        | 12737         | 84\.39%   | 1\.39%     | 98\.61%    | 3\.37%       |
| Somalia                | 1916          | 73         | 327           | 20\.88%    | 18\.25%     | 81\.75%     | 3465          | 98         | 2877          | 84\.01%   | 0\.97%     | 99\.03%    | 17\.28%      |
| Turkey                 | 163103        | 4515       | 126984        | 80\.62%    | 3\.43%      | 96\.57%     | 304610        | 7574       | 268435        | 83\.48%   | 2\.12%     | 97\.88%    | 1\.32%       |
| Cuba                   | 2025          | 83         | 1795          | 92\.74%    | 4\.42%      | 95\.58%     | 5141          | 116        | 4462          | 82\.75%   | 1\.22%     | 98\.78%    | 3\.20%       |
| Morocco                | 7780          | 204        | 5401          | 72\.04%    | 3\.64%      | 96\.36%     | 103119        | 1855       | 84158         | 82\.46%   | 2\.05%     | 97\.95%    | 1\.59%       |
| Iraq                   | 6179          | 195        | 3110          | 53\.49%    | 5\.90%      | 94\.10%     | 322856        | 8625       | 258075        | 82\.43%   | 3\.20%     | 96\.80%    | 2\.70%       |
| Korea, South           | 11468         | 270        | 10405         | 93\.09%    | 2\.53%      | 97\.47%     | 23106         | 388        | 20441         | 81\.68%   | 1\.16%     | 98\.84%    | 1\.37%       |
| Peru                   | 155671        | 4371       | 66447         | 45\.49%    | 6\.17%      | 93\.83%     | 768895        | 31369      | 607837        | 81\.42%   | 4\.75%     | 95\.25%    | 1\.42%       |
| India                  | 181827        | 5185       | 86936         | 50\.66%    | 5\.63%      | 94\.37%     | 5487580       | 87882      | 4396399       | 81\.40%   | 1\.88%     | 98\.12%    | 3\.75%       |
| Argentina              | 16214         | 528        | 4788          | 32\.79%    | 9\.93%      | 90\.07%     | 640147        | 13482      | 508563        | 81\.40%   | 2\.51%     | 97\.49%    | 7\.43%       |
| Romania                | 19133         | 1259       | 13046         | 74\.77%    | 8\.80%      | 91\.20%     | 113589        | 4458       | 90649         | 81\.38%   | 3\.96%     | 96\.04%    | 4\.84%       |
| Russia                 | 396575        | 4555       | 167469        | 43\.38%    | 2\.65%      | 97\.35%     | 1105048       | 19420      | 909026        | 81\.07%   | 1\.97%     | 98\.03%    | 0\.68%       |
| Philippines            | 17224         | 950        | 3808          | 27\.62%    | 19\.97%     | 80\.03%     | 290190        | 4999       | 230233        | 80\.75%   | 1\.76%     | 98\.24%    | 18\.21%      |
| Poland                 | 23571         | 1061       | 11016         | 51\.24%    | 8\.79%      | 91\.21%     | 79988         | 2298       | 64604         | 80\.73%   | 2\.26%     | 97\.74%    | 6\.53%       |
| El Salvador            | 2395          | 46         | 1031          | 44\.97%    | 4\.27%      | 95\.73%     | 27798         | 812        | 21782         | 80\.52%   | 3\.56%     | 96\.44%    | 0\.71%       |
| New Zealand            | 1504          | 22         | 1481          | 99\.93%    | 1\.46%      | 98\.54%     | 1815          | 25         | 1729          | 80\.45%   | 1\.20%     | 98\.80%    | 0\.27%       |
| Malaysia               | 7762          | 115        | 6330          | 83\.03%    | 1\.78%      | 98\.22%     | 10276         | 130        | 9395          | 80\.40%   | 0\.49%     | 99\.51%    | 1\.30%       |
| Thailand               | 3077          | 57         | 2961          | 98\.08%    | 1\.89%      | 98\.11%     | 3511          | 59         | 3343          | 77\.89%   | 0\.52%     | 99\.48%    | 1\.37%       |
| Haiti                  | 1865          | 41         | 24            | 3\.49%     | 63\.08%     | 36\.92%     | 8624          | 221        | 6482          | 77\.56%   | 2\.71%     | 97\.29%    | 60\.37%      |
| Panama                 | 13018         | 330        | 9414          | 74\.85%    | 3\.39%      | 96\.61%     | 106810        | 2272       | 82320         | 77\.11%   | 2\.59%     | 97\.41%    | 0\.79%       |
| Senegal                | 3535          | 42         | 1761          | 51\.00%    | 2\.33%      | 97\.67%     | 14738         | 302        | 11458         | 76\.98%   | 2\.61%     | 97\.39%    | \-0\.28%     |
| Germany                | 183189        | 8530       | 164908        | 94\.68%    | 4\.92%      | 95\.08%     | 275560        | 9390       | 242656        | 76\.97%   | 1\.09%     | 98\.91%    | 3\.82%       |
| Mali                   | 1250          | 76         | 696           | 61\.76%    | 9\.84%      | 90\.16%     | 3024          | 128        | 2377          | 76\.95%   | 3\.00%     | 97\.00%    | 6\.84%       |
| Luxembourg             | 4016          | 110        | 3815          | 97\.73%    | 2\.80%      | 97\.20%     | 7916          | 124        | 6839          | 76\.12%   | 0\.46%     | 99\.54%    | 2\.34%       |
| Indonesia              | 25773         | 1573       | 7015          | 33\.32%    | 18\.32%     | 81\.68%     | 248852        | 9677       | 180797        | 75\.70%   | 4\.46%     | 95\.54%    | 13\.86%      |
| Dominican Republic     | 16908         | 498        | 9557          | 59\.47%    | 4\.95%      | 95\.05%     | 108783        | 2054       | 82274         | 75\.23%   | 2\.09%     | 97\.91%    | 2\.86%       |
| Moldova                | 8098          | 291        | 4455          | 58\.61%    | 6\.13%      | 93\.87%     | 46796         | 1211       | 35018         | 74\.87%   | 2\.92%     | 97\.08%    | 3\.21%       |
| Bulgaria               | 2499          | 139        | 1064          | 48\.14%    | 11\.55%     | 88\.45%     | 19014         | 765        | 13727         | 74\.61%   | 4\.71%     | 95\.29%    | 6\.84%       |
| Bolivia                | 9592          | 310        | 889           | 12\.50%    | 25\.85%     | 74\.15%     | 130986        | 7654       | 90240         | 74\.50%   | 7\.60%     | 92\.40%    | 18\.26%      |
| Bangladesh             | 44608         | 610        | 9375          | 22\.38%    | 6\.11%      | 93\.89%     | 350621        | 4979       | 258717        | 74\.48%   | 1\.72%     | 98\.28%    | 4\.39%       |
| Nepal                  | 1401          | 6          | 219           | 16\.06%    | 2\.67%      | 97\.33%     | 65276         | 427        | 47238         | 72\.93%   | 0\.89%     | 99\.11%    | 1\.78%       |
| Bosnia and Herzegovina | 2494          | 153        | 1831          | 79\.55%    | 7\.71%      | 92\.29%     | 25521         | 770        | 18109         | 71\.78%   | 3\.65%     | 96\.35%    | 4\.06%       |
| Kosovo                 | 1064          | 30         | 829           | 80\.73%    | 3\.49%      | 96\.51%     | 12683         | 488        | 8788          | 71\.19%   | 5\.44%     | 94\.56%    | \-1\.95%     |
| Algeria                | 9267          | 646        | 5549          | 66\.85%    | 10\.43%     | 89\.57%     | 50023         | 1679       | 35180         | 69\.96%   | 3\.37%     | 96\.63%    | 7\.06%       |
| Israel                 | 17012         | 284        | 14811         | 88\.73%    | 1\.88%      | 98\.12%     | 190929        | 1273       | 136780        | 69\.93%   | 0\.80%     | 99\.20%    | 1\.08%       |
| Finland                | 6826          | 316        | 5500          | 85\.20%    | 5\.43%      | 94\.57%     | 9046          | 341        | 7700          | 68\.89%   | 1\.12%     | 98\.88%    | 4\.31%       |
| Latvia                 | 1065          | 24         | 745           | 72\.21%    | 3\.12%      | 96\.88%     | 1526          | 36         | 1248          | 68\.03%   | 2\.33%     | 97\.67%    | 0\.79%       |
| Kenya                  | 1888          | 63         | 464           | 27\.91%    | 11\.95%     | 88\.05%     | 37079         | 650        | 23949         | 65\.86%   | 2\.44%     | 97\.56%    | 9\.52%       |
| Austria                | 16685         | 668        | 15520         | 97\.02%    | 4\.13%      | 95\.87%     | 38658         | 767        | 29516         | 62\.73%   | 0\.70%     | 99\.30%    | 3\.42%       |
| Switzerland            | 30845         | 1919       | 28400         | 98\.29%    | 6\.33%      | 93\.67%     | 50378         | 2050       | 40500         | 60\.98%   | 1\.07%     | 98\.93%    | 5\.26%       |
| Estonia                | 1865          | 67         | 1622          | 90\.56%    | 3\.97%      | 96\.03%     | 2941          | 64         | 2379          | 60\.22%   | \-0\.40%   | 100\.40%   | 4\.36%       |
| Denmark                | 11633         | 571        | 10327         | 93\.68%    | 5\.24%      | 94\.76%     | 23323         | 640        | 17738         | 60\.20%   | 0\.92%     | 99\.08%    | 4\.32%       |
| Italy                  | 232664        | 33340      | 155633        | 81\.22%    | 17\.64%     | 82\.36%     | 299506        | 35724      | 218703        | 59\.22%   | 3\.64%     | 96\.36%    | 14\.00%      |
| Iceland                | 1806          | 10         | 1794          | 99\.89%    | 0\.55%      | 99\.45%     | 2377          | 10         | 2125          | 57\.77%   | 0\.00%     | 100\.00%   | 0\.55%       |
| Slovenia               | 1473          | 108        | 1357          | 99\.46%    | 7\.37%      | 92\.63%     | 4470          | 142        | 3048          | 57\.40%   | 1\.97%     | 98\.03%    | 5\.40%       |
| Portugal               | 32203         | 1396       | 19186         | 63\.91%    | 6\.78%      | 93\.22%     | 69200         | 1920       | 45736         | 55\.69%   | 1\.94%     | 98\.06%    | 4\.85%       |
| Albania                | 1122          | 33         | 857           | 79\.32%    | 3\.71%      | 96\.29%     | 12535         | 364        | 6995          | 55\.55%   | 5\.12%     | 94\.88%    | \-1\.41%     |
| Norway                 | 8437          | 236        | 7727          | 94\.38%    | 2\.96%      | 97\.04%     | 13005         | 267        | 10371         | 53\.05%   | 1\.16%     | 98\.84%    | 1\.80%       |
| Sudan                  | 4800          | 262        | 1272          | 31\.96%    | 17\.08%     | 82\.92%     | 13555         | 836        | 6760          | 50\.43%   | 9\.47%     | 90\.53%    | 7\.61%       |
| Guinea\-Bissau         | 1256          | 8          | 42            | 3\.98%     | 16\.00%     | 84\.00%     | 2303          | 39         | 1127          | 49\.53%   | 2\.78%     | 97\.22%    | 13\.22%      |
| Czechia                | 9230          | 319        | 6546          | 74\.38%    | 4\.65%      | 95\.35%     | 50764         | 522        | 25425         | 43\.47%   | 1\.06%     | 98\.94%    | 3\.58%       |
| Ukraine                | 23204         | 696        | 9311          | 43\.13%    | 6\.96%      | 93\.04%     | 182900        | 3652       | 81131         | 43\.25%   | 3\.95%     | 96\.05%    | 3\.00%       |
| Ethiopia               | 1063          | 8          | 208           | 20\.32%    | 3\.70%      | 96\.30%     | 69709         | 1108       | 28634         | 42\.49%   | 3\.73%     | 96\.27%    | \-0\.02%     |
| Slovakia               | 1521          | 28         | 1356          | 90\.99%    | 2\.02%      | 97\.98%     | 6756          | 39         | 3571          | 41\.44%   | 0\.49%     | 99\.51%    | 1\.53%       |
| Lebanon                | 1191          | 26         | 708           | 61\.63%    | 3\.54%      | 96\.46%     | 29987         | 307        | 12507         | 41\.29%   | 2\.33%     | 97\.67%    | 1\.22%       |
| Lithuania              | 1670          | 70         | 1229          | 77\.78%    | 5\.39%      | 94\.61%     | 3814          | 87         | 2199          | 39\.24%   | 1\.72%     | 98\.28%    | 3\.67%       |
| Costa Rica             | 1047          | 10         | 658           | 63\.80%    | 1\.50%      | 98\.50%     | 65602         | 745        | 25127         | 38\.81%   | 2\.92%     | 97\.08%    | \-1\.42%     |
| US                     | 1770165       | 103776     | 416461        | 29\.39%    | 19\.95%     | 80\.05%     | 6856884       | 199865     | 2615949       | 36\.23%   | 4\.19%     | 95\.81%    | 15\.76%      |
| Honduras               | 5094          | 201        | 536           | 14\.47%    | 27\.27%     | 72\.73%     | 72075         | 2204       | 22611         | 33\.75%   | 8\.32%     | 91\.68%    | 18\.95%      |
| Tunisia                | 1076          | 48         | 950           | 92\.75%    | 4\.81%      | 95\.19%     | 11260         | 164        | 2386          | 15\.12%   | 7\.47%     | 92\.53%    | \-2\.66%     |
| Ireland                | 24929         | 1651       | 22089         | 95\.23%    | 6\.95%      | 93\.05%     | 33121         | 1792       | 23364         | 15\.09%   | 9\.96%     | 90\.04%    | \-3\.00%     |
| Hungary                | 3867          | 524        | 2142          | 68\.94%    | 19\.65%     | 80\.35%     | 18866         | 686        | 4401          | 14\.94%   | 6\.69%     | 93\.31%    | 12\.96%      |
| Belgium                | 58186         | 9453       | 15769         | 43\.35%    | 37\.48%     | 62\.52%     | 103392        | 9950       | 18977         | 4\.74%    | 13\.41%    | 86\.59%    | 24\.06%      |
| France                 | 185616        | 28720      | 66051         | 51\.06%    | 30\.30%     | 69\.70%     | 473974        | 31174      | 77254         | 3\.60%    | 17\.97%    | 82\.03%    | 12\.34%      |
| Netherlands            | 46257         | 5951       | 178           | 13\.25%    | 97\.10%     | 2\.90%      | 100491        | 6327       | 2993          | 3\.38%    | 11\.78%    | 88\.22%    | 85\.31%      |
| United Kingdom         | 272826        | 38376      | 1187          | 14\.50%    | 97\.00%     | 3\.00%      | 401122        | 41877      | 2228          | 1\.26%    | 77\.08%    | 22\.92%    | 19\.92%      |
| Greece                 | 2915          | 175        | 1374          | 53\.14%    | 11\.30%     | 88\.70%     | 15595         | 344        | 1347          | 1\.01%    | 119\.01%   | \-19\.01%  | \-107\.72%   |
| Spain                  | 239228        | 27125      | 150376        | 74\.20%    | 15\.28%     | 84\.72%     | 671468        | 30663      | 150376        | 0\.72%    | 100\.00%   | 0\.00%     | \-84\.72%    |
| Sweden                 | 37113         | 4395       | 4971          | 25\.24%    | 46\.93%     | 53\.07%     | 88237         | 5865       | 0             | \-4\.44%  | \-41\.99%  | 141\.99%   | 88\.91%      |
| Serbia                 | 11381         | 242        | 6606          | 60\.17%    | 3\.53%      | 96\.47%     | 32938         | 743        | 0             | \-23\.40% | \-8\.21%   | 108\.21%   | 11\.74%      |


下面是美国各地区确诊数超过1000，按After-EC从高往低排序情况：

| Name                 | 0530Confirmed | 0530Deaths | 0530Recovered | Before\-EC | Before\-EDR | Before\-ERR | 0921Confirmed | 0921Deaths | 0921Recovered | After\-EC | After\-EDR | After\-ERR | ERR\-Changed |
|----------------------|---------------|------------|---------------|------------|-------------|-------------|---------------|------------|---------------|-----------|------------|------------|--------------|
| New Hampshire        | 4492          | 238        | 2802          | 67\.68%    | 7\.83%      | 92\.17%     | 7952          | 438        | 7201          | 93\.63%   | 4\.35%     | 95\.65%    | 3\.48%       |
| Mississippi          | 15229         | 723        | 9401          | 66\.48%    | 7\.14%      | 92\.86%     | 93556         | 2810       | 85327         | 93\.50%   | 2\.68%     | 97\.32%    | 4\.47%       |
| Massachusetts        | 96301         | 6768       |               | 7\.03%     | 100\.00%    | 0\.00%      | 127796        | 9317       | 109397        | 92\.50%   | 2\.28%     | 97\.72%    |              |
| Louisiana            | 39577         | 2786       | 28700         | 79\.56%    | 8\.85%      | 91\.15%     | 161462        | 5377       | 145570        | 91\.91%   | 2\.17%     | 97\.83%    | 6\.68%       |
| North Carolina       | 27794         | 929        | 14954         | 57\.15%    | 5\.85%      | 94\.15%     | 194355        | 3247       | 176422        | 91\.77%   | 1\.42%     | 98\.58%    | 4\.43%       |
| Tennessee            | 22566         | 364        | 15193         | 68\.94%    | 2\.34%      | 97\.66%     | 184409        | 2233       | 166674        | 90\.82%   | 1\.22%     | 98\.78%    | 1\.12%       |
| Minnesota            | 24190         | 1036       | 17864         | 78\.13%    | 5\.48%      | 94\.52%     | 90942         | 2021       | 82174         | 90\.63%   | 1\.51%     | 98\.49%    | 3\.97%       |
| Arkansas             | 7013          | 133        | 5166          | 75\.56%    | 2\.51%      | 97\.49%     | 76364         | 1197       | 66934         | 88\.41%   | 1\.69%     | 98\.31%    | 0\.82%       |
| Ohio                 | 35033         | 2149       |               | 6\.13%     | 100\.00%    | 0\.00%      | 145165        | 4623       | 123423        | 88\.03%   | 1\.97%     | 98\.03%    |              |
| Texas                | 62675         | 1652       | 40068         | 66\.57%    | 3\.96%      | 96\.04%     | 734778        | 15127      | 611856        | 84\.45%   | 2\.30%     | 97\.70%    | 1\.66%       |
| Wisconsin            | 18230         | 588        | 11338         | 65\.42%    | 4\.93%      | 95\.07%     | 102498        | 1244       | 86822         | 84\.07%   | 0\.86%     | 99\.14%    | 4\.07%       |
| Maine                | 2282          | 89         | 1505          | 69\.85%    | 5\.58%      | 94\.42%     | 5106          | 140        | 4384          | 83\.43%   | 1\.74%     | 98\.26%    | 3\.84%       |
| Oklahoma             | 6418          | 334        | 5435          | 89\.89%    | 5\.79%      | 94\.21%     | 77908         | 948        | 64941         | 83\.34%   | 1\.02%     | 98\.98%    | 4\.77%       |
| Indiana              | 34211         | 2125       |               | 6\.21%     | 100\.00%    | 0\.00%      | 112027        | 3512       | 88173         | 81\.49%   | 1\.55%     | 98\.45%    |              |
| District of Columbia | 8717          | 462        | 1100          | 17\.92%    | 29\.58%     | 70\.42%     | 14978         | 621        | 11856         | 81\.36%   | 1\.46%     | 98\.54%    | 28\.12%      |
| South Dakota         | 4960          | 62         | 3805          | 77\.96%    | 1\.60%      | 98\.40%     | 18869         | 202        | 15777         | 80\.74%   | 1\.16%     | 98\.84%    | 0\.45%       |
| North Dakota         | 2554          | 60         | 1943          | 78\.43%    | 3\.00%      | 97\.00%     | 18244         | 193        | 14841         | 80\.24%   | 1\.02%     | 98\.98%    | 1\.97%       |
| Utah                 | 9533          | 112        | 5995          | 64\.06%    | 1\.83%      | 98\.17%     | 64394         | 441        | 51660         | 78\.91%   | 0\.72%     | 99\.28%    | 1\.12%       |
| Pennsylvania         | 75697         | 5537       | 47133         | 69\.58%    | 10\.51%     | 89\.49%     | 155693        | 7985       | 123665        | 76\.66%   | 3\.10%     | 96\.90%    | 7\.41%       |
| Nebraska             | 13905         | 170        |               | 1\.22%     | 100\.00%    | 0\.00%      | 41388         | 452        | 30509         | 74\.70%   | 0\.92%     | 99\.08%    |              |
| West Virginia        | 1989          | 75         | 1290          | 68\.63%    | 5\.49%      | 94\.51%     | 14181         | 315        | 10317         | 72\.31%   | 2\.59%     | 97\.41%    | 2\.90%       |
| Iowa                 | 19244         | 531        | 11019         | 60\.02%    | 4\.60%      | 95\.40%     | 81007         | 1284       | 57942         | 68\.64%   | 1\.58%     | 98\.42%    | 3\.02%       |
| Michigan             | 56969         | 5464       | 38099         | 76\.47%    | 12\.54%     | 87\.46%     | 129662        | 6981       | 90216         | 62\.29%   | 2\.83%     | 97\.17%    | 9\.71%       |
| New Mexico           | 7624          | 351        | 2728          | 40\.39%    | 11\.40%     | 88\.60%     | 27683         | 851        | 15412         | 53\.58%   | 3\.79%     | 96\.21%    | 7\.61%       |
| Idaho                | 2803          | 82         | 2225          | 82\.30%    | 3\.55%      | 96\.45%     | 37901         | 447        | 20304         | 51\.82%   | 1\.98%     | 98\.02%    | 1\.58%       |
| Alabama              | 17359         | 618        | 9355          | 57\.45%    | 6\.20%      | 93\.80%     | 145780        | 2439       | 61232         | 39\.54%   | 3\.39%     | 96\.61%    | 2\.81%       |
| Delaware             | 9422          | 361        | 5205          | 59\.07%    | 6\.49%      | 93\.51%     | 19667         | 627        | 10376         | 38\.56%   | 4\.89%     | 95\.11%    | 1\.59%       |
| South Carolina       | 11394         | 487        | 6459          | 60\.96%    | 7\.01%      | 92\.99%     | 138124        | 3212       | 51431         | 36\.36%   | 5\.71%     | 94\.29%    | 1\.30%       |
| Arizona              | 19258         | 904        | 4657          | 28\.88%    | 16\.26%     | 83\.74%     | 214251        | 5478       | 33946         | 16\.23%   | 13\.51%    | 86\.49%    | 2\.75%       |
| Kentucky             | 9704          | 431        | 3231          | 37\.74%    | 11\.77%     | 88\.23%     | 61917         | 1112       | 11283         | 14\.99%   | 7\.80%     | 92\.20%    | 3\.97%       |
| Oregon               | 4185          | 153        | 2137          | 54\.72%    | 6\.68%      | 93\.32%     | 30995         | 529        | 5431          | 12\.79%   | 10\.25%    | 89\.75%    | \-3\.56%     |
| Virginia             | 43611         | 1370       | 5745          | 16\.31%    | 19\.26%     | 80\.74%     | 141022        | 3019       | 16903         | 9\.56%    | 12\.88%    | 87\.12%    | 6\.38%       |
| New Jersey           | 159608        | 11634      | 26301         | 23\.77%    | 30\.67%     | 69\.33%     | 200154        | 16069      | 34672         | 7\.89%    | 34\.63%    | 65\.37%    | \-3\.96%     |
| Rhode Island         | 14819         | 711        | 1225          | 13\.06%    | 36\.73%     | 63\.27%     | 23932         | 1097       | 2268          | 6\.50%    | 27\.01%    | 72\.99%    | 9\.71%       |
| Connecticut          | 42022         | 3912       | 7127          | 26\.27%    | 35\.44%     | 64\.56%     | 56024         | 4495       | 9204          | 5\.91%    | 21\.92%    | 78\.08%    | 13\.52%      |
| Colorado             | 26084         | 1443       | 3859          | 20\.33%    | 27\.22%     | 72\.78%     | 65379         | 2018       | 6291          | 5\.01%    | 19\.12%    | 80\.88%    | 8\.09%       |
| Maryland             | 52015         | 2509       | 3649          | 11\.84%    | 40\.74%     | 59\.26%     | 120568        | 3883       | 7378          | 4\.46%    | 26\.93%    | 73\.07%    | 13\.82%      |
| New York             | 369660        | 29710      | 65609         | 25\.79%    | 31\.17%     | 68\.83%     | 450473        | 33092      | 76218         | 3\.94%    | 24\.17%    | 75\.83%    | 7\.00%       |
| Nevada               | 8517          | 417        | 428           | 9\.92%     | 49\.35%     | 50\.65%     | 76036         | 1531       | 2026          | 3\.61%    | 41\.08%    | 58\.92%    | 8\.27%       |
| Kansas               | 9690          | 215        | 547           | 7\.86%     | 28\.22%     | 71\.78%     | 53627         | 601        | 1970          | 3\.42%    | 21\.34%    | 78\.66%    | 6\.88%       |
| Florida              | 55424         | 2447       |               | 4\.42%     | 100\.00%    | 0\.00%      | 685439        | 13317      |               | 1\.59%    | 100\.00%   | 0\.00%     |              |
| Georgia              | 46331         | 2004       |               | 4\.33%     | 100\.00%    | 0\.00%      | 307339        | 6604       |               | 1\.51%    | 100\.00%   | 0\.00%     |              |
| California           | 109895        | 4144       |               | 3\.77%     | 100\.00%    | 0\.00%      | 790096        | 15056      |               | 1\.39%    | 100\.00%   | 0\.00%     |              |
| Illinois             | 118917        | 5330       |               | 4\.48%     | 100\.00%    | 0\.00%      | 277920        | 8693       |               | 1\.23%    | 100\.00%   | 0\.00%     |              |
| Washington           | 21349         | 1118       |               | 5\.24%     | 100\.00%    | 0\.00%      | 82730         | 2049       |               | 1\.14%    | 100\.00%   | 0\.00%     |              |
| Puerto Rico          | 3718          | 133        |               | 3\.58%     | 100\.00%    | 0\.00%      | 42476         | 609        |               | 1\.12%    | 100\.00%   | 0\.00%     |              |
| Missouri             | 13298         | 774        |               | 5\.82%     | 100\.00%    | 0\.00%      | 115537        | 1838       |               | 0\.93%    | 100\.00%   | 0\.00%     |              |


[*返回主页*](.)
------------------------------------------------------------------


***