# VS Code

## Extensions

Here's a list of useful extensions. Open them in VS Code Marketplace or check the "Recommended extensions" tab in VS Code.

- [DotENV](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv)
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Even Better TOML](https://marketplace.visualstudio.com/items?itemName=tamasfe.even-better-toml)
- [GitHub Actions](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-github-actions)
- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- [Mustache](https://marketplace.visualstudio.com/items?itemName=dawhite.mustache)
- [PHP Intelephense](https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

## Profile settings & key bindings

You can import/export different profiles in VS Code but it's kind of buggy on macOS and VS Code defaults back to the default profile every time you restart VS Code (bug?). So for that reason, we are replacing our default settings instead of importing a new profile, so we don't have switch profile all the time.

1. Open VS Code with your default profile active and open settings `cmd + ,`.
1. Search for the setting to show settings as json instead of ui: `"workbench.settings.editor": "json"`.
1. Open your settings again but this time it should open in json format.
1. Copy and paste the contents of [settings.json](settings.json) to your settings.json in VS Code and save.
1. Open Settings -> Keyboard Shortcuts in VS Code and click the icon in the upper right to show keybindings as json format instead of ui.
1. Copy and paste the contents of [keybindings.json](keybindings.json) to your keybindings.json in VS Code and save.
