# Clickable URLs

<a href='https://ko-fi.com/X8X19BQH' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://az743702.vo.msecnd.net/cdn/kofi1.png?v=0' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

A plugin for [Sublime Text 2 and 3](http://sublimetext.com)

![Screenshot of a clickable URL](https://raw.github.com/leonid-shevtsov/ClickableUrls_SublimeText2/master/screenshot.png)

**Breaking change! The `open_url` command is named `open_url_under_cursor` since v1.3.0 to avoid conflict with the built-in command with the same name. Please update your configuration if you've made custom bindings.**

## Summary

This plugin underlines URLs in Sublime Text, and lets you open them with a keystroke (`Cmd+Option+Enter` by default).

After you put the cursor over an URL, you can either hit `Cmd+Option+Enter` (`Ctrl+Alt+Enter` on Windows & Linux), or select "Open URL under cursor" from the Command Palette. Instead of selecting an auto detected URL, you can select any block of text and it will also open in a browser as a URL.

If you actually want to use a mouse+key combination to open URLs, you'll have to part with one of the selection modes (likely the Option-selection, which is rectangular block selection and is not used very often). See [this issue](https://github.com/leonid-shevtsov/ClickableUrls_SublimeText2/issues/2) for details and examples on how to do it. Unfortunately Sublime Text's API is not flexible with mouse bindings.

There is also an "Open all URLs" command, which opens all URLs found in the current document.

**Performance warning.** The plugin is automatically disabled if the document has more than 200 URLs, in order to avoid a massive performance hit. To change this number, set the `max_url_limit` option (see "Configuration" below).


## Installation

### By Package Control

1. Download & Install **`Sublime Text 3`** (https://www.sublimetext.com/3)
1. Go to the menu **`Tools -> Install Package Control`**, then,
    wait few seconds until the installation finishes up
1. Now,
    Go to the menu **`Preferences -> Package Control`**
1. Type **`Add Channel`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
    input the following address and press <kbd>Enter</kbd>
    ```
    https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json
    ```
1. Go to the menu **`Tools -> Command Palette...
    (Ctrl+Shift+P)`**
1. Type **`Preferences:
    Package Control Settings – User`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
    find the following setting on your **`Package Control.sublime-settings`** file:
    ```js
    "channels":
    [
        "https://packagecontrol.io/channel_v3.json",
        "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
    ],
    ```
1. And,
    change it to the following, i.e.,
    put the **`https://raw.githubusercontent...`** line as first:
    ```js
    "channels":
    [
        "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
        "https://packagecontrol.io/channel_v3.json",
    ],
    ```
    * The **`https://raw.githubusercontent...`** line must to be added before the **`https://packagecontrol.io...`** one, otherwise,
      you will not install this forked version of the package,
      but the original available on the Package Control default channel **`https://packagecontrol.io...`**
    > [!WARNING]
    > Placing this custom channel before the default channel changes Package Control's resolution globally.
    > Packages from this channel with the same name will override versions from the default channel.
    >
    > You can review the channel contents here:
    > https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json
1. Now,
    go to the menu **`Preferences -> Package Control`**
1. Type **`Install Package`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
    search for **`ClickableURLs`** and press <kbd>Enter</kbd>

See also:

1. [ITE - Integrated Toolset Environment](https://github.com/evandrocoan/ITE)
1. [Package control docs](https://packagecontrol.io/docs/usage) for details.


## Configuration

All configuration is done via the settings file that you can open via the main menu: `Preferences > Package Settings > Clickable URLs > Settings - User`.

To rebind mouse keys, open `Preferences > Package Settings > Clickable URLs > Mouse Bindings - User`

### Customising the browser

By default, Clickable URLs uses some default system browser. If it doesn't work for you, you can change the browser by setting the `clickable_urls_browser` in the `ClickableUrls.sublime-settings`
file, to which you can get from the menu.

Anything from [this list](https://docs.python.org/2/library/webbrowser.html#webbrowser.register) will work, for example:

    {
        "clickable_urls_browser": "firefox"
    }

**Note for Windows users.** If the browser you want won't open, you might have to specify the full path manually:

    {
        "clickable_urls_browser": "\"c:\\program files\\mozilla firefox\\firefox.exe\" %s &"
    }

Take note of the escaped slashes and the quoting around the name.

The ampersand at the end is significant - without it the editor will hang and wait for browser to close.

### Disabling URL highlighting

Unfortunately, the only way to underline a block of text in Sublime Text 2 is a hack with underlining empty regions, and there is no way to control its appearance. If you want, you can disable URL highlighting by setting the option `highlight_urls` to false.

    {
        "highlight_urls": false
    }

Note that this isn't an issue with Sublime Text 3.

## Known Issues

* URLs are not underlined in Markdown files when using the [MarkdownEditing plugin](https://github.com/SublimeText-Markdown/MarkdownEditing) plugin (that plugin applies its own styles to the URLs). Otherwise ClickableUrls works as usual.

---

(c) 2015 [Leonid Shevtsov](http://leonid.shevtsov.me) under the MIT license.
