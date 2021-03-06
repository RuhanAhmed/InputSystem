    ////WIP

# Keyboard Support

A keyboard is defined as a device with a set of keys defined by the `Key` enumeration.

The location of individual keys is agnostic to keyboard layout meaning that, for example, the `A` key is always the key to the right of the `Caps Lock` key regardless of where the currently active language layout places the key that generates an `A` character (if the layout even has a key assigned to that character).

To query which (if any) character is generated by given key, use the key's `displayName` property. The value of the property will change automatically when the keyboard layout is changed at the system level.

Keys can be looked up by their produced character using [control paths](Controls.md#control-paths). For example, the key producing the "a" character can be queried from `Keyboard` using `Keyboard.current["#(a)"]`. Alternatively, one can simple loop through the keys on the keyboard and select a key by `displayName`.

```CSharp
    Keyboard.current.allChildren.FirstOrDefault(x => x.displayName == "a")
```

## Controls

A given key can be retrieved from `Keyboard` using either one of the accessor properties (e.g. `Keyboard.spaceKey`) or using `Keyboard`'s indexer and the `Key` enumeration (e.g. `keyboard[Key.Space]`.

|Control|Description|
|-------|-----------|
|`enterKey`|Enter/return key on right side |
|`tabKey`|Tab key on the left side of the keyboard, right above `capsLockKey`.|
|`backquoteKey`||
|`semicolonKey`||
|`commaKey`||
|`periodKey`||
|`slashKey`||
|`backslashKey`||
|`leftBracketKey`||
|`rightBracketKey`||
|`minusKey`||
|`equalsKey`||
|`aKey`||
|`bKey`||
|`cKey`||
|`dKey`||
|`eKey`||
|`dKey`||
|`eKey`||
|`fKey`||
|`kKey`||
|`hKey`||
|`iKey`||
|`jKey`||
|`kKey`||
|`lKey`||
|`mKey`||
|`nKey`||
|`oKey`||
|`pKey`||
|`qKey`||
|`rKey`||
|`sKey`||
|`tKey`||
|`uKey`||
|`vKey`||
|`wKey`||
|`xKey`||
|`yKey`||
|`zKey`||
|`digit1Key`||
|`digit2Key`||
|`digit3Key`||
|`digit4Key`||
|`digit5Key`||
|`digit6Key`||
|`digit7Key`||
|`digit8Key`||
|`digit9Key`||
|`digit0Key`||
|`leftShiftKey`||
|`rightShiftKey`||
|`leftAltKey`||
|`rightAltKey`||
|`leftCtrlKey`||
|`rightCtrlKey`||
|`leftMetaKey`||
|`rightMetaKey`||
|`leftWindowsKey`||
|`rigthWindowsKey`||
|`leftAppleKey`||
|`rightAppleKey`||
|`leftCommandKey`||
|`rightCommandKey`||
|`contextMenuKey`||
|`escapeKey`||
|`leftArrowKey`||
|`rightArrowKey`||
|`upArrowKey`||
|`downArrowKey`||
|`backspaceKey`||
|`pageDownKey`||
|`pageUpKey`||
|`homeKey`||
|`endKey`||
|`insertKey`||
|`deleteKey`|
|`capsLockKey`||
|`scrollLockKey`||
|`numLockKey`||
|`printScreenKey`||
|`pauseKey`||
|`numpadEnterKey`||
|`numpadDivideKey`||
|`numpadMultiplyKey`||
|`numpadMinusKey`||
|`numpadPlusKey`||
|`numpadPeriodKey`||
|`numpadEqualsKey`||
|`numpad0Key`||
|`numpad1Key`||
|`numpad2Key`||
|`numpad3Key`||
|`numpad4Key`||
|`numpad5Key`||
|`numpad6Key`||
|`numpad7Key`||
|`numpad8Key`||
|`numpad9Key`||
|`f1Key`||
|`f2Key`||
|`f3Key`||
|`f4Key`||
|`f5Key`||
|`f6Key`||
|`f7Key`||
|`f8Key`||
|`f9Key`||
|`f10Key`||
|`f11Key`||
|`f12Key`||
|`oem1Key`||
|`oem2Key`||
|`oem3Key`||
|`oem4Key`||
|`oem5Key`||

## Text Input

It is recommended to not manually translate text input from key presses by trying to trying to string together the characters corresponding to the keys. Instead, to listen to text input, hook into `Keyboard.onTextInput`. This will deliver character-by-character input as reported by the platform (including input from on-screen keyboards).

Note that the text input API does not allocate GC memory as it does not deliver fully composed strings.

## Keyboard Layouts

The name of the current keyboard layout can be queried with `Keyboard.keyboardLayout`. Note that the names are platform-specific.

There is no support for setting keyboard layouts from the application.

To monitor for when the keyboard layout changes, hook into `InputSystem.onDeviceChange` and check for `InputDeviceChange.ConfigurationChanged` on a `Keyboard` device.

## IME

## On-Screen Keyboards

We do not yet support on-screen keyboards in the new input system. For now, please Unity's existing API in `UnityEngine.TouchScreenKeyboard`.
