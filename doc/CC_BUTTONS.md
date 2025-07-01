# CC Buttons Priority & User Control Principles

This document defines the design guidelines for user control principles around caption buttons and the interaction between extension and native caption systems.

## Terminology
- **Native CC**: The CC button on the YouTube player (YouTube's native captions)
- **Extension CC**: The CC button on the extension side panel (DeepSRT's caption system)
- **Perfect Language Match**: When user's preferred language matches video's native caption language (e.g., zh-tw user watching zh-tw content)

## Core User Control Principle

> **When user explicitly toggles extension CC, they should have full control over native CC and extension won't hide native CCs.**

## Control States & Behaviors

### **Extension CC ON (Programmatic)**
- **Extension can manage native CC** for optimal experience
- **Enable native CC** for perfect language matches (better performance)
- **Disable native CC** when live translation is needed (avoid conflicts)
- **Clean up programmatic changes** when navigating between videos
- **Respect user override** if user takes explicit control

**Example Scenarios:**
```
zh-tw user + zh-tw video → Extension enables native CC (optimal performance)
zh-tw user + English video → Extension disables native CC (uses translation)
Navigation cleanup → Extension removes its programmatic changes only
```

### **Extension CC OFF (User Explicit)**
- **Extension completely hands off control** to the user
- **User has full control** over native CC state
- **Extension never interferes** with native CC when user disabled extension
- **No programmatic changes** to native CC state
- **Sidebar continues working** independently for transcript display

**Example Scenarios:**
```
User toggles Extension CC OFF → Extension backs off completely
User controls Native CC → Extension respects all user choices
User toggles Native CC ON/OFF → Extension never interferes
```

### **Native CC User Interaction**
- **Once user touches native CC button**, extension backs off permanently for that session
- **User preference takes precedence** over extension optimization logic
- **Extension tracks user intent** via MutationObserver on native CC button
- **No cleanup of user changes** during navigation
- **Extension optimization disabled** until page reload

**Example Scenarios:**
```
Extension enables Native CC → User clicks Native CC button → Extension backs off
User manually controls Native CC → Extension never interferes again
Navigation with user control → Extension preserves user's explicit choices
```

## Implementation Details

### User Intent Tracking
```javascript
// Track explicit user actions
this.userExplicitlyDisabledExtCC = false;      // User turned OFF extension CC
this.userExplicitlyControlledNativeCC = false; // User touched native CC button  
this.programmaticallyEnabledNativeCC = false;  // Extension enabled native CC
```

### Control Decision Logic
```javascript
shouldRespectUserControl() {
  // Don't interfere if user has taken explicit control
  return this.userExplicitlyDisabledExtCC || this.userExplicitlyControlledNativeCC;
}
```

### Navigation Cleanup
```javascript
// Clean up only programmatic changes, preserve user choices
if (this.programmaticallyEnabledNativeCC && !this.userExplicitlyControlledNativeCC) {
  // Remove extension's programmatic changes only
  cleanupProgrammaticChanges();
}
```

## Behavior Matrix

| Extension CC | Native CC | User Action | Extension Behavior | Result |
|-------------|-----------|-------------|-------------------|---------|
| ON (Auto) | OFF | None | Enable Native CC | Native captions show (optimal) |
| ON (Auto) | ON | None | Leave as-is | Native captions continue |
| OFF (User) | OFF | User disabled Ext | No interference | User controls Native CC |
| OFF (User) | ON | User disabled Ext | No interference | Native captions continue |
| ON (Auto) | OFF→ON | User clicked Native | Back off permanently | User has full control |
| ON (Auto) | ON→OFF | User clicked Native | Back off permanently | User has full control |

## Navigation Scenarios

### Scenario 1: Perfect Match Navigation
```
Video A (zh-tw) → Extension enables Native CC → Video B (English)
Result: Extension cleans up Native CC, enables translation
```

### Scenario 2: User Control Navigation  
```
Video A → User controls Native CC → Video B → Extension preserves user choice
Result: User's explicit Native CC state maintained across navigation
```

### Scenario 3: Mixed Control Navigation
```
Video A → Extension optimizes → User takes control → Video B
Result: Extension backs off, user retains full control
```

## Performance Considerations

### Native CC Advantages (Perfect Match)
- **Hardware-accelerated rendering** via YouTube's optimized system
- **Lower CPU usage** compared to custom subtitle overlay
- **Better battery life** on mobile devices
- **Native user experience** with YouTube's caption styling

### Extension Overlay Advantages (Translation)
- **Live translation capability** for non-matching languages
- **Custom styling options** and positioning
- **Bilingual display support** when needed
- **Independent of YouTube's caption availability**

## Error Handling & Edge Cases

### YouTube API Unavailable
```javascript
// Fallback to button click if YouTube API not available
if (typeof player.toggleSubtitles !== 'function') {
  // Use direct button interaction
  captionsButton.click();
}
```

### Button Not Found
```javascript
// Graceful degradation if native CC button not available
if (!captionsButton) {
  console.warn('Native CC button not found - using extension overlay');
  // Fall back to extension's subtitle system
}
```

### User Control Detection Failure
```javascript
// Conservative approach - respect user if detection uncertain
if (uncertainUserIntent) {
  // Default to user control, don't interfere
  this.userExplicitlyControlledNativeCC = true;
}
```

## Testing Scenarios

### Manual Test Cases
1. **Perfect Match Optimization**: zh-tw user + zh-tw video → Native CC enabled
2. **Translation Mode**: zh-tw user + English video → Extension overlay used  
3. **User Override**: Extension optimizes → User clicks Native CC → Extension backs off
4. **Navigation Cleanup**: Perfect match → Translation video → Native CC cleaned up
5. **User Control Persistence**: User controls Native CC → Navigate → Choice preserved
6. **Extension Toggle**: User disables Extension CC → Full native control

### Automated Test Scenarios
- Monitor `userExplicitlyDisabledExtCC` flag changes
- Track `userExplicitlyControlledNativeCC` via MutationObserver
- Verify `programmaticallyEnabledNativeCC` cleanup on navigation
- Test `shouldRespectUserControl()` decision logic

## Future Considerations

### Potential Enhancements
- **Session persistence** of user control preferences
- **Per-video user preferences** storage
- **Advanced user intent detection** via interaction patterns
- **Accessibility improvements** for caption control

### Backward Compatibility
- **Existing user workflows** remain unchanged
- **Default behavior** maintains current functionality
- **Progressive enhancement** of user control features
- **Graceful degradation** for unsupported scenarios

---

*This document reflects the current implementation of user control principles in DeepSRT's caption management system. Updates should be made when behavior changes or new scenarios are identified.*
