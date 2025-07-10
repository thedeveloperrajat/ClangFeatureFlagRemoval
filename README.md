# ClangFeatureFlagRemoval

Feature Flag is a way to allow certain section of code to be skipped or allowed to be run when a certain feature is on or off. This allows to flexibly and iteratively add our code without altering the current behavior and also check the new code behavior by just turning on the feature. This also gives developers enough time and confidence to be ready for shipping the feature and test the feature and only ship when the feature is well tested.

This repository aims to detect feature control code patterns in a project and cleanup the existing code. This is done by Clang to detect such patterns in the code and ensures that the new code logic is not altered and we have eliminated the feature control.

For example:

### Example 1

Input Code:

```cpp
const bool isFeatureOn;

if(isFeatureOn && isSomethingActive) {
    // Placeholder Code
}
```

Output Code:

```cpp
const bool isFeatureOn;

if(isSomethingActive) {
    // Placeholder Code
}
```

### Example 2

Input Code:

```cpp
const bool isFeatureOn;

if(!isFeatureOn && isSomethingActive) {
    // Placeholder Code 1
}

// Placeholder Code 2

```

Output Code:

```cpp

// Placeholder Code 2

```
