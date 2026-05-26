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
