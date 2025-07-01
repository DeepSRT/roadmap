# Version - 1.5.2
## 🚀 Version 1.5.2 Release Ready!

#### **🎯 Major Achievements:**
- **Complete bilingual caption system** working for all language combinations
- **Intelligent user control** that respects explicit user actions
- **Independent sidebar functionality** regardless of Extension CC state
- **Server-side language-aware processing** with dynamic AI prompts
- **Professional testing framework** with 50+ comprehensive test cases

#### **🔧 Technical Milestones:**
- **Client-server coordination** with explicit source/target languages
- **Multiple optimization point fixes** preventing conflicts
- **Block count consistency** eliminating 400 batch errors
- **Programmatic vs user click detection** preventing false triggers
- **Dynamic AI prompt generation** for accurate translations

#### **📚 Documentation Excellence:**
- **BILINGUAL_CAPTIONS_LESSONS_LEARNED.md** - Complete technical guide
- **TEST_CASES.md** - Professional QA framework
- **Updated README.md** - Clear system behavior explanation
- **Comprehensive regression checklist** for future releases

#### **🌐 Language Support Matrix:**
All combinations working correctly:
- Chinese ↔ English, Korean, Japanese
- Korean ↔ Chinese, English, Japanese  
- Japanese ↔ Chinese, English, Korean
- English ↔ All Asian languages

### **🎉 Ready for Production:**

Version 1.5.2 represents a complete, tested, and documented bilingual caption system that:
- ✅ Works reliably across all supported language combinations
- ✅ Respects user control while providing intelligent automation
- ✅ Performs optimally for both perfect and non-perfect language matches
- ✅ Handles errors gracefully with comprehensive fallback mechanisms
- ✅ Maintains quality through professional testing framework

# Version - 1.5.1
## 🐛 Bug Fixes
  - Fixed [#62](https://github.com/DeepSRT/roadmap/issues/62)
  - Fixed [#63](https://github.com/DeepSRT/roadmap/issues/63)

# Version - 1.5.0
## ✨ New Features
  - Closed [#59](https://github.com/DeepSRT/roadmap/issues/59)

# Version - 1.4.6
## 🐛 Bug Fixes
  - Fixed [#54](https://github.com/DeepSRT/roadmap/issues/54)

# Version - 1.4.5
## 🐛 Bug Fixes
  - Fixed [#51](https://github.com/DeepSRT/roadmap/issues/51)

# Version - 1.4.0
## 🐛 Bug Fixes
  - Fixed [#35](https://github.com/DeepSRT/roadmap/issues/35) [#36](https://github.com/DeepSRT/roadmap/issues/36) [#37](https://github.com/DeepSRT/roadmap/issues/37) [#38](https://github.com/DeepSRT/roadmap/issues/38)

# Version - 1.3.4
## 🐛 Bug Fixes
  - Fixed [#27](https://github.com/DeepSRT/roadmap/issues/27)

# Version - 1.3.3
## 🐛 Bug Fixes
  - Fixed [#25](https://github.com/DeepSRT/roadmap/issues/25)

# Version - 1.3.2
## 🐛 Bug Fixes
  - Fixed [#21](https://github.com/DeepSRT/roadmap/issues/21)

# Version - 1.3.1
## 🐛 Bug Fixes
  - Fixed [#19](https://github.com/DeepSRT/roadmap/issues/19)

# Version - 1.3.0
## 🐛 Bug Fixes
- zh-tw preferred when native zh-tw CC is available [#16](https://github.com/DeepSRT/roadmap/issues/16)

## ✨ New Features
- Introducing SRT Partner [#15](https://github.com/DeepSRT/roadmap/issues/15)


# Version - 1.2.3
## 🐛 Bug Fixes
- Fixed Chinese language selection mapping where zh-cn (Simplified Chinese) and zh-hk (Hong Kong Chinese) were incorrectly defaulting to zh-tw (Traditional Chinese) in subtitle requests [#13](https://github.com/DeepSRT/roadmap/issues/13)
- Fixed UI issue with double scrollbars in the sidebar that was affecting user experience [#7](https://github.com/DeepSRT/roadmap/issues/7)
  - Implemented single scrollbar solution using flexbox layout
  - Improved overall sidebar container structure

## ✨ New Features
- Added a copy button to the transcript container for easily copying raw transcript text [#10](https://github.com/DeepSRT/roadmap/issues/10)
  - Matches existing copy functionality in summary container
  - Improves user workflow for text extraction

## 📝 Technical Changes
- Refactored sidebar CSS to use flexbox for better content management
- Updated language mapping logic in transcription API requests

# Version - 1.2.2
  - Fix [#4](https://github.com/DeepSRT/roadmap/issues/4) [#5](https://github.com/DeepSRT/roadmap/issues/5)

# Version - 1.2.1
  - New Language - 繁體中文(香港）

# Version - 1.2.0
  - support bulleted summary mode

# Version - 1.1.4
   - make the transcript text area more compact by replacing the newlines with spaces
   - refactor the code by splitting a single huge JS with 1000+ lines into multiple small modules
   -  remove not required host permissions to scope down the requested permissions and avoid future proofing
   -  reload button now only refreshes side panel, not reloading the video

# Version - 1.1.3
  - realtime lang switching and subtitles refresh
  - refactor the user preference management
  - new language support - Thai

# Version - 1.1.2
  - increase the font size of the live captions
  - more flexible configurations will be available soon

# Version - 1.1.1
  - minor fix

# Version - 1.1.0
  - 🚀 Live Captions support(preview) for zh-CN, zh-TW, KO, JA, FR and ES. 

# Version - 1.0.6
  - better AI support in some regions
  - improved zh-TW summary quality
  - improved JA(JP) title translation quality

# Version - 1.0.5
  - support font-size selection
