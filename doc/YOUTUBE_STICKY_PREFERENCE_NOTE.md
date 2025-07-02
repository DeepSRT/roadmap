# YouTube Sticky Language Preference - Important User Note

## The Issue

YouTube maintains its own **sticky language preference system** that can interfere with DeepSRT's automatic caption selection. This means when you change your language preference in the DeepSRT extension, YouTube's native captions might not automatically select the language you expect.

## What You Might See

### Example Scenario:
1. **Your DeepSRT setting**: Korean (ko)
2. **Video content**: Korean video with Korean captions available
3. **Expected behavior**: Korean native captions should appear
4. **Actual behavior**: You see "Korean (auto-translated) → Chinese (Traditional)" or another unexpected language

## Why This Happens

YouTube remembers your **previous caption language choice** across videos and sessions. Even when DeepSRT detects a perfect language match and tries to enable the correct native captions, YouTube's sticky preference can override this selection.

### Technical Details:
- YouTube stores caption language preferences in browser storage
- This preference persists across video navigation
- DeepSRT's automatic selection may be overridden by YouTube's sticky preference
- The issue is most noticeable when switching between different language preferences

## Simple Solution

### **One-Time Manual Reset**
When you notice incorrect caption language selection:

1. **Click the CC button** on the YouTube player (bottom right)
2. **Click the Settings gear** → **Subtitles/CC**
3. **Manually select your preferred native language** (e.g., "Korean" instead of "Korean (auto-translated)")
4. **Close the settings menu**

This **resets YouTube's sticky preference** to your desired language.

### **After the Reset**
- Future videos in the same language should automatically select correctly
- DeepSRT's perfect match optimization will work as expected
- No need to repeat this process unless you switch to a different language preference

## Prevention Tips

### **For Consistent Experience:**
1. **Set your browser language** to match your DeepSRT preference
2. **Use YouTube's language setting**: Profile → Settings → Language
3. **Add language parameter to URLs**: `&hl=ko` for Korean, `&hl=zh-tw` for Traditional Chinese

### **When Switching Languages in DeepSRT:**
- Expect to manually select native captions **once** for the new language
- After the manual selection, automatic selection should work correctly
- This is a YouTube limitation, not a DeepSRT bug

## Technical Background

### **Why DeepSRT Can't Always Override This**
- YouTube's sticky preference is deeply integrated into the player
- Direct caption toggling (DeepSRT's fastest method) respects YouTube's preference
- Menu-based selection can override it, but is slower and more disruptive
- DeepSRT prioritizes speed and user experience over perfect language selection

### **DeepSRT's Optimization Trade-off**
- **Accepts**: YouTube's sticky preference for faster performance
- **Gains**: 15-25x faster caption enabling, zero menu operations
- **Rationale**: Speed and smooth UX are more valuable than perfect language selection

## Summary

**This is expected behavior** due to YouTube's design, not a DeepSRT malfunction. The one-time manual selection is a small trade-off for the significant performance improvements DeepSRT provides in perfect match scenarios.

**Remember**: After manually selecting your preferred language once, DeepSRT's automatic selection should work correctly for subsequent videos in that language.
