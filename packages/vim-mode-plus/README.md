# vim-mode-plus [![Build Status](https://travis-ci.org/t9md/atom-vim-mode-plus.svg)](https://travis-ci.org/t9md/atom-vim-mode-plus)

vim-mode improved.

<!-- TOC START min:1 max:3 link:true update:true -->
- [vim-mode-plus](#vim-mode-plus)
- [What's new in v0.58.0](#whats-new-in-v0580)
- [Important](#important)
- [Thanks](#thanks)
- [Issue report](#issue-report)
- [Whats this?](#whats-this)
- [FAQ](#faq)
    - [Why fork? why not directly contribute to official vim-mode?](#why-fork-why-not-directly-contribute-to-official-vim-mode)
    - [In visual-block mode, some motion make editor slow, freeze.](#in-visual-block-mode-some-motion-make-editor-slow-freeze)
    - [ex-mode?](#ex-mode)
    - [Want to suppress autocomplete-plus's auto suggestion except insert-mode.](#want-to-suppress-autocomplete-pluss-auto-suggestion-except-insert-mode)
- [Wiki](#wiki)
- [Keymap](#keymap)
- [Helper packages](#helper-packages)
- [References](#references)
  - [Vim official](#vim-official)
  - [Other](#other)
- [Commit emoji convention](#commit-emoji-convention)

<!-- TOC END -->

# What's new in v0.58.0

In v0.58.0, introduce `preset-occurrence` and `persistent-selection`.
In v0.55.0, introduce `occurrence-modifier`

These features are very powerfull especially for power user, read folloiwng document to learn how to use.  

- [Advanced Topic Tutorial](https://github.com/t9md/atom-vim-mode-plus/wiki/AdvancedTopicTutorial)
- [Occurrence Modifier](https://github.com/t9md/atom-vim-mode-plus/wiki/OccurrenceModifier)
- [CHANGELOG.md](https://github.com/t9md/atom-vim-mode-plus/blob/master/CHANGELOG.md)

# Important

- **vim-mode-plus is replacement of vim-mode, you must disable vim-mode first to use vim-mode-plus**.
- You don't need following packages since it's built-in to vim-mode-plus.
  - [vim-surround](https://atom.io/packages/vim-surround)
  - [vim-mode-visual-block](https://atom.io/packages/vim-mode-visual-block)
- Scope for CSS selector and keymap is different from vim-mode, **not compatible**.
- Internal code base is very different. Thus, issue, PRs should be directly sent to vim-mode-plus. **DONT report vim-mode-plus's issue or PRs to official vim-mode.**

# Thanks

My work is greatly owing to former achievement done by original vim-mode developers and many of its contributors.  
As you can see in commit history, this project is originally started by forking official [vim-mode](https://github.com/atom/vim-mode).  
The great design to achieve Vim operation by composing operator with target(motion, text-object) on top of operationStack is still lives in vim-mode-plus now.  
I don't think I can find this idea by myself from nothing.  
Sincerely, I feel I couldn't do anything without original vim-mode.  

# Issue report

- Read [ISSUE_TEMPLATE](https://github.com/t9md/atom-vim-mode-plus/blob/master/ISSUE_TEMPLATE.md)

# Whats this?

Fork of [vim-mode](https://github.com/atom/vim-mode). Started at 2015.8.1.

- Many bug fixes.
- Refactoring: Rewritten almost every lines of codes.
- Highlight search
- visual-blockwise built-in
- Incremental search by `incrementalSearch` setting(disabled by default).
- Cursor visible in all visual-mode(characterwise, blockwise, linewise).
- Stay same cursor position after operate(e.g `y`, `gU`) by `stayOnYank`, `stayOnOperate` setting.(disabled by default)
- Lots of new motion like `move-up-to-edge`, `move-down-to-edge`.(No keymap by default)
- Surround built-in. Powerful AnyPair family(`change-surround-any-pair` operator, `inner-any-pair` text-object) to detect pair automatically.
- Set cursor position to start of change on undo or redo by enabling `setCursorToStartOfChangeOnUndoRedo`(enabled by default. Atom's default is end of change).
- Allow super granular keymap only effective when specific operation is pending like `yank-pending`, `delete-pending`. [#215](https://github.com/t9md/atom-vim-mode-plus/issues/215)
- And more...

# FAQ

Search [Q&A](https://github.com/t9md/atom-vim-mode-plus/issues?utf8=%E2%9C%93&q=label%3AQ%26A) label on issues.

### Why fork? why not directly contribute to official vim-mode?

- Changes are [too big](https://github.com/t9md/atom-vim-mode-plus/graphs/contributors).
- I felt many features are too experimental to merge to official vim-mode.

### In visual-block mode, some motion make editor slow, freeze.

Not freezing, its just VERY slow.  
You can workaround by disabling some keymap. See [#214](https://github.com/t9md/atom-vim-mode-plus/issues/214).

### ex-mode?

- Very immature package [vim-mode-plus-ex-mode](https://atom.io/packages/vim-mode-plus-ex-mode) is exists.
- My thought for ex-mode is [here #52](https://github.com/t9md/atom-vim-mode-plus/issues/52).

### Want to suppress autocomplete-plus's auto suggestion except insert-mode.

Set `suppressActivationForEditorClasses` autocomplete-plus's config to following value.

```
vim-mode-plus.normal-mode, vim-mode-plus.visual-mode, vim-mode-plus.operator-pending-mode, vim-mode-plus.insert-mode.replace
```

If you want to directly edit `config.cson`, here it is.

```coffeescript
"autocomplete-plus":
  suppressActivationForEditorClasses: [
    "vim-mode-plus.normal-mode"
    "vim-mode-plus.visual-mode"
    "vim-mode-plus.operator-pending-mode"
    "vim-mode-plus.insert-mode.replace"
  ]
```

# Wiki

- [TIPS](https://github.com/t9md/atom-vim-mode-plus/wiki/TIPS)
- [Commands](https://github.com/t9md/atom-vim-mode-plus/wiki/Commands) summary of vmp's commands with keymap.
- [Operations](https://github.com/t9md/atom-vim-mode-plus/wiki/Operations) includes most of commands with keymap information.
- [GIFs](https://github.com/t9md/atom-vim-mode-plus/wiki/GIFs) demonstrates fancy features.
- [Keymap example](https://github.com/t9md/atom-vim-mode-plus/wiki/Keymap-example).
- [Extend vmp in init file](https://github.com/t9md/atom-vim-mode-plus/wiki/Extend-vmp-in-init-file)
- [Create vmp plugin](https://github.com/t9md/atom-vim-mode-plus/wiki/Create-vmp-plugin)
- [List of vmp plugins](https://github.com/t9md/atom-vim-mode-plus/wiki/List-of-vmp-plugins)

# Keymap

vim-mode-plus have many advanced, experimental feature but most of it have no default keymap.  
If you want to use full power of vim-mode-plus, see and experiment each keymap, command in following links.  

- [Commands](https://github.com/t9md/atom-vim-mode-plus/wiki/Commands) summary of vmp's commands with keymap.
- [default keymaps](https://github.com/t9md/atom-vim-mode-plus/blob/master/keymaps/vim-mode-plus.cson)
- [Commands which have no default keymap](https://github.com/t9md/atom-vim-mode-plus/wiki/Commands-which-have-no-default-keymap)
- [my dotfiles](https://github.com/t9md/dotfiles)

# Helper packages

- [List of vmp plugins](https://github.com/t9md/atom-vim-mode-plus/wiki/List-of-vmp-plugins)

Below is list of my packages which provide more vim-like experience.  
Why I don't builtin these feature? Because it take more time and some feature is useful for non-vim user.

- [cursor-history](https://atom.io/packages/cursor-history)
provides <kbd>c-i</kbd>, <kbd>c-o</kbd> to go/back cursor position history.
- [open-this](https://atom.io/packages/open-this)
provides <kbd>gf</kbd> to open file under cursor.
- [clip-history](https://atom.io/packages/clip-history)
Not exist in pure Vim, provides clip-board history you can pop yanked text until you get result you want.
- [choose-pane](https://atom.io/packages/choose-pane)
Not exist in pure Vim, provide keyboard navigation of between panes/panels by choosing it by label.
- [paner](https://atom.io/packages/paner)
provides <kbd>ctrl-w H, J, K, L, x</kbd> to move pane.

# References

## Vim official
- [motion](http://vimhelp.appspot.com/motion.txt.html)
- [operator](http://vimhelp.appspot.com/motion.txt.html#operator)
- [text-object](http://vimhelp.appspot.com/motion.txt.html#object-select)
- [change](http://vimhelp.appspot.com/change.txt.html)
- [marks](http://vimhelp.appspot.com/motion.txt.html#mark-motions)
- [scroll](http://vimhelp.appspot.com/scroll.txt.html)
- [search-commands](http://vimhelp.appspot.com/pattern.txt.html#search-commands)

## Other
- [operator, the true power of Vim](http://whileimautomaton.net/2008/11/vimm3/operator) by kana.  
  True power of Vim is Operator and TextOjbect.

- [List of text-object as vim plugin](https://github.com/kana/vim-textobj-user/wiki)  
  vim-mode-plus builtin textobj for function, fold, entire, comment, indent, line, and any-pair(super set of many pair text-obj)

# Commit emoji convention

- :memo: Add comment or doc
- :gift: New feature.
- :bug: Bug fix
- :bomb: Breaking compatibility.
- :white_check_mark: Write test.
- :fire: Remove something.
- :beer: I'm happy like reduced code complexity.
