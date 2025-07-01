# DeepSRT Regression Testing Checklist

This document provides a comprehensive regression testing checklist for DeepSRT releases. It ensures that all critical functionality continues to work correctly after code changes and before new versions are released.

## Pre-Release Testing Process

### 1. Environment Setup

- [ ] Test on Chrome latest stable version
- [ ] Test on Chrome beta version
- [ ] Test on Windows 10/11
- [ ] Test on macOS latest
- [ ] Test on Linux (Ubuntu)
- [ ] Test with various network conditions (fast, slow, intermittent)

### 2. Core Functionality

#### Bilingual Caption System

- [ ] Caption detection works for all supported video types
- [ ] Bilingual captions display correctly for all language pairs
- [ ] Caption timing is synchronized with video content
- [ ] Caption formatting is consistent and readable
- [ ] Caption toggle respects YouTube's CC button state
- [ ] Captions persist when navigating within the video
- [ ] Captions update correctly when seeking to different positions

#### Language Support

- [ ] All language pairs in the support matrix function correctly
- [ ] Chinese variants (zh-CN, zh-TW, zh-HK) are handled properly
- [ ] Language auto-detection works correctly
- [ ] Language preferences are preserved between sessions
- [ ] Language switching is responsive and accurate
- [ ] Default language selection based on browser settings works

#### User Interface

- [ ] Sidebar displays and functions correctly
- [ ] Language selection dropdowns populate completely
- [ ] Active languages are clearly indicated
- [ ] Font size adjustments work as expected
- [ ] UI is responsive across different window sizes
- [ ] Dark/light mode compatibility is maintained
- [ ] All buttons and controls are clickable and functional

### 3. Error Handling

- [ ] Graceful handling of network disconnection
- [ ] Clear error messages for service unavailability
- [ ] Recovery after temporary errors without requiring restart
- [ ] Appropriate handling of videos without captions
- [ ] Batch processing errors (400 errors) are prevented
- [ ] Rate limiting is handled with appropriate backoff
- [ ] Unsupported languages trigger helpful user messages

### 4. Performance Metrics

- [ ] CPU usage remains below 15% during normal operation
- [ ] Memory usage is stable during extended use
- [ ] Initial caption load time is under 2 seconds
- [ ] Language switching completes within 1 second
- [ ] Seek operations update captions within 1 second
- [ ] Multiple video tabs function without performance degradation
- [ ] Long videos (1+ hour) maintain consistent performance

### 5. Integration Points

- [ ] YouTube player controls integration works correctly
- [ ] YouTube theater mode displays captions properly
- [ ] YouTube fullscreen mode displays captions properly
- [ ] Embedded YouTube videos are supported
- [ ] Compatible with other popular YouTube extensions
- [ ] Extension updates do not disrupt active sessions
- [ ] Permission usage is minimal and appropriate

### 6. Language-Specific Tests

#### English ↔ Asian Languages

- [ ] English → Chinese translation is accurate
- [ ] Chinese → English translation is accurate
- [ ] English → Korean translation is accurate
- [ ] Korean → English translation is accurate
- [ ] English → Japanese translation is accurate
- [ ] Japanese → English translation is accurate

#### Asian Languages ↔ Asian Languages

- [ ] Chinese → Japanese translation is accurate
- [ ] Japanese → Chinese translation is accurate
- [ ] Korean → Chinese translation is accurate
- [ ] Chinese → Korean translation is accurate
- [ ] Japanese → Korean translation is accurate
- [ ] Korean → Japanese translation is accurate

#### European Languages

- [ ] English → Spanish translation is accurate
- [ ] Spanish → English translation is accurate
- [ ] English → French translation is accurate
- [ ] French → English translation is accurate
- [ ] Spanish → French translation is accurate

### 7. User Preference Tests

- [ ] User language preferences are preserved after updates
- [ ] User interface preferences are maintained
- [ ] Font size preferences are respected
- [ ] Sidebar state persistence works correctly
- [ ] Programmatic vs. user actions are distinguished correctly
- [ ] Explicit user selections are always prioritized

## Regression Test Execution

### Test Documentation

For each test case:

1. **Status**: Pass/Fail
2. **Version tested**: x.x.x
3. **Environment**: OS, Chrome version
4. **Date executed**: YYYY-MM-DD
5. **Tester**: Name
6. **Notes**: Any observations or issues

### Critical Path Testing

These tests must pass for any release:

1. **Basic caption functionality** - Captions display correctly for all language pairs
2. **Language switching** - Changing languages works correctly
3. **Error recovery** - System recovers from network/service disruptions
4. **Performance stability** - No resource leaks or performance degradation
5. **YouTube integration** - Works with YouTube's latest interface

### Automated Testing Components

- [ ] Unit tests for core functions pass at 100%
- [ ] Integration tests for API communication pass
- [ ] UI component tests verify correct rendering
- [ ] Performance benchmarks meet or exceed previous version
- [ ] Security checks pass without warnings

## Release Approval Checklist

Before finalizing a release:

- [ ] All critical path tests pass
- [ ] No high-priority bugs remain unfixed
- [ ] Performance meets or exceeds previous version
- [ ] Documentation is updated to reflect changes
- [ ] Release notes accurately describe changes
- [ ] Version numbers are updated in all relevant files
- [ ] Final review by QA lead completed

## Post-Release Monitoring

After release:

- [ ] Monitor error rates in production
- [ ] Track user feedback for unexpected issues
- [ ] Verify analytics for feature usage
- [ ] Check performance metrics against baseline
- [ ] Prepare hotfix plan if critical issues emerge

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2025-07-15 | Initial checklist creation |
| 1.5.2 | 2025-07-15 | Updated for bilingual caption system |

---

This regression checklist should be reviewed and updated with each major release to ensure it covers all critical functionality.