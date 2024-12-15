# Expo DocumentPicker: Android Null Uri Bug

This repository demonstrates a bug in the Expo DocumentPicker API on Android where the promise resolves with a null `uri` after file selection.  The issue occurs inconsistently, making debugging difficult.

## Bug Description

The `DocumentPicker.getDocumentAsync()` method on Android sometimes resolves its promise with an object where the `uri` property is null. This happens even when the user successfully selects a file.  The rest of the object (e.g., `name`, `type`) may be populated correctly. This leads to errors when the application attempts to access or use the null `uri`.

## Reproduction Steps

1. Run the `bug.js` example on an Android device or emulator.
2. Select a file using the DocumentPicker.
3. Observe that the `uri` is sometimes null, even after a successful file selection.  The probability of observing this varies depending on the device and potentially other factors.

## Solution

The `bugSolution.js` file demonstrates a possible workaround using error handling.  We add a check to handle the case where `uri` is null, preventing crashes but potentially requiring an alternative approach in your app's logic if a file selection is critical.