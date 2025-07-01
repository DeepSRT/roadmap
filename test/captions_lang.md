
# DeepSRT Test Cases for Captions

This document outlines comprehensive test cases for the DeepSRT bilingual caption system. Each test case validates the correct behavior for different user language preferences and video content combinations.

## Test Methodology

### Caption Display Rules
- **Perfect Language Match**: User's preferred language = Video's native language → **Native captions only**
- **Non-Perfect Language Match**: User's preferred language ≠ Video's native language → **Bilingual captions**
  - **Top**: Translated captions (user's preferred language)
  - **Bottom**: Native captions (video's original language)

### Test Video Library
| Language | Video ID | Title | URL |
|----------|----------|-------|-----|
| **Chinese (zh-tw)** | `CtUtxYXLmgQ` | AI 資料中心與機器人雙爆發 | [Watch](https://www.youtube.com/watch?v=CtUtxYXLmgQ) |
| **English (en)** | `5mlb83mrjPE` | Stan Druckenmiller Interview | [Watch](https://www.youtube.com/watch?v=5mlb83mrjPE) |
| **Korean (ko)** | `Ak2SiHYekdA` | Korean Content | [Watch](https://www.youtube.com/watch?v=Ak2SiHYekdA) |
| **Japanese (ja)** | `Hk_IybulQcc` | Japanese Content | [Watch](https://www.youtube.com/watch?v=Hk_IybulQcc) |

---

## Test Cases by User Language Preference

### 🇹🇼 Taiwan Users (`preferredLang=zh-tw`)

#### Test Case 1.1: Perfect Match - Chinese User + Chinese Video
- **Video**: [AI 資料中心與機器人雙爆發](https://www.youtube.com/watch?v=CtUtxYXLmgQ) (zh-tw)
- **Expected Result**: ✅ **Native zh-tw captions only**
- **Rationale**: Perfect language match → Optimal performance with native rendering
- **Validation**:
  - [ ] Only native Chinese captions visible at bottom
  - [ ] No extension overlay captions
  - [ ] YouTube's native CC button shows "ON"
  - [ ] Extension CC button shows "ON"

#### Test Case 1.2: Bilingual - Chinese User + English Video
- **Video**: [Stan Druckenmiller Interview](https://www.youtube.com/watch?v=5mlb83mrjPE) (en)
- **Expected Result**: ✅ **Bilingual zh-tw + en captions**
- **Rationale**: Non-perfect match → Show both languages for context
- **Validation**:
  - [ ] Chinese translated captions at top (extension overlay)
  - [ ] English native captions at bottom (YouTube native)
  - [ ] Both caption streams synchronized
  - [ ] Extension CC button shows "ON"

#### Test Case 1.3: Bilingual - Chinese User + Korean Video
- **Video**: [Korean Content](https://www.youtube.com/watch?v=Ak2SiHYekdA) (ko)
- **Expected Result**: ✅ **Bilingual zh-tw + ko captions**
- **Validation**:
  - [ ] Chinese translated captions at top
  - [ ] Korean native captions at bottom
  - [ ] Translation quality is appropriate

#### Test Case 1.4: Bilingual - Chinese User + Japanese Video
- **Video**: [Japanese Content](https://www.youtube.com/watch?v=Hk_IybulQcc) (ja)
- **Expected Result**: ✅ **Bilingual zh-tw + ja captions**
- **Validation**:
  - [ ] Chinese translated captions at top
  - [ ] Japanese native captions at bottom
  - [ ] CJK character rendering is correct

---

### 🇰🇷 Korean Users (`preferredLang=ko`)

#### Test Case 2.1: Perfect Match - Korean User + Korean Video
- **Video**: [Korean Content](https://www.youtube.com/watch?v=Ak2SiHYekdA) (ko)
- **Expected Result**: ✅ **Native ko captions only**
- **Validation**:
  - [ ] Only native Korean captions visible
  - [ ] No extension overlay
  - [ ] Optimal performance (native rendering)

#### Test Case 2.2: Bilingual - Korean User + Chinese Video
- **Video**: [AI 資料中心與機器人雙爆發](https://www.youtube.com/watch?v=CtUtxYXLmgQ) (zh-tw)
- **Expected Result**: ✅ **Bilingual ko + zh-tw captions**
- **Validation**:
  - [ ] Korean translated captions at top
  - [ ] Chinese native captions at bottom
  - [ ] CJK to Korean translation quality

#### Test Case 2.3: Bilingual - Korean User + English Video
- **Video**: [Stan Druckenmiller Interview](https://www.youtube.com/watch?v=5mlb83mrjPE) (en)
- **Expected Result**: ✅ **Bilingual ko + en captions**
- **Validation**:
  - [ ] Korean translated captions at top
  - [ ] English native captions at bottom
  - [ ] Financial/technical term translation accuracy

#### Test Case 2.4: Bilingual - Korean User + Japanese Video
- **Video**: [Japanese Content](https://www.youtube.com/watch?v=Hk_IybulQcc) (ja)
- **Expected Result**: ✅ **Bilingual ko + ja captions**
- **Validation**:
  - [ ] Korean translated captions at top
  - [ ] Japanese native captions at bottom
  - [ ] CJK character handling

---

### 🇯🇵 Japanese Users (`preferredLang=ja`)

#### Test Case 3.1: Perfect Match - Japanese User + Japanese Video
- **Video**: [Japanese Content](https://www.youtube.com/watch?v=Hk_IybulQcc) (ja)
- **Expected Result**: ✅ **Native ja captions only**
- **Validation**:
  - [ ] Only native Japanese captions visible
  - [ ] Hiragana/Katakana/Kanji rendering correct
  - [ ] No extension overlay needed

#### Test Case 3.2: Bilingual - Japanese User + Chinese Video
- **Video**: [AI 資料中心與機器人雙爆發](https://www.youtube.com/watch?v=CtUtxYXLmgQ) (zh-tw)
- **Expected Result**: ✅ **Bilingual ja + zh-tw captions**
- **Validation**:
  - [ ] Japanese translated captions at top
  - [ ] Chinese native captions at bottom
  - [ ] Traditional Chinese character handling

#### Test Case 3.3: Bilingual - Japanese User + English Video
- **Video**: [Stan Druckenmiller Interview](https://www.youtube.com/watch?v=5mlb83mrjPE) (en)
- **Expected Result**: ✅ **Bilingual ja + en captions**
- **Validation**:
  - [ ] Japanese translated captions at top
  - [ ] English native captions at bottom
  - [ ] Technical term translation (AI, finance)

#### Test Case 3.4: Bilingual - Japanese User + Korean Video
- **Video**: [Korean Content](https://www.youtube.com/watch?v=Ak2SiHYekdA) (ko)
- **Expected Result**: ✅ **Bilingual ja + ko captions**
- **Validation**:
  - [ ] Japanese translated captions at top
  - [ ] Korean native captions at bottom
  - [ ] Cross-CJK translation quality
