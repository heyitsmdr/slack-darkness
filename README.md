# slack-darkness
A dark theme for Slack.

This theme is based on the following Gist:

https://gist.github.com/a7madgamal/c2ce04dde8520f426005e5ed28da8608

## Mac Installation

Open the following file:

```
/Applications/Slack.app/Contents/Resources/app.asar.unpacked/src/static/ssb-interop.js
```

Append the following to the bottom:

```
function getAndAppend(url) {
  $.ajax({
    url: url + '?ts=' + Date.now(),
    success: function(css) {
      $("<style></style>").appendTo('head').html(css);
      
    }
  });
}

document.addEventListener('DOMContentLoaded', function() {
  getAndAppend('https://raw.githubusercontent.com/heyitsmdr/slack-darkness/master/styles/base.css')
  getAndAppend('https://raw.githubusercontent.com/heyitsmdr/slack-darkness/master/styles/theme.css')
});
```

> Note: You will need to do this every time Slack is updated, since this file will be overriden.
> An automated method is coming soon.

## Improvements

Please feel free to create a PR. Only modify the `theme.css` file, as the `base.css` file is what this theme derived from, which should remain untouched.
