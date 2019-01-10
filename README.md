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
document.addEventListener('DOMContentLoaded', function() {
  $.ajax({
    url: 'https://raw.githubusercontent.com/heyitsmdr/slack-darkness/master/generated/theme.css?ts=' + Date.now(),
    success: function(css) {
      $("<style></style>").appendTo('head').html(css);
    }
  });
});
```

> Note: You will need to do this every time Slack is updated, since this file will be overriden.
> An automated method is coming soon.

## Development

Please feel free to create a PR and contribute!

### Testing Changes

It's easiest to go to your Slack workplace in Chrome and open the Chrome 
Developer Tools. You can paste the following in the console to start working on styling locally:

```
$('<link href="http://127.0.0.1:8080/theme.css" rel="stylesheet" type="text/css" id="slack-darkness-css">').appendTo('head');
setInterval(function(){ $("#slack-darkness-css")[0].href = "http://127.0.0.1:8080/theme.css?ts=" + Date.now() }, 1000);
```

This will load the LESS-generated stylesheet locally and refresh it every second to allow your changes to show up near-immediately.
