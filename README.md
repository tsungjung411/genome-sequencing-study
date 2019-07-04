
## 名詞解釋
- DNA：deoxyribonucleic[di͵ɑksiraɪbonuˋkliɪk] acid, 去氧核醣核酸(繁體), 脱氧核醣核酸(簡體)
  - 一種生物分子，帶有遺傳資訊
  - 染色體上的編碼分子
  - 比較：RNA: Ribonucleic[raɪbonuˋkliɪk]  acid, 核糖核酸
- gene：基因（DNA 上特定的片段）
- sequencing：定序(繁體)，測序(簡體)
  - 簡單講：從 DNA 序列讀出 ATCG 字串
- bp：base paire [鹼基對](https://zh.wikipedia.org/wiki/%E7%A2%B1%E5%9F%BA%E5%AF%B9)
  - 形成：
    - 核酸 DNA & RNA 的單體
  - 基本原料：
    - 腺嘌呤（A）（注音：[ㄒㄧㄢˋ ㄆㄧㄠ ㄌㄧㄥˊ](https://www.moedict.tw/~%E8%85%BA%E5%98%8C%E5%91%A4)）
    - 胸腺嘧啶（T）（注音：ㄒㄩㄥ ㄒㄧㄢˋ [ㄇ一ˋ ㄉ一ㄥˋ](https://www.moedict.tw/~%E5%98%A7%E5%95%B6)）
    - 鳥嘌呤（G）（注音：[ㄋㄧㄠˇ ㄆㄧㄠ ㄌㄧㄥˊ](https://www.moedict.tw/~%E9%B3%A5%E5%98%8C%E5%91%A4)）
    - 胞嘧啶（C）（注音：ㄅㄠ [ㄇ一ˋ ㄉ一ㄥˋ](https://www.moedict.tw/~%E5%98%A7%E5%95%B6)）
    - 尿嘧啶（U）。
- kbp：kilo base pair 千鹼基對，kbp 簡寫為 kb (不等於 "kilo byte")
- mbp：mega base pair 兆鹼基對
- read：an (inferred) sequence of base pairs，一條(推論測得)的鹼基對序列
  - short reads: 短序列讀長
  - long reads: 長序列讀長
- read length：讀長(單位：bp)，序列片段長短
- high-throughput: 高通量

<br>

## 定序技術
- 演化：
  - 第一代：
    - 桑格定序法(Sanger Sequencing)，為第二代 NGS 的基礎
      - [註1](https://yourgene.pixnet.net/blog/post/66237085), 
        [註2](https://unclegene6666.pixnet.net/blog/post/305966068),
        [註3](https://www.bilibili.com/video/av45259672/?spm_id_from=333.788.videocard.0)(影片)
    - 名詞解釋：
      - PCR: Polymerase Chain Reaction 聚合酶連鎖反應
        - 影片：[10502選修生物ch11 5 06基因放大技術 聚合酶連鎖反應PCR二簡](https://www.youtube.com/watch?v=vUxyiAYOh5w)
      - [NTP](https://zh.wikipedia.org/wiki/%E6%A0%B8%E8%8B%B7%E4%B8%89%E7%A3%B7%E9%85%B8): 核苷三磷酸（核苷酸）
      - dNTP: 去氧核苷三磷酸
      - [ddNTP](https://zh.wikipedia.org/wiki/%E5%8F%8C%E8%84%B1%E6%B0%A7%E6%A0%B8%E8%8B%B7%E9%85%B8): 雙去氧核苷三磷酸(雙脫氧核苷三磷酸)
      - [primer](https://zh.wikipedia.org/wiki/%E5%BC%95%E7%89%A9)：DNA 引子，為人工合成的 DNA 片段
  - 第二代：
      - 次世代定序儀(Next Generation Sequencing, NGS)
  - 第三代：
- 考量：
  - 讀長：單次定序所得到的序列長度
  - 通量：單位時間內所能產出的數據量（定序速度x定序數量的綜合表現）
  - 準確性：讀取序列的準確程度
  - 成本：花費的錢


## 基因工程
- [HD16_聚合酶鏈鎖反應00464](https://www.youtube.com/watch?v=vhWlY18IGnk)
  - 犯罪現場 -> 收集檢體 -> 萃取 DNA -> 第量複製 DNA 樣本，以便於分析
- [11 6遺傳工程聚合酶、限制酶、連接酶、重組DNA、細菌的基因轉殖三公](https://www.youtube.com/watch?v=5si_ClkscdI) (影片)

<br>

## 分析工具
### 交換資料格式
- [[NGS]NGS的產物-FASTQ格式介紹](https://welgene.blogspot.com/2012/05/ngsngs-fastq.html)
  - 介紹 FASTA 和 FASTQ 的差異性
- [[wiki] FASTA格式](https://zh.wikipedia.org/wiki/FASTA%E6%A0%BC%E5%BC%8F)
- [[wiki] FASTQ格式](https://zh.wikipedia.org/wiki/FASTQ%E6%A0%BC%E5%BC%8F)


## 分析工具 BWA
- BWA: Burrow-Wheeler Aligner
  - 使用目的：
    - 一種軟體套件 / 一套演算法，用在「序列比對」上
    - 將定序得到的 reads，比對到人基因體參考序列上
    - 也就是說，將某個 DNA 序列，映射到人類基因體資料庫上，相當於 db.findIndex(dna)
  - 演算法：
    - 有三種：
      - BWA-BackTrack
      - BWA-SW
      - BWA-MEM
    - 如何選擇([參考](https://www.jianshu.com/p/180655da09a7))：
      - reads < 70bp，使用 BWA-Backtrack
      - 70bp <= reads <= 1Mbp 
        - 有頻繁的 gaps 時，使用 BWA-SW
        - 其餘，使用 BWA-MEM (預設使用)
        - BWA-SW & BWA-MEM 皆支援 long-reads, split alignment
 
  - 使用說明：
    - [BWA 下载、安装與執行](http://www.bioinfo-scrounger.com/archives/181)
    - [BWA 執行說明](https://kknews.cc/zh-tw/news/gbo2ko9.html)
    - [BWA 主要參數說明](https://blog.csdn.net/u014182497/article/details/51690341)

- [序列比对 BWA(Burrows-Wheeler Aligner)](https://www.jianshu.com/p/180655da09a7)
- [如何利用 BWA 進行序列比對呢？](https://kknews.cc/zh-tw/news/gbo2ko9.html)
- [[gutbub] BWA 原始碼 (https://github.com/lh3/bwa)](https://github.com/lh3/bwa)
- [[官網] Burrows-Wheeler Aligner (http://bio-bwa.sourceforge.net/)](http://bio-bwa.sourceforge.net/)

<br>

## 分析工具 GATK
- [【原创】GATK使用方法详解（包含bwa使用）第一部分](http://blog.sina.cn/dpool/blog/s/blog_12d5e3d3c0101qu6e.html)
- [GATK 之 HaplotypeCaller](http://www.biotrainee.com/thread-1417-1-1.html)
  - GATK的主要功能其实就是识别变异位点，其他功能都是锦上添花。

<br>

## 分析工具 DeepVariant
- [結合深度學習與基因檢測的DeepVariant](https://yourgene.pixnet.net/blog/post/118252122)
  - DeepVariant 的原理講解
- [[精準醫療] Variant Calling 的戰況分析](https://medium.com/@chungtsai/%E7%B2%BE%E6%BA%96%E9%86%AB%E7%99%82-variant-calling-%E7%9A%84%E6%88%B0%E6%B3%81%E5%88%86%E6%9E%90-97e77d0730c8)
  - DeepVarient v.s. GATK
  
<br>

## 科普
- [基因與生物](https://www.youtube.com/watch?v=XDxBTP0Pals)
  - DNA 的生命藍圖
- [【分子生物学动画】Sanger法测序 Sanger双脱氧链终止法](https://www.bilibili.com/video/av45259672/?spm_id_from=333.788.videocard.0)
- [什麼是單核苷酸多型性 (Single Nucleotide Polymorphism，SNP](https://unclegene6666.pixnet.net/blog/post/308333779)
  - SNP = 生物多樣性
  - SNP v.s. 突變(Mutation)?


## 其他術語
- [genome](https://tw.dictionary.search.yahoo.com/search?p=genome): 基因體(繁體) , 基因組(簡體)
- HGP: Human Genome Project, 人類基因體計劃
- WGS: Whole Genome Sequencing, 全基因體定序
- GRC: Genome Reference [Consortium](https://tw.dictionary.search.yahoo.com/search?p=Consortium), 基因體參照序列聯盟
- [GC 含量](https://zh.wikipedia.org/wiki/GC%E5%90%AB%E9%87%8F)
