# Caption Selection Priority / 字幕選擇優先順序

## English

### Overview
This document describes the intelligent caption selection algorithm used by the YouTube Subtitles Extension. The system automatically selects the best available captions based on user preferences and available options.

### Selection Priority Logic

The extension follows this priority order when selecting captions:

#### 1. **Exact Language Match (Highest Priority)**
- For user's preferred language, look for exact matches
- **Special case for Traditional Chinese (zh-tw)**: 
  - Looks for `zh-tw`, `zh-TW`, or captions containing "Taiwan"
  - If found → **Use native CC only** (no live translation needed)

#### 2. **Chinese Variant Smart Handling**
- **For Traditional Chinese (zh-tw)**: Look for Chinese variants
  - `zh`, `zh-cn`, `zh-CN`, `zh-Hans` or captions containing "Chinese" or "Simplified"
  - **If English is also available** → Prefer English to avoid redundancy
  - **If only Chinese variants available** → **Use native CC only** to avoid redundant Chinese-to-Chinese translation
  - **If English + Chinese variants available** → Use English for live translation

- **For Simplified Chinese (zh-cn)**: Look for Chinese variants
  - `zh-tw`, `zh-TW`, `zh-Hant` or captions containing "Traditional" or "Taiwan"
  - **If English is also available** → Prefer English to avoid redundancy
  - **If only Chinese variants available** → **Use native CC only** to avoid redundant Chinese-to-Chinese translation

- **For Hong Kong Chinese (zh-hk)**: Look for any Chinese variants
  - Any Chinese variant (`zh-tw`, `zh-cn`, `zh-Hans`, `zh-Hant`)
  - **If English is also available** → Prefer English to avoid redundancy
  - **If only Chinese variants available** → **Use native CC only** to avoid redundant Chinese-to-Chinese translation

#### 3. **Non-English Auto-Generated (Video's Native Language)**
- Look for any non-English auto-generated captions (Korean, Japanese, Thai, Spanish, etc.)
- **Rationale**: When YouTube creates auto-generated captions in a specific language, it indicates the video is spoken in that language
- If found → **Use live bilingual translation** (Source language → User's preferred language)

#### 4. **English Auto-Generated**
- Fallback to English auto-generated captions (most common and reliable)
- If found → **Use live bilingual translation** (English → User's preferred language)

#### 5. **Any English Captions**
- Fallback to any available English captions (manual or auto-generated)

#### 6. **First Available Caption (Last Resort)**
- Use the first available caption regardless of language

### Examples

#### Example 1: Traditional Chinese User with Korean Video
- **User Preference**: Traditional Chinese (zh-tw)
- **Available Captions**: Korean (auto-generated), English (auto-generated)
- **Selection**: Korean (auto-generated) ← Priority #3
- **Result**: Live bilingual translation (Korean → Traditional Chinese)

#### Example 2: Traditional Chinese User with Chinese Video (English Available)
- **User Preference**: Traditional Chinese (zh-tw)
- **Available Captions**: Chinese (Simplified), English
- **Selection**: English ← Priority #2 (avoid redundancy)
- **Result**: Live bilingual translation (English → Traditional Chinese)

#### Example 3: Traditional Chinese User with Chinese Video (No English)
- **User Preference**: Traditional Chinese (zh-tw)
- **Available Captions**: Chinese (Simplified) only
- **Selection**: Chinese (Simplified) ← Priority #2 (smart handling)
- **Result**: Native CC only (avoid redundant Chinese-to-Chinese translation)

#### Example 4: Traditional Chinese User with Taiwan Video
- **User Preference**: Traditional Chinese (zh-tw)
- **Available Captions**: Chinese (Taiwan), Korean, English
- **Selection**: Chinese (Taiwan) ← Priority #1
- **Result**: Native CC only (exact match, no translation needed)

### Benefits

1. **Intelligent Language Matching**: Prioritizes content in user's preferred language
2. **Cultural Sensitivity**: Special handling for Chinese language variants
3. **Redundancy Avoidance**: Prevents confusing dual Chinese displays
4. **Quality Over Convenience**: Prefers original language captions over English translations
5. **Graceful Degradation**: Always finds the best available option

---

## 繁體中文（台灣）

### 概述
本文件說明 YouTube 字幕擴充功能所使用的智慧字幕選擇演算法。系統會根據使用者偏好和可用選項自動選擇最佳的字幕。

### 選擇優先順序邏輯

擴充功能在選擇字幕時遵循以下優先順序：

#### 1. **精確語言匹配（最高優先）**
- 針對使用者偏好語言，尋找精確匹配
- **繁體中文（zh-tw）特殊情況**：
  - 尋找 `zh-tw`、`zh-TW` 或包含「Taiwan」的字幕
  - 如果找到 → **僅使用原生 CC**（無需即時翻譯）

#### 2. **中文變體智慧處理**
- **針對繁體中文（zh-tw）**：尋找中文變體
  - `zh`、`zh-cn`、`zh-CN`、`zh-Hans` 或包含「Chinese」或「Simplified」的字幕
  - **如果英文也可用** → 偏好英文以避免冗餘
  - **如果僅有中文變體** → **僅使用原生 CC** 以避免冗餘的中文對中文翻譯
  - **如果英文 + 中文變體都可用** → 使用英文進行即時翻譯

- **針對簡體中文（zh-cn）**：尋找中文變體
  - `zh-tw`、`zh-TW`、`zh-Hant` 或包含「Traditional」或「Taiwan」的字幕
  - **如果英文也可用** → 偏好英文以避免冗餘
  - **如果僅有中文變體** → **僅使用原生 CC** 以避免冗餘的中文對中文翻譯

- **針對香港中文（zh-hk）**：尋找任何中文變體
  - 任何中文變體（`zh-tw`、`zh-cn`、`zh-Hans`、`zh-Hant`）
  - **如果英文也可用** → 偏好英文以避免冗餘
  - **如果僅有中文變體** → **僅使用原生 CC** 以避免冗餘的中文對中文翻譯

#### 3. **非英文自動生成（影片原生語言）**
- 尋找任何非英文自動生成字幕（韓文、日文、泰文、西班牙文等）
- **理由**：當 YouTube 以特定語言創建自動生成字幕時，表示影片是以該語言錄製
- 如果找到 → **使用即時雙語翻譯**（來源語言 → 使用者偏好語言）

#### 4. **英文自動生成**
- 後備至英文自動生成字幕（最常見且可靠）
- 如果找到 → **使用即時雙語翻譯**（英文 → 使用者偏好語言）

#### 5. **任何英文字幕**
- 後備至任何可用的英文字幕（手動或自動生成）

#### 6. **第一個可用字幕（最後手段）**
- 使用第一個可用字幕，無論語言

### 範例

#### 範例 1：繁體中文使用者觀看韓文影片
- **使用者偏好**：繁體中文（zh-tw）
- **可用字幕**：韓文（自動生成）、英文（自動生成）
- **選擇**：韓文（自動生成）← 優先順序 #3
- **結果**：即時雙語翻譯（韓文 → 繁體中文）

#### 範例 2：繁體中文使用者觀看中文影片（有英文）
- **使用者偏好**：繁體中文（zh-tw）
- **可用字幕**：簡體中文、英文
- **選擇**：英文 ← 優先順序 #2（避免冗餘）
- **結果**：即時雙語翻譯（英文 → 繁體中文）

#### 範例 3：繁體中文使用者觀看中文影片（無英文）
- **使用者偏好**：繁體中文（zh-tw）
- **可用字幕**：僅簡體中文
- **選擇**：簡體中文 ← 優先順序 #2（智慧處理）
- **結果**：僅原生 CC（避免冗餘的中文對中文翻譯）

#### 範例 4：繁體中文使用者觀看台灣影片
- **使用者偏好**：繁體中文（zh-tw）
- **可用字幕**：中文（台灣）、韓文、英文
- **選擇**：中文（台灣）← 優先順序 #1
- **結果**：僅原生 CC（精確匹配，無需翻譯）

### 優點

1. **智慧語言匹配**：優先選擇使用者偏好語言的內容
2. **文化敏感性**：特別處理中文語言變體
3. **避免冗餘**：防止令人困惑的雙中文顯示
4. **品質優於便利性**：偏好原始語言字幕而非英文翻譯
5. **優雅降級**：總是找到最佳可用選項

---

## Technical Implementation / 技術實作

### Code Location / 程式碼位置
- File: `chrome-extension/lib/subtitles-manager/youtube.js`
- Functions: `findBestCaptionTrack()`, `findBestCaptionMenuItem()`, `shouldUseNativeCCOnly()`, `cleanCaptionsUrl()`

### Key Features / 主要功能
- Automatic caption detection / 自動字幕偵測
- Language preference matching / 語言偏好匹配
- Fallback mechanism / 後備機制
- **Chinese variant smart handling / 中文變體智慧處理**
- **Redundancy avoidance / 冗餘避免**
- **YouTube translation parameter cleaning / YouTube 翻譯參數清理**

### Chinese Variant Smart Handling / 中文變體智慧處理

#### Problem / 問題
Chinese users (zh-tw, zh-cn, zh-hk) could encounter confusing dual Chinese displays when only Chinese variants are available:

- **Traditional Chinese user** with Simplified Chinese captions would see:
  - **Translated**: Traditional Chinese (translated from Simplified)
  - **Original**: Simplified Chinese

This creates redundant and confusing content for users who can read both Chinese variants.

中文使用者（zh-tw、zh-cn、zh-hk）在僅有中文變體可用時可能遇到令人困惑的雙中文顯示：

- **繁體中文使用者** 觀看簡體中文字幕會看到：
  - **翻譯**：繁體中文（從簡體翻譯）
  - **原文**：簡體中文

這為能夠閱讀兩種中文變體的使用者創造了冗餘且令人困惑的內容。

#### Solution / 解決方案
The `shouldUseNativeCCOnly()` function now includes smart logic for Chinese variants:

1. **Check for exact language match** → Use native CC only
2. **If Chinese variant found**:
   - **English also available** → Prefer English (meaningful bilingual experience)
   - **Only Chinese variants** → Use native CC only (avoid redundancy)

`shouldUseNativeCCOnly()` 函數現在包含中文變體的智慧邏輯：

1. **檢查精確語言匹配** → 僅使用原生 CC
2. **如果找到中文變體**：
   - **英文也可用** → 偏好英文（有意義的雙語體驗）
   - **僅有中文變體** → 僅使用原生 CC（避免冗餘）

### YouTube Translation Parameter Issue / YouTube 翻譯參數問題

#### Problem / 問題
YouTube maintains session-based language preferences that can cause issues when navigating between videos of different languages. When a user:

1. Watches a Korean video with Korean captions
2. Navigates to an English video
3. YouTube automatically adds `tlang=ko` to translate English captions to Korean

This results in the extension receiving Korean-translated text instead of the original English captions.

YouTube 會維護基於會話的語言偏好，這可能在不同語言影片間導航時造成問題。當使用者：

1. 觀看韓文影片並使用韓文字幕
2. 導航到英文影片
3. YouTube 自動添加 `tlang=ko` 將英文字幕翻譯成韓文

這導致擴充功能接收到韓文翻譯文本而非原始英文字幕。

#### Solution / 解決方案
The `cleanCaptionsUrl()` function removes the `tlang` parameter from intercepted YouTube captions URLs to ensure we always get the original source language captions.

`cleanCaptionsUrl()` 函數會從攔截的 YouTube 字幕 URL 中移除 `tlang` 參數，確保我們總是獲得原始來源語言的字幕。

**Before / 之前:**
```
https://www.youtube.com/api/timedtext?...&lang=en&tlang=ko&...
```

**After / 之後:**
```
https://www.youtube.com/api/timedtext?...&lang=en&...
```

This prevents double translation (English → Korean → Target Language) and ensures better translation quality.

這防止了雙重翻譯（英文 → 韓文 → 目標語言）並確保更好的翻譯品質。 
