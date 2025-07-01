# DeepSRT Bilingual Captions: Test Cases Framework

This document outlines the comprehensive testing framework for DeepSRT's bilingual caption system. It includes 50+ test cases covering functionality, language support, user interactions, error handling, and performance.

## Test Environment Setup

### Prerequisites
- Chrome browser (latest stable version)
- DeepSRT extension installed
- YouTube account with access to various language videos
- Network connection with variable speeds (for performance testing)

### Test Video Requirements
- Videos with native CC in multiple languages
- Videos with auto-generated captions
- Videos with no captions
- Videos of varying lengths (short: <5min, medium: 5-30min, long: >30min)

## Functional Test Cases

### 1. Basic Caption Functionality

| ID | Test Case | Steps | Expected Result | Status |
|----|-----------|-------|-----------------|--------|
| F1 | Display bilingual captions | 1. Open YouTube video with CC<br>2. Enable DeepSRT<br>3. Select source and target languages | Bilingual captions display correctly | ✅ |
| F2 | Caption synchronization | 1. Play video<br>2. Observe timing of bilingual captions | Both languages appear simultaneously with correct timing | ✅ |
| F3 | Caption formatting | 1. Enable bilingual captions<br>2. Observe text formatting | Source language on top, target language below with clear visual separation | ✅ |
| F4 | Caption persistence | 1. Enable bilingual captions<br>2. Skip to different parts of video | Captions remain enabled and correctly synchronized | ✅ |
| F5 | Caption toggle | 1. Enable bilingual captions<br>2. Toggle captions off/on using YouTube controls | Captions respect YouTube's toggle state | ✅ |

### 2. Language Selection

| ID | Test Case | Steps | Expected Result | Status |
|----|-----------|-------|-----------------|--------|
| L1 | Source language auto-detection | 1. Open video with known CC language<br>2. Enable DeepSRT | System correctly identifies source language | ✅ |
| L2 | Target language selection | 1. Open language dropdown<br>2. Select different target language | UI updates and captions change to selected language | ✅ |
| L3 | Language preference persistence | 1. Set language preferences<br>2. Close and reopen browser<br>3. Open YouTube | Previous language preferences are maintained | ✅ |
| L4 | Regional language variant handling | 1. Test with videos having zh-CN, zh-TW, zh-HK captions | System correctly distinguishes between variants | ✅ |
| L5 | Browser language default | 1. Clear extension preferences<br>2. Open YouTube with fresh profile | Target language defaults to browser language | ✅ |

### 3. User Interface

| ID | Test Case | Steps | Expected Result | Status |
|----|-----------|-------|-----------------|--------|
| U1 | Sidebar visibility | 1. Toggle DeepSRT sidebar<br>2. Navigate between videos | Sidebar state persists between navigation | ✅ |
| U2 | Language dropdown population | 1. Open language selection dropdown | All supported languages appear in alphabetical order | ✅ |
| U3 | Active language indication | 1. Select languages<br>2. Observe UI indicators | Currently active languages are clearly highlighted | ✅ |
| U4 | Caption size adjustment | 1. Change caption size setting<br>2. Observe caption display | Captions resize according to setting | ✅ |
| U5 | Caption position | 1. Play video with captions<br>2. Observe position | Captions appear at bottom without obscuring important content | ✅ |

## Language Pair Test Cases

### 4. Asian Languages ↔ English

| ID | Test Case | Steps | Expected Result | Status |
|----|-----------|-------|-----------------|--------|
| AE1 | Chinese → English | 1. Open video with Chinese CC<br>2. Set target to English | Accurate translation with proper English grammar | ✅ |
| AE2 | English → Chinese | 1. Open video with English CC<br>2. Set target to Chinese | Accurate translation with correct characters and tone | ✅ |
| AE3 | Korean → English | 1. Open video with Korean CC<br>2. Set target to English | Accurate translation preserving meaning | ✅ |
| AE4 | English → Korean | 1. Open video with English CC<br>2. Set target to Korean | Accurate translation with correct honorifics | ✅ |
| AE5 | Japanese → English | 1. Open video with Japanese CC<br>2. Set target to English | Accurate translation with cultural context preserved | ✅ |
| AE6 | English → Japanese | 1. Open video with English CC<br>2. Set target to Japanese | Accurate translation with appropriate formality level | ✅ |

### 5. Asian Languages ↔ Asian Languages

| ID | Test Case | Steps | Expected Result | Status |
|----|-----------|-------|-----------------|--------|
| AA1 | Chinese → Japanese | 1. Open video with Chinese CC<br>2. Set target to Japanese | Accurate translation with correct Japanese grammar | ✅ |
| AA2 | Japanese → Chinese | 1. Open video with Japanese CC<br>2. Set target to Chinese | Accurate translation with correct characters | ✅ |
| AA3 | Korean → Chinese | 1. Open video with Korean CC<br>2. Set target to Chinese | Accurate translation preserving meaning | ✅ |
| AA4 | Chinese → Korean | 1. Open video with Chinese CC<br>2. Set target to Korean | Accurate translation with correct honorifics | ✅ |
| AA5 | Japanese → Korean | 1. Open video with Japanese CC<br>2. Set target to Korean | Accurate translation with appropriate formality | ✅ |
| AA6 | Korean → Japanese | 1. Open video with Korean CC<br>2. Set target to Japanese | Accurate translation with correct Japanese grammar | ✅ |

### 6. European Languages

| ID | Test Case | Steps | Expected Result | Status |
|----|-----------|-------|-----------------|--------|
| E1 | English → Spanish | 1. Open video with English CC<br>2. Set target to Spanish | Accurate translation with correct grammar and accents | ✅ |
| E2 | Spanish → English | 1. Open video with Spanish CC<br>2. Set target to English | Accurate translation preserving meaning | ✅ |
| E3 | English → French | 1. Open video with English CC<br>2. Set target to French | Accurate translation with correct grammar and accents | ✅ |
| E4 | French → English | 1. Open video with French CC<br>2. Set target to English | Accurate translation preserving meaning | ✅ |
| E5 | Spanish → French | 1. Open video with Spanish CC<br>2. Set target to French | Accurate translation between romance languages | ✅ |

## Error Handling Test Cases

### 7. Network and Service Errors

| ID | Test Case | Steps | Expected Result | Status |
|----|-----------|-------|-----------------|--------|
| N1 | Network disconnection | 1. Enable captions<br>2. Disconnect network<br>3. Continue video playback | Graceful error message; previous captions remain visible | ✅ |
| N2 | Slow network connection | 1. Throttle network speed<br>2. Enable bilingual captions | System adjusts batch size; captions appear with minimal delay | ✅ |
| N3 | Service unavailability | 1. Simulate API service outage<br>2. Attempt caption translation | Clear error message with retry option | ✅ |
| N4 | Rate limiting | 1. Generate excessive translation requests<br>2. Observe system behavior | Graceful handling with backoff strategy and user notification | ✅ |
| N5 | Recovery after error | 1. Trigger error condition<br>2. Restore normal conditions<br>3. Continue using extension | System recovers without requiring restart | ✅ |

### 8. Content Errors

| ID | Test Case | Steps | Expected Result | Status |
|----|-----------|-------|-----------------|--------|
| C1 | Missing source captions | 1. Open video without CC<br>2. Enable DeepSRT | Clear message indicating need for source captions | ✅ |
| C2 | Malformed caption data | 1. Use video with known caption errors<br>2. Enable bilingual captions | System handles malformed data gracefully | ✅ |
| C3 | Unsupported language | 1. Open video with rare language CC<br>2. Enable DeepSRT | Clear message about unsupported language | ✅ |
| C4 | Mixed language content | 1. Open video with mixed language speech<br>2. Enable bilingual captions | System handles language switches appropriately | ✅ |
| C5 | Special characters | 1. Open video with mathematical/scientific notation<br>2. Enable bilingual captions | Special characters preserved in translation | ✅ |

## Performance Test Cases

### 9. Resource Usage

| ID | Test Case | Steps | Expected Result | Status |
|----|-----------|-------|-----------------|--------|
| P1 | CPU usage | 1. Monitor CPU during caption processing<br>2. Play video for 10+ minutes | CPU usage remains below 15% of system resources | ✅ |
| P2 | Memory usage | 1. Monitor memory during extended use<br>2. Play multiple videos sequentially | No significant memory leaks; usage remains stable | ✅ |
| P3 | Battery impact (laptops) | 1. Measure battery drain rate with and without extension | Less than 10% additional battery consumption | ✅ |
| P4 | Network bandwidth | 1. Monitor network requests during caption processing | Efficient batching; minimal redundant requests | ✅ |
| P5 | Long video performance | 1. Test with 1+ hour video<br>2. Enable bilingual captions | Consistent performance throughout video duration | ✅ |

### 10. Responsiveness

| ID | Test Case | Steps | Expected Result | Status |
|----|-----------|-------|-----------------|--------|
| R1 | Initial caption load time | 1. Open video<br>2. Enable DeepSRT<br>3. Measure time to first caption | First captions appear within 2 seconds | ✅ |
| R2 | Language switch speed | 1. Change target language<br>2. Measure time until new language appears | New language captions appear within 1 second | ✅ |
| R3 | Seek performance | 1. Jump to different video positions<br>2. Measure caption update time | Captions update within 1 second after seek | ✅ |
| R4 | Concurrent video tabs | 1. Open multiple YouTube tabs with DeepSRT active<br>2. Test functionality in each | All tabs function correctly without interference | ✅ |
| R5 | Background tab behavior | 1. Enable captions<br>2. Switch to different browser tab<br>3. Return to YouTube | Captions continue functioning correctly | ✅ |

## Integration Test Cases

### 11. YouTube Interface Integration

| ID | Test Case | Steps | Expected Result | Status |
|----|-----------|-------|-----------------|--------|
| Y1 | YouTube CC button integration | 1. Toggle YouTube's CC button<br>2. Observe DeepSRT behavior | DeepSRT respects YouTube's CC state | ✅ |
| Y2 | YouTube language settings | 1. Change YouTube's caption language<br>2. Observe DeepSRT behavior | DeepSRT detects and adapts to YouTube's language change | ✅ |
| Y3 | YouTube theater mode | 1. Switch to theater mode<br>2. Enable bilingual captions | Captions position correctly in theater mode | ✅ |
| Y4 | YouTube fullscreen mode | 1. Switch to fullscreen<br>2. Enable bilingual captions | Captions position correctly in fullscreen | ✅ |
| Y5 | YouTube embed compatibility | 1. Test with embedded YouTube videos<br>2. Enable DeepSRT | Captions function correctly in embedded videos | ✅ |

### 12. Extension Integration

| ID | Test Case | Steps | Expected Result | Status |
|----|-----------|-------|-----------------|--------|
| E1 | Other caption extensions | 1. Install another caption extension<br>2. Enable both extensions | Clear priority handling without conflicts | ✅ |
| E2 | YouTube enhancer extensions | 1. Test with popular YouTube enhancers<br>2. Enable DeepSRT | Compatible operation without interference | ✅ |
| E3 | Browser theme compatibility | 1. Test with dark/light browser themes<br>2. Observe DeepSRT UI | UI adapts appropriately to browser theme | ✅ |
| E4 | Extension update behavior | 1. Trigger extension update<br>2. Continue using DeepSRT | Smooth update without disrupting active sessions | ✅ |
| E5 | Extension permissions | 1. Review required permissions<br>2. Verify each permission usage | Minimal permissions used only when necessary | ✅ |

## Regression Test Checklist

Before each release, verify that:

1. ✅ All previously supported language pairs continue to function
2. ✅ User preferences are preserved during updates
3. ✅ Performance remains consistent with previous versions
4. ✅ No new error conditions have been introduced
5. ✅ UI remains compatible with YouTube's latest interface

## Test Execution Guidelines

1. **Priority Order**: Execute tests in this order:
   - Functional basics (Section 1)
   - Error handling (Section 7-8)
   - Language pairs (Section 4-6)
   - Performance (Section 9-10)
   - Integration (Section 11-12)

2. **Test Environment Rotation**:
   - Test across multiple Chrome versions
   - Test on different operating systems
   - Test with various network conditions

3. **Documentation**:
   - Document all test results
   - Include screenshots of failures
   - Note browser console errors

4. **Regression Testing**:
   - Run full regression suite before each release
   - Prioritize tests for areas with code changes

## Conclusion

This test framework ensures comprehensive coverage of DeepSRT's bilingual caption system. By systematically executing these test cases, we can maintain high quality and reliability across all supported language combinations and usage scenarios.