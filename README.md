# TDLikertScaleSelectorView

[![Build Status](http://img.shields.io/travis/elprl/TDLikertScaleSelectorView/master.svg?style=flat)](https://travis-ci.org/elprl/TDLikertScaleSelectorView)

This library provides a UI Control for displaying a Likert Scale question

[![](https://github.com/elprl/TDLikertScaleSelectorView/raw/master/screenshot.png)](https://github.com/elprl/TDLikertScaleSelectorView/raw/master/screenshot.png)

## Features

- [x] Ability to ask a Likert Scale question
- [x] Ability to select an answer - strongly agree, agree, neutral, disagree or strong disagree
- [x] Ability to skin the UI with fonts, colours, etc
- [x] Ability to add the control via Interface Builder or programmatically

## Requirements

- iOS 11.0 or later
- macOS 10.13 or later
- Xcode 10 beta 4 or later

## How To Use
The `TDLikertScaleSelectorView` class is the main UIView class containing the answer options / selections. You can add the UIView through code as shown below, or through Interface Builder. Implement a concrete class or struct of the `TDSelectionBuildConfig` protocol to skin / theme the controls to your needs.

```swift
import TDLikertScaleSelectorView

struct MyBuildConfig: TDSelectionBuildConfig {
    var font: UIFont? = UIFont.systemFont(ofSize: 15)
    var textColor: UIColor?  = UIColor.purple
    var backgroundColorNormal: UIColor? = UIColor.clear
    var backgroundColorHighlighted: UIColor? = UIColor.lightGray
    var backgroundColorSelected: UIColor? = UIColor.red
    var backgroundColorHighlightedSelected: UIColor? = UIColor.lightGray
    var borderColor: UIColor? = .purple
    var borderWidth: CGFloat? = 2.0
    var buttonRadius: CGFloat? = 22
    var lineColor: UIColor? = .purple
}
    
if let likertView = TDLikertScaleSelectorView(withConfig: config, frame: CGRect.zero) {
    likertView.delegate = self
    likertView.tag = 1 // could be question number
    self.view.addSubview(likertView)
}

extension ViewController: TDLikertScaleDelegate {
    func didSelect(category cat: TDSelectionCategory, tag: Int) {
        print("Question with tag \(tag) has answer \(cat.localizedName)")
    }
}

```
