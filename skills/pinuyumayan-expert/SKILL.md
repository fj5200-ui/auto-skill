---
name: pinuyumayan-expert
description: >
  卑南族（Pinuyumayan / Puyuma）文化、語言與應用開發專家技能。
  Use when: (1) answering questions about Puyuma indigenous culture, history, rituals, or language;
  (2) developing or modifying the pinuyumayan website or related applications;
  (3) processing FormosanBank Puyuma corpora or ILRDF vocabulary data;
  (4) generating AI summaries or content mentioning the Puyuma people.
  Key constraints enforced: correct tribal naming (禁用「普悠瑪族」), four-dialect TTS support, UI/UX standards for language learning and cultural archive pages.
---

# Pinuyumayan Expert Skill

## Critical Naming Rules (MUST FOLLOW)

- **NEVER** use「普悠瑪族」— this is incorrect.
- **ALWAYS** use「卑南族」or「Pinuyumayan」(or「Puyuma」in English contexts).
- Tribal grouping: use「卑南族十社」(Puyuma Ten Communities), NOT「八社」.

## Language & Dialects

Puyuma has **4 dialects** — always distinguish them in TTS, teaching materials, and data processing:

| Dialect | Puyuma Name | System |
|---------|-------------|--------|
| 南王 Nanwang | Puyuma | 竹生系統 |
| 知本 Zhiben | Katratripulr | 石生系統 |
| 建和 Jianhe | Kasavakan | 石生系統 |
| 西群 Xiqun | Ulivelivek etc. | 石生系統 |

**TTS rule**: Use English phonetic approximations for pronunciation rules — never Chinese zhuyin descriptions.

**Disabled vocabulary**: Must NOT contain simplified Chinese characters.

## FormosanBank Corpus & Audio Resources

**XML Corpus Location**: `/home/ubuntu/FormosanBank/Corpora/ePark/XML/`
Subdirectories per dialect: `Nanwang_Puyuma.xml`, `Zhiben_Puyuma.xml`, `Jianhe_Puyuma.xml`, `Xiqun_Puyuma.xml`

**Audio Resources (Google Drive)** — ✅ VERIFIED: All 6,648 files confirmed as Puyuma-only (0 non-Puyuma files):
Root Folder ID: `1mdzXxD5XQAVLIAdrD5xy3iRI7B3XnlUo`

| Category | Drive Folder ID | Nanwang | Zhiben | Jianhe | Xiqun | Total |
|----------|----------------|---------|--------|--------|-------|-------|
| ep1_九階教材 | `1_Tq3vumPRAOPvIxZPHfBsQ3O9SVufH0d` | 0 | 0 | 1,000 | 0 | 1,000 |
| ep2_文化篇 | `1U8yvI1jaLRAlE9nJZoxOI_YnpXP3SKw7` | 0 | 0 | 777 | 223 | 1,000 |
| ep2_生活會話篇 | `1vKRsHvyprVDfAjBX057OvCnjDwU3FzRS` | 0 | 0 | 754 | 246 | 1,000 |
| ep2_情境族語 | `1HdsHtjsKRMdS6N7GWgIixfG_VUnV-8_X` | 0 | 0 | 906 | 94 | 1,000 |
| ep2_閱讀書寫篇 | `1HJbFL8y6ZjdI0Vc3MbXFm9X32MJqkMb9` | 0 | 0 | 689 | 311 | 1,000 |
| ep2_族語短文 | `1BwBcThAEAVQrOqjHlLDycgsM0b5LCAzV` | 162 | 162 | 162 | 162 | 648 |
| ILRDF_字典 | `1o_iEc2dbet-cENHLjv86R_b67M0TlakZ` | — | — | — | — | 1,000 |
| **合計** | | **162** | **162** | **4,288** | **1,036** | **6,648** |

*Note: ILRDF audio files are named `Puyuma_XXXX.mp3` without dialect prefix. Use `gws` CLI to access.*

Total corpus: **27,018 sentences** across 10 categories. Parse script: `/home/ubuntu/skills/pinuyumayan-expert/scripts/parse_puyuma_corpus.py`

| Category | Dir Name | Sentences |
|----------|----------|-----------|
| 學習詞表 | `xue_xi_ci_biao_learning_vocabulary` | 4,364 |
| 文化篇 | `wen_hua_pian_cultural_section` | 3,900 |
| 生活會話 | `sheng_huo_hui_hua_pian_daily_conversation` | 3,167 |
| 情境族語 | `qing_jing_zu_yu_contextual_indigenous_language` | 3,701 |
| 閱讀書寫 | `yue_du_shu_xie_pian_reading_writing` | 3,327 |
| 句型篇高中 | `ju_xing_pian_gao_zhong_sentence_patterns_senior_high` | 3,457 |
| 句型篇國中 | `ju_xing_pian_guo_zhong_sentence_patterns_junior_high` | 2,404 |
| 九階教材 | `jiu_jie_jiao_cai_nine_level_materials` | 1,804 |
| 族語短文 | `zu_yu_duan_wen_indigenous_language_essays` | 648 |
| 圖畫故事 | `tu_hua_gu_shi_pian_picture_story` | 246 |

Each sentence includes: original/standard romanization, IPA phonetics, Chinese & English translation, audio URL.

## pinuyumayan Website Development Standards

For detailed UI/UX and feature specs, read: `/home/ubuntu/skills/pinuyumayan-expert/references/development_guidelines.md`

Key rules (summary):
- `/language` page: add Quick Access cards (今日挑戰, 繼續學習, 詞彙排行榜, 每日測驗), grid vocab layout (4-col), TTS play button per word, learning progress tracking with `recordQuizCompletion`.
- `/culture` page: cultural figures link to `/culture/figures/:id`; expand media categories (紀錄片, 祭儀樂舞).
- Tribe intro: rename「認識八社」→「卑南族十社」, vertical scroll card list.

## Cultural Knowledge Reference

For detailed cultural knowledge (rituals, social structure, history), read: `/home/ubuntu/skills/pinuyumayan-expert/references/culture_history.md`

Key facts (summary):
- **Social structure**: Matrilineal society (母系社會) — property/surname passed through daughters; men marry into wife's family.
- **Male institutions**: Age-grade system (年齡階級組織) + Men's house (會所) — Trakuban (少年) → Palakuwan (青年).
- **Annual rituals**: March (婦女除草完工慶) → April (祭祖) → July (小米收穫祭) → December (年祭: 猴祭 + 大獵祭).
- **Core belief**: biruwa / pirua — spirits of nature, ancestors, and the cosmos.
- **Historical note**: South Wang (南王) tribe was historically dominant; Puyuma King (卑南大王) recognized by Qing dynasty.

## Notable Figures (卑南族重要人物)

**MUST verify all figures are confirmed Puyuma — do NOT include figures from other tribes.**

| Name | Puyuma Name | Period | Significance |
|------|-------------|--------|--------------|
| 南志信 | Sising Katadrepan | 1886–1958 | 臺灣第一位原住民西醫；制憲國大代表；首任臺灣省政府委員；推動原住民正名 |
| 陸森寶 | Baliwakes Raera | 1910–1988 | 「卑南族音樂靈魂」；創作《美麗的稻穗》《懷念年祭》等近30首卑南語歌曲 |
| 胡德夫 | Kimbo Hu | 1950– | 臺灣民歌運動先驅；以黑人靈歌詮釋原住民歌曲；推動原住民權益運動 |
| 陳建年 | Chaonira Eleng | 1967– | 金曲歌王；陸森寶外孫；代表作《海洋》 |
| 紀曉君 | Samingad | 1978– | 金曲獎得主；陳建年外甥女；以卑南母語演唱見長 |
| 張惠妹（阿妹） | A-Mei | 1972– | 天后級歌手；卑南族知本部落出身 |
| 桑布伊 | Sangpuy Katatepan | 1979– | 金曲獎最佳原住民歌手；知本部落出身 |

## Archaeology & History (考古與歷史)

- **卑南遺址**：位於臺東縣卑南山東南麓，距今 5300–2300 年前，環太平洋最大墓葬群，出土石板棺、玉器、陶器。現為國立臺灣史前文化博物館卑南文化公園（約 30 公頃）。
- **卑南文化特徵**：石板棺墓葬（死者朝向都蘭山）、精美玉器（玉管、玉玦、人獸形玉玦）、陶器。
- **卑南王（Pinadray）**：清朝乾隆年間封號，傳說統轄後山七十二社，影響力北至花蓮玉里、南至屏東恆春。
- **大庄事件（1888）**：光緒 14 年，花東縱谷卑南族、阿美族等反抗清朝統治的重要歷史事件。

## Material Culture (物質文化)

**IMPORTANT**: Only include items confirmed as Puyuma — do NOT mix with Amis, Rukai, or other tribes' items.

### 服飾 (Traditional Clothing)

- **男子服飾**：主色為紅、黃、綠、黑。成年男子穿著「後敞褲」（無襠短褲），方便山林活動。不同年齡階層有不同服飾規定。
- **女子服飾**：包含頭巾、上衣、胸兜、腰裙、綁腿。南王部落女子服飾常帶有精美十字繡圖案。

### 刀具 (Traditional Knives)

- **卑南族番刀**：男子狩獵、防身與日常必備工具。
  - 刀鞘：木頭製成，雕刻傳統圖騰，部分裝飾金屬線或動物骨骸。
  - 功能：狩獵、防身、日常勞作。
  - 文化意義：成年男子的身份象徵，大獵祭中的重要配備。

### 工藝品 (Traditional Crafts)

- **月桃葉編織**：卑南族婦女擅長以月桃葉編製籃子、蓆子等生活器具。
- **十字繡**：南王部落的特色工藝，常見於女子服飾與裝飾品上，圖案多為幾何形與自然元素。
- **玉器**：卑南遺址出土大量玉器，顯示卑南文化在史前時代已有高度工藝水準。

## Men's House Architecture (會所建築)

- **少年會所（Trakuban / takoban）**：南王、知本部落為高干欄建築，圓形平台外徑約 11 公尺，竹梯上下，屋頂為雙坡頂加兩個半圓形頂，是卑南族代表性建築。
- **青年會所（Palakuwan / parakoan）**：長方形建築，室內中央設方形地灶，周圍竹編床台。

## Traditional House Architecture (傳統家屋)

- **家屋名稱**：ruma，由家族長女繼承（母系社會特徵）。
- **建築結構**：柱梁系統，竹木材料，雙坡茅葺頂，牆體為雙層竹片夾茅草。
- **空間配置**：矩形平面，東西向雙入口（前門朝東象徵日出，後門朝西代表日落）。家屋正脊下方設中柱（主要祭祀對象）、竹編高床式寢床、三石灶（西南側）、穀倉（北側）。

## Shamanism & Traditional Medicine (巫師制度與傳統醫療)

- **巫師制度**：卑南族巫覡文化盛行，巫師分為女巫（巴拉馬/palama）與男巫（覡）。女巫主要負責巫醫、巫術儀式，施法治病祈福；男巫主要掌握氏族的祭祀與部落公共事務所需的占卜、祭祀與祝禱。
- **傳統醫療植物**：長行天南星（治療腫傷）、廣葉鋸齒雙蓋蕨 (pa'at，減緩腹瀉)、棕葉狗尾草 (dalina，止血消炎)、大葉楠 (lrahu，解熱退燒)。

## Mythology & Origin Stories (神話傳說)

**IMPORTANT**: Only include myths confirmed as Puyuma — do NOT mix with other tribes' legends.

- **石生傳說**（石生系統部落）：遠古時代，台東知本里海岸附近巨石裂開，誕生一名女子，其後代與因洪水逃難的男子結合，成為卑南族祖先。另一版本：在 Panapanayan（Ruvoahan）發祥地，石塊中誕生 Vais，其後代繁衍卑南族人，部分族人遷徙至大武山成為排灣族始祖。
- **竹生傳說**（竹生系統部落）：一位女神在太麻里鄉美和村將竹子豎立於地，竹節裂開後誕生一對男女神，成為卑南族祖先。女神也將石頭丟到地上，誕生阿美族祖先。
- **大洪水與日月起源**（卡大地布部落）：大洪水後，五位兄弟姊妹乘坐木臼逃難，Hunin 和 Vulan 成為日月，Sukasukaw 和 Tavatav 在 Panapanayan 登陸，繁衍後代。

## Hunting & Fishing Culture (漁獵文化)

- **狩獵工具**：主要使用弓箭、長矛、陷阱（如套索陷阱、石板陷阱）及獵犬。
- **大獵祭 (Mangayau)**：是卑南族最重要的狩獵祭儀，不僅是為了獲取肉類，更是男性成年禮與軍事訓練的結合。狩獵前需進行嚴格的禁忌與祭祀，獵物分配有嚴格的社會規範，通常會優先分給長者與寡婦。

## Food & Agriculture Culture (飲食與農業文化)

- **傳統主食**：小米、旱稻、甘薯、芋頭；蛋白質來源為狩獵動物肉類及河川魚貝類。
- **小米文化**：小米是炊飯、煮粥、製飴及釀酒的原料，在祭典中不可或缺。相傳祖先 Temalasaw 與 Tayban 將小米種子從蘭嶼帶回部落。
- **傳統食品**：月桃葉包裹糯米粉糰和鹹豬肉製成的月桃小米或糯米粿粽（慶典食品）。
- **檳榔**：日常零食，也是祭祀時不可或缺的重要物品。
- **水稻引入**：18 世紀時，卑南王 Pinadray 引入水稻耕作技術。

## Music & Songs (音樂歌謠)

**IMPORTANT**: Do NOT include pasibutbut (布農族祈禱小米豐收歌) — it belongs to Bunun people, NOT Puyuma.

- **卑南語詞彙**：「唱歌」= semenay，「歌謠」= senay。
- **音樂特徵**：以「對偶原則」為顯著特徵，體現在歌謠修辭、實詞與聲詞、領唱與答唱的安排，反映母系社會精神。
- **即興填詞**：非儀式性歌謠可依情境即興填詞（pungadangadan），歌詞富含多層次隱喻並力求雙聲疊韻。
- **陸森寶代表作**：《美麗的稻穗》、《懷念年祭》、《卑南王》等近 30 首卑南語歌曲，將傳統古調譜上五線譜。

## Life Rituals (生命禮俗)

- **出生**：胎衣、臍帶與米糠置於竹筒內掛在屋簷下。第二天請女巫以檳榔擦拭嬰兒身體。男嬰持小刀，女嬰持小鋤，象徵男獵女耕。
- **命名**：出生後第五天舉行，由家長或族長從傳統階級名譜中選取名字。
- **婚姻**：男子入贅女方家庭（從妻居）。男子以頭巾和檳榔袋作為定情飾物送給女子。
- **喪葬**：傳統有室內葬習俗，屍身屈肢裝殮，頭向西面向上，配偶需陪靈三夜。

## Modern Development (現代發展)

- **卑南學**：自 2013 年起，每兩年舉辦一次學術研討會，建立屬於卑南族群的知識體系，鼓勵族人自我書寫與詮釋歷史文化。
- **教育自主**：卑南族花環部落學校、臺東縣南王 Puyuma 花環實驗小學的設立，是爭取教育自主權的重要實踐。
- **語言復振**：卑南語被列為瀕危語言；臺東縣卑南族民族自治事務促進發展協會成立語言推動組織。
- **社會運動**：大獵祭成員因持槍被捕事件、卡大地布遷葬事件、知本光電案等，促使族人透過學術研究與社會行動捍衛自身權益。

## Language Vocabulary Categories (語言詞彙分類)

根據 FormosanBank 語料庫提取，卑南語詞彙豐富，以下為部分基礎詞彙分類（以建和方言為例）：

- **數字**：一 (sasaya), 二 (duduwaya), 三 (tutuluwa), 四 (papata), 五 (lrulruwaca), 六 (nanema), 七 (pituwa), 八 (waluwaluwa), 九 (iwaywaya), 十 (mukecep/pulu')。
- **親屬稱謂**：爸爸 (ama), 媽媽 (ina), 兄長 (iva), 姊姊 (iva na vavayan), 孫子/孫女 (tumuwan), 丈夫 (turuma'anlri)。
- **身體部位**：頭 (canguru'), 眼睛 (maca), 耳朵 (calinga), 鼻子 (ungcan), 嘴巴 (udung), 手 (lima), 腳 (kuwi)。
- **動植物**：豬 (lriyung), 狗 (suwan), 鳥 ('ayam), 魚 (vulraw), 樹 (kawi), 花朵 ('apuc), 竹子 (vasikaw)。

## Language Grammar Summary (語言文法摘要)

- **語序**：動詞置前（VSO）。
- **焦點系統**：4 種形態（主事焦點、受事焦點、對象焦點、工具焦點）。
- **時制**：完成式、未完成式、未來式。
- **語氣**：祈使式、規勸未來式。
- **代詞格位**：主格、斜格（直接格、間接格、非主詞格）、中性格。
- **格位標記**：i（單數人稱）、a（單數非人稱）、na（複數）。
- **詞綴系統**：前綴（如 ka-, ki-, mi-, pa-, si-）、後綴（如 -a, -an, -aw, -ay）、中綴（-in-, -em-）、環綴（ka- -an, si- -an 等）。
- **參考文法**：Teng, Stacy Fang-Ching (2008). *A Reference Grammar of Puyuma*. Pacific Linguistics 595, ANU.

## Advanced Rituals & Crafts (進階祭儀與工藝)

- **猴祭 (Vasivas)**：少年（13-18歲）的成年禮，藉由刺猴培養膽識與服從精神。祭典前需進行驅邪（puvangaw），並在會所（trakuban）接受嚴格訓練。
- **大獵祭 (Mangayau)**：青年與成年男子的狩獵祭儀，象徵除舊佈新與軍事訓練。祭典包含野外紮營、狩獵、長老教導、除喪儀式，最後由婦女搭建凱旋門迎接。
- **月桃編織**：採集月桃莖，經曝曬、剝絲、揉捻後，編織成草蓆（ruma）、置物簍等。
- **十字繡**：南王部落特色，圖案多為菱形（祖靈之眼）、花草紋，色彩以紅、黃、綠為主，象徵生命與自然。

## Academic Research & Literature (學術研究文獻)

- **移川子之藏**：日治時期學者，著有《台灣高砂族系統所屬之研究》，對卑南族神話與部落系統有基礎分類。
- **馬淵東一**：深入研究卑南族母系社會結構與親屬制度。
- **宋龍生**：著有《卑南族的社會與文化》、《台灣原住民史：卑南族史篇》，是當代卑南族研究的重要文獻。
- **陳文德**：研究卑南族年齡階級與會所制度。
