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

### Language Learning App Specifications
- **Gamification**: Implement milestone badges for consecutive learning days and vocabulary completion.
- **Quiz System**: Support CSV/PDF export for quiz results, customizable notification times, and batch deletion in the admin backend.
- **Vector Search**: Implement pgvector Hybrid Search for vocabulary and articles, with a daily automatic incremental update schedule.
- **Personalization**: Display recommended articles and vocabulary on the homepage based on user browsing history.

### API Development Guidelines
- **TTS API**: Must support `dialect` parameter (Nanwang, Zhiben, Jianhe, Xiqun). Include a scheduled task (e.g., 3:00 AM) to pre-heat uncached vocabulary.
- **Vocabulary API**: Serve structured JSON data from `/home/ubuntu/puyuma_vocab_index.json` (17,584 sentences, 7,073 dictionary entries).
- **Subscription API**: Integrate ECPay for premium content (e.g., full language courses, audio downloads). Implement a webhook for payment verification and an automated daily cron job to downgrade expired subscriptions.

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
- **卑南文化特徵**：
  - **石板棺墓葬**：出土超過 2,000 具，多為「量身訂做」，由板岩石板鋪設墓穴四周，上方覆蓋超過棺口大小的蓋板。死者腳部朝向都蘭山（卑南族聖山），顯示出強烈的信仰與空間觀念。部分石板棺有多次葬的現象。
  - **陶器製作**：以夾砂陶為主，顏色多為橙紅或紅褐色。器型多樣，包括罐、缽、盆、豆等，表面常有繩紋、劃紋或刻劃紋裝飾。陶器不僅用於日常烹煮與儲存，也作為陪葬品。
  - **精美玉器**：玉管、玉玦、人獸形玉玦等。
- **卑南王（Pinadray）**：清朝乾隆年間封號，傳說統轄後山七十二社，影響力北至花蓮玉里、南至屏東恆春。
- **大庄事件（1888）**：光緒 14 年，花東縱谷卑南族、阿美族等反抗清朝統治的重要歷史事件。

## Material Culture (物質文化)

**IMPORTANT**: Only include items confirmed as Puyuma — do NOT mix with Amis, Rukai, or other tribes' items.

### 服飾與紋身 (Traditional Clothing & Tattoos)

- **男子服飾**：主色為紅、黃、綠、黑。成年男子穿著「後敞褲」（無襠短褲），方便山林活動。不同年齡階層有不同服飾規定。
- **女子服飾**：包含頭巾、上衣、胸兜、腰裙、綁腿。南王部落女子服飾常帶有精美十字繡圖案。
- **紋身文化**：卑南族確實存在傳統紋身文化，但主要流行於**知本社**，而射馬干社（建和）、大巴六九社（泰安）則較少施行，卑南社（南王）則完全不施行刺青。紋身圖案多為幾何圖形，具有社會階級與成年的象徵意義。

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
- **傳統漁法**：卑南族傳統漁法多在河川進行，使用魚筌（如竹編漏斗狀陷阱）、魚網、魚叉等工具。捕魚活動常伴隨祭祀儀式，祈求豐收並感謝河神。

## Traditional Instruments (傳統樂器)

- **竹製樂器**：卑南族傳統樂器多就地取材，以竹製為主。常見的有竹口笛、竹鼓、竹琴等。
- **口簧琴**：利用竹片與細繩製作，透過口腔共鳴發聲，常於休閒或男女傳情時吹奏。
- **文化意義**：樂器演奏多伴隨歌謠與舞蹈，在祭典、聚會或日常生活中扮演重要角色，是情感表達與文化傳承的媒介。

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
- **命名系統**：屬於「非永續性家名制」（家屋名制）。個人名字後會附加家屋名，形成「個人名 + 家屋名」的結構。直接稱呼個人本名被視為不禮貌，通常以親屬稱謂或長幼關係代稱。命名儀式通常在出生後第五天舉行。
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

## Language Phonology & Grammar (語言音韻與文法)

### Phonology (音韻系統)
- **輔音 (Consonants)**：18個。包含雙唇音 (p, b, m)、齒齦音 (t, d, n, s, r, l)、翹舌音 (ʈ/tr, ɖ/dr, ɭ/lr)、硬顎音 (j/y)、軟腭音 (k, ɡ, ŋ/ng, w)、聲門音 (ʔ/')。
- **元音 (Vowels)**：4個。前閉元音 /i/、後閉元音 /u/、中面央元音 /ə/ (e)、開央元音 /a/。
- **方言差異**：南王方言保留了古卑南語的濁塞音，但在語法上較為創新（如斜格與屬格的合併）。建和方言在詞彙上與其他三方言差異最大。

### Grammar (文法摘要)

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

## Ancestral Shrines & Leadership (祖靈屋與頭目制度)

- **祖靈屋 (karuma'an)**：卑南族傳統社會的核心信仰與祭祀空間，通常由各氏族或家族的長女（或女性長輩）負責管理。祖靈屋內供奉著家族的祖靈（biruwa），是舉行重要祭儀（如收穫祭、年祭）時的祭祀中心。各部落的祖靈屋在建築形式與祭祀細節上略有差異，但皆嚴格遵守禁忌，非家族成員或未經允許者不得隨意進入。
- **頭目制度 (ayawan)**：卑南族的頭目制度在歷史上曾發展出強大的酋邦體系（如卑南大王）。傳統上，頭目（ayawan）通常由特定家族世襲，負責統籌部落公共事務、對外談判及主持大型祭典。頭目的權威建立在血緣、財富、個人能力及宗教神聖性上。現代社會中，頭目雖失去實質政治權力，但仍是部落文化傳承與精神凝聚的象徵。

## Divination & Taboos (占卜與禁忌)

- **占卜系統**：卑南族傳統占卜主要用於預測吉凶、決定祭典日期或尋找失物。常見方式包括：
  - **夢占**：透過祭司或當事人的夢境解析吉凶，如夢見清澈溪水為吉，夢見濁水或落齒為凶。
  - **鳥占**：觀察特定鳥類（如繡眼畫眉）的飛行方向與叫聲來判斷吉凶。
  - **竹占**：巫師利用竹片加熱後的裂紋來解讀神意。
- **禁忌 (taboo)**：卑南族生活中有嚴格的禁忌規範，如狩獵前禁止與妻子同房、禁止食用特定食物；喪葬期間家屬需遵守嚴格的飲食與行為限制；女性在生理期或懷孕期間不得參與某些祭典或接觸獵具。

## Traditional Medicine & Shamanism (傳統醫療與巫醫)

- **巫醫儀式**：卑南族的傳統醫療高度依賴巫師（女巫 palama 與男巫）。疾病常被視為靈魂失落、惡靈作祟或觸犯禁忌的結果。巫師透過 Ya'ulas（召喚巫靈）儀式，使用檳榔、琉璃珠等法器進行診斷與驅邪。
- **藥草使用**：除了巫術治療，卑南族也擁有豐富的植物知識。例如使用長行天南星治療腫傷，廣葉鋸齒雙蓋蕨 (pa'at) 減緩腹瀉，棕葉狗尾草 (dalina) 止血消炎，大葉楠 (lrahu) 解熱退燒。

## Clothing Crafts & Dyeing (服飾工藝與染色)

- **紡織技術**：傳統使用水平背帶織布機（機杼）進行織布，材料多來自苧麻。
- **染色技術**：使用天然植物染料，如薯榔（染紅褐色）、九芎（染黑色）、泥土（媒染劑）。
- **刺繡工藝**：南王部落以精美的十字繡聞名，常見圖案包括菱形（象徵祖靈之眼）、花草紋及人形紋。服飾的色彩與圖案不僅是裝飾，更代表年齡階級與社會地位。

## Japanese Colonial Period (日治時期歷史)

- **高砂義勇隊**：太平洋戰爭期間，部分卑南族人被徵召加入高砂義勇隊，如初鹿社頭目馬智禮的族人，參與南洋叢林戰。
- **皇民化運動**：日治後期的皇民化運動對卑南族文化造成衝擊，推行國語（日語）家庭、改日本名、神社參拜等政策，導致傳統祭儀與母語傳承受到壓抑。
- **青年團制度**：日本政府將卑南族傳統的年齡階級與會所制度（Palakuwan）改造為「青年團」，以利於殖民統治與動員。

## Language Revitalization (語言復振運動)

- **族語教育**：面對卑南語瀕危的困境，部落積極推動語言復振。如設立「花環部落學校」與「南王 Puyuma 花環實驗小學」，將族語融入正規教育。
- **數位化工具**：原住民族語言研究發展基金會（ILRDF）建置「族語E樂園」與線上辭典，提供豐富的數位學習資源。
- **族語認證**：推動族語能力認證考試，鼓勵年輕一代學習並使用母語。

## Inter-tribal Relations & Religion (族群互動與宗教)

- **與阿美族**：歷史上，卑南族（特別是南王部落）曾與阿美族發生多次衝突與結盟。大庄事件（1888）中，兩族曾共同反抗清朝統治。
- **與排灣族**：知本部落等石生系統部落與鄰近的排灣族在地理與文化上有密切交流，部分神話傳說（如石生起源）有共通之處，但也曾因領地與資源發生摩擦。
- **與漢人**：清代以來，漢人移民進入臺東平原，卑南族透過貿易、通婚等方式與漢人互動，但也面臨土地流失與文化同化的壓力。
- **與外來宗教**：天主教與基督教（長老教會）傳入後，對卑南族傳統信仰產生深遠影響。天主教在南王、建和等部落較為盛行，常將傳統祭儀（如大獵祭）與彌撒結合，展現高度的文化融合（如白冷會神父的本土化策略）。長老教會則在部分部落推動母語聖經翻譯，對語言保存有一定貢獻。

## Tribal Demographics & Geography (部落人口與地理)

卑南族總人口約 15,000 人（2023年統計），主要分布於臺東縣臺東市及卑南鄉。

- **南王部落 (Puyuma)**：位於臺東市南王里，竹生系統，人口約 3,000+，歷史上曾為「卑南大王」所在地。
- **知本部落 (Katratripulr)**：位於臺東市知本里，石生系統，人口約 2,000+，擁有保存完整的會所制度。
- **建和部落 (Kasavakan)**：位於臺東市建和里，石生系統，人口約 1,500+，以木雕藝術與年祭聞名。
- **初鹿部落 (Ulivelivek)**：位於卑南鄉初鹿村，石生系統，人口約 1,500+，以七月收穫祭（鞦韆祭）為特色。
- **利嘉部落 (Likavung)**：位於卑南鄉利嘉村，石生系統，人口約 1,200+，以年底的大獵祭與年祭為核心。
- **部落遷移歷史**：「竹生」傳說以南王部落為中心，其祖先在現址定居並發展出強大的政治實體；「石生」傳說則以知本部落為發源地，其祖先從 Ruvoahan 登陸後，部分向北遷徙建立建和、初鹿等部落，部分向南與排灣族融合。

## Academic Research & Literature (學術研究文獻)

- **移川子之藏**：日治時期學者，著有《台灣高砂族系統所屬之研究》，對卑南族神話與部落系統有基礎分類。
- **馬淵東一**：深入研究卑南族母系社會結構與親屬制度。
- **宋龍生**：著有《卑南族的社會與文化》、《台灣原住民史：卑南族史篇》，是當代卑南族研究的重要文獻。
- **陳文德**：研究卑南族年齡階級與會所制度。
307	- **孫大川**：卑南族學者，著有《夾縫中的族群建構》，探討原住民文學與主體性。
308	- **林志興**：卑南族學者，著有《南王部落史》，深入探討南王部落的歷史沿革與文化變遷。
309	- **巴代 (Badai)**：卑南族作家，著有多部以卑南族歷史為背景的小說（如《笛鸛》、《斯卡羅人》），結合口傳歷史與文學創作。
310	- **陳光榮**：卑南族學者，致力於卑南語文法與詞彙的整理與研究。
311	
312	## Traditional Plant Knowledge (傳統植物知識)
313	
314	- **月桃 (lra'up)**：葉片用於包裹食物（如 avai），莖部剝絲後用於編織草蓆 (ruma) 與置物簍。
315	- **大葉楠 (lrahu)**：葉片搗碎敷於額頭可解熱退燒，木材可用於建築與製作器具。
316	- **廣葉鋸齒雙蓋蕨 (pa'at)**：嫩葉可食，根部煎水飲用可減緩腹瀉。
317	- **棕葉狗尾草 (dalina)**：葉片搗碎敷於傷口可止血消炎。
318	- **苧麻 (gliu)**：莖皮纖維是傳統織布 (tenun) 的主要原料。
319	- **薯榔**：塊根富含單寧，是傳統染布的重要紅色染料。
320	- **九芎**：木材堅硬，常用於製作農具與建築支柱，樹皮可作為黑色染料。
321	- **檳榔 (savang)**：不僅是日常嗜好品，更是祭祀、巫術儀式 (Ya'ulas) 與社交（如定情）中不可或缺的神聖物品。
322	
323	## Detailed Ritual Differences (各部落祭典差異)
324	
325	- **南王部落**：年底的年祭 ('amiyan) 結合了猴祭 (Vasivas) 與大獵祭 (Mangayau)，強調年齡階級的晉升與軍事訓練。
326	- **知本部落**：大獵祭後有獨特的「除喪祭」，由青年會所成員至喪家吟唱哀歌並進行除喪儀式，隨後跳勇士舞。
327	- **建和部落**：以七月的小米收穫祭 (kemaderunan) 與年底的年祭為重，年祭中包含鞦韆祭，具有祈福與聯誼的意義。
328	- **初鹿部落**：七月的收穫祭 (mulaliyaban) 是其年度最盛大的祭典，包含盪鞦韆儀式，象徵祈求農作物豐收。
329	
330	## Lu Sen-Bao's Compositions (陸森寶歌曲清單)
331	
332	陸森寶 (Baliwakes Raera) 創作了近 30 首卑南語歌曲，深刻影響了卑南族現代音樂：
333	- **《美麗的稻穗》 (bulai naniyam da ruma')**：1958年創作，八二三砲戰期間思念前線族人，以豐收的稻穗寄託和平的期望。
334	- **《懷念年祭》 (puyuma 'amiyan)**：1964年創作，描繪南王部落年祭的歡樂場景與遊子思鄉之情。
335	- **《卑南王》 (pinadray)**：歌頌卑南大王 Pinadray 的英雄事蹟與歷史榮耀。
336	- **《頌祭祖先》 (kakuwayanan)**：祭祀祖先的莊嚴歌曲，表達對傳統文化的敬重。
337	- **《散步歌》 (taulu)**：輕鬆愉快的日常歌謠。
338	- **《祝福》 (kikarun)**：用於婚禮或慶典的祝福歌曲。
339	- **《思故鄉》 (lralra'i)**：抒發對部落與親人的深切思念。
