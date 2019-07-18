---
id: improvingux
title: 改进用户体验
---

## Configure text inputs
## 配置文本输入

在触屏手机中输入文本是一件具有挑战的事情，因为它的小屏幕， 软键盘。 但是基于你需要的数据，你可以配置文本输入让这个过程变得简单。

- 自动对焦( focus )第一个文本域
- 使用placeholder 作为预想的输入格式
- 启用 或者 禁用 自动大写 或者自动校正
- 选择键盘类型 \[例如 email, 数字(numeric)\]
- 确保回车按钮对焦到下一个域或者提交表单 
- 留意 [`TextInput` docs](textinput.md) 取得更多配置信息.

<video src="/react-native/img/textinput.mp4" muted autoplay loop width="320" height="430"></video>
[Try it on your phone](https://snack.expo.io/H1iGt2vSW)


Entering text on touch phone is a challenge - small screen, software keyboard. But based on what kind of data you need, you can make it easier by properly configuring the text inputs:

- Focus the first field automatically
- Use placeholder text as an example of expected data format
- Enable or disable autocapitalization and autocorrect
- Choose keyboard type (e.g. email, numeric)
- Make sure the return button focuses the next field or submits the form

Check out [`TextInput` docs](textinput.md) for more configuration options.

<video src="/react-native/img/textinput.mp4" muted autoplay loop width="320" height="430"></video>

[Try it on your phone](https://snack.expo.io/H1iGt2vSW)

## 键盘隐藏时的布局管理

软键盘几乎占用将近一般的手机屏幕。 如果你有会被软键盘覆盖的交互式组件，请使用[`KeyboardAvoidingView` component]以确保他们可以在打开键盘时可以被访问。
<video src="/react-native/img/keyboardavoidingview.mp4" muted autoplay loop width="320" height="448"></video>
[Try it on your phone](https://snack.expo.io/ryxRkwnrW)

## Manage layout when keyboard is visible

Software keyboard takes almost half of the screen. If you have interactive elements that can get covered by the keyboard, make sure they are still accessible by using the [`KeyboardAvoidingView` component](keyboardavoidingview.md).

<video src="/react-native/img/keyboardavoidingview.mp4" muted autoplay loop width="320" height="448"></video>

[Try it on your phone](https://snack.expo.io/ryxRkwnrW)

## 放大可触控区域
在手机上精准的点击一个按钮是很困难的一件事。 确保所有交互式元素大于等于44x44。 为元素保留足够空间的其中一种做法是，使用 `padding`, `minWidth` 和 `minHeight` 样式。 
或者， 可以使用 [`hitSlop` prop](touchablewithoutfeedback.md#hitslop)  无需影响布局来增加可交互区域。 这是一个演示：
<video src="/react-native/img/hitslop.mp4" muted autoplay loop width="320" height="120"></video>

[Try it on your phone](https://snack.expo.io/rJPwCt4HZ)

## Make tappable areas larger

On mobile phones it's hard to be very precise when pressing buttons. Make sure all interactive elements are 44x44 or larger. One way to do this is to leave enough space for the element, `padding`, `minWidth` and `minHeight` style values can be useful for that. Alternatively, you can use [`hitSlop` prop](touchablewithoutfeedback.md#hitslop) to increase interactive area without affecting the layout. Here's a demo:

<video src="/react-native/img/hitslop.mp4" muted autoplay loop width="320" height="120"></video>

[Try it on your phone](https://snack.expo.io/rJPwCt4HZ)


## 使用 Android Ripple
安卓 API 21+ 使用 material design Ripple 在用户点击屏幕上可交互区域的时候为用户提供反馈。 React Native 利用[`TouchableNativeFeedback` component](touchablenativefeedback.md) 实现了这个功能。 使用这个可触摸影响(touchable effect)取代 opacity 或者 highlight 通常会让您的应用程序更加切合平台。 尽管如此， 还是需要注意这个组件在 IOS 平台上 或者 Android API 小于21 的情况下无法工作的情况，所以你需要退而求其次，在IOS上使用其他的可触控组件，可以使用诸如 [react-native-platform-touchable](https://github.com/react-community/react-native-platform-touchable) 的组件解决平台差异。

## Use Android Ripple

Android API 21+ uses the material design ripple to provide user with feedback when they touch an interactable area on the screen. React Native exposes this through the [`TouchableNativeFeedback` component](touchablenativefeedback.md). Using this touchable effect instead of opacity or highlight will often make your app feel much more fitting on the platform. That said, you need to be careful when using it because it doesn't work on iOS or on Android API < 21, so you will need to fallback to using one of the other Touchable components on iOS. You can use a library like [react-native-platform-touchable](https://github.com/react-community/react-native-platform-touchable) to handle the platform differences for you.

<video src="/react-native/img/ripple.mp4" muted autoplay loop width="320"></video>

[Try it on your phone](https://snack.expo.io/SJywqe3rZ)

## 屏幕的旋转锁定
一般情况下 多屏幕(指的是横向和纵向) 会正常显示，除非你使用`Dimensions` API 并且 不处理 方向改变事件 (orientation changes)。 如果你不想做多屏幕方向支持，你可以锁定屏幕方向为 横向 或者纵向.
On iOS, in the General tab and Deployment Info section of Xcode enable the Device Orientation you want to support (ensure you have selected iPhone from the Devices menu when making the changes).（没了解过Xcode， 无法解读）
对于安卓， 打开 AndroidManifest.xml 文件 并且在 活动元素中添加 `'android:screenOrientation="portrait"'` 以锁定屏幕为纵向， 或者使用`'android:screenOrientation="landscape"'`锁定屏幕为横向。

## Screen orientation lock

Multiple screen orientations should work fine by default unless you're using `Dimensions` API and don't handle orientation changes. If you don't want to support multiple screen orientations, you can lock the screen orientation to either portrait or landscape.

On iOS, in the General tab and Deployment Info section of Xcode enable the Device Orientation you want to support (ensure you have selected iPhone from the Devices menu when making the changes). For Android, open the AndroidManifest.xml file and within the activity element add `'android:screenOrientation="portrait"'` to lock to portrait or `'android:screenOrientation="landscape"'` to lock to landscape.

# 了解更多

[Material Design](https://material.io/) 和 [Human Interface Guidelines](https://developer.apple.com/ios/human-interface-guidelines/overview/design-principles/) 是学习移动设计的非常优秀的资源。

# Learn more

[Material Design](https://material.io/) and [Human Interface Guidelines](https://developer.apple.com/ios/human-interface-guidelines/overview/design-principles/) are great resources for learning more about designing for mobile platforms.
