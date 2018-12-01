# 簡述


剛剛看到yutin1987上傳的2018台灣公投的[所有開票所的結果](https://github.com/g0v/referendum_report/tree/master/results2)，出於對資料的手癢，就立即下載下來跑了分析。不跑不知道，一跑嚇一跳。通過初步的描述分析就可以發現，中選會公佈的有些開票所的結果出現了明顯不合理的數據！

廢話不多說，直接上結果。

首先，這是所有公投案之間的散點圖。可以看到，與鄉鎮層級的結果不同的是，在每張圖上，垂直和水平方向都出現了不少的觀測值，這是不合常理的。

<img src="scatter.png">

我們隨便看看其中的一張。
<img src="scatter_1.png">

我一開始以為是極端值特有的屬性，但是看到下面這張圖，就發現有些開票結果是明顯有問題的。這是第14案vs第15案的散點圖。我們知道這兩案都是平權方提出的，兩案的開票結果應該是高度正相關的。在絕大多數的開票所，結果也確實是高度正相關。但是，散點圖也顯示，有不少的奇怪的觀測值出現在圖的正上方和正右方。若仔細看這些極端值的話，他們在兩個公投案的結果上是負相關的！
<img src="scatter_2.png">

畫上兩條線後，一目了然！兩條斜度是1和-1的斜線可以完美地貫穿所有的觀測值。+1斜線附近的觀測值是正常的。-1斜線附近的觀測值是不正常的，在這些開票，有一案的公投結果應該是報反了！
<img src="scatter_3.png">

我們可以直接在中選會的網站上找到這些開票所的結果。例如，以南投縣中寮鄉0373開票所為例。下面是兩案結果的鏈接：

http://referendum.2018.nat.gov.tw/pc/zh_TW/08/10008000800000373.html

http://referendum.2018.nat.gov.tw/pc/zh_TW/09/10008000800000373.html

我們可以看到，14案和15案的結果是相反的。隨便再舉一例：高雄市三民區0943開票所。

http://referendum.2018.nat.gov.tw/pc/zh_TW/08/64000000500000943.html

http://referendum.2018.nat.gov.tw/pc/zh_TW/09/64000000500000943.html

這些結果都是明顯不合理的。

結論：中選會公佈的公投案結果有重大瑕疵。投票中少數人因為看不懂公投題目投反了是有可能的，但是一整個投票所所有人都投反了，這是難以用常理解釋的。雖然出問題的投票所應該不是很多，當不會影響總體的結果。但這依然是一個非常嚴肅的問題！

# 疑問 1

不合理的結果並不僅僅是出現在第14、15案，下面是第7、8案的散點圖。

<img src="scatter_78.png">

為什麼所有的極端值都出現在一條水平和一條垂直線上？左邊的極端值可以用一條-1斜線完美貫穿，也就是說那些投票所的結果應該也是有一案報反了，但是我無法解釋上面和下面的極端值。

報反的案例：桃園市八德區370。

http://referendum.2018.nat.gov.tw/pc/zh_TW/01/68000000800000370.html

http://referendum.2018.nat.gov.tw/pc/zh_TW/02/68000000800000370.html

# 疑問 2

以14、15案為例，為什麼所有報反的投票所都是結果極端的投票所？可以看到，-1斜線附近的觀測值都在極端，中間很少。也就是說，報反的投票所幾乎都是同意票特別多或者反對票特別多的投票所，為什麼？那些投票所的結果即便沒有報反，就真的可信嗎？

# 更新 1

有幾個問題可以立即回答。首先，中選會公佈的全國總的開票數結果是否等於各投開票結果之和呢？

答案：是！以下是各投開票所結果之和，與中選會公佈的[總開票結果](http://referendum.2018.nat.gov.tw/pc/zh_TW/00/00000000000000000.html)完全一致。也就是說，不僅僅是網站報錯了，中選會的原始數據就是錯的！

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>同意票數</th>
      <th>不同意票數</th>
    </tr>
    <tr>
      <th>案件</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>第10案</th>
      <td>7658008</td>
      <td>2907429</td>
    </tr>
    <tr>
      <th>第11案</th>
      <td>7083379</td>
      <td>3419624</td>
    </tr>
    <tr>
      <th>第12案</th>
      <td>6401748</td>
      <td>4072471</td>
    </tr>
    <tr>
      <th>第13案</th>
      <td>4763086</td>
      <td>5774556</td>
    </tr>
    <tr>
      <th>第14案</th>
      <td>3382286</td>
      <td>6949697</td>
    </tr>
    <tr>
      <th>第15案</th>
      <td>3507665</td>
      <td>6805171</td>
    </tr>
    <tr>
      <th>第16案</th>
      <td>5895560</td>
      <td>4014215</td>
    </tr>
    <tr>
      <th>第7案</th>
      <td>7955753</td>
      <td>2109157</td>
    </tr>
    <tr>
      <th>第8案</th>
      <td>7599267</td>
      <td>2346316</td>
    </tr>
    <tr>
      <th>第9案</th>
      <td>7791856</td>
      <td>2231425</td>
    </tr>
  </tbody>
</table>

# 更新 2

那麼，結果報反的投票所有多少呢？如果把-1斜線附近的投票所都抓出來的話（詳情見代碼），以下為統計結果。可以看到，絕大多數的報反的案例出現在第14、15案，有141個，佔全國投票所數量的0.89%。這141個投票所的投票數為93306，佔全國總投票數的0.9%，對總的投票結果的影響應該不大。

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>第7、8案</th>
      <th>第8、9案</th>
      <th>第10、11案</th>
      <th>第14、15案</th>
      <th>合集</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>不合理結果數量</th>
      <td>23</td>
      <td>19</td>
      <td>12</td>
      <td>141</td>
      <td>184</td>
    </tr>
  </tbody>
</table>


[這裡](dubious_cases.csv)是所有有疑問的結果。

