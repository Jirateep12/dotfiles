💻 vscode

- download extensions : [extensions vscode for me](https://drive.google.com/file/d/1dnew8LJA01ajWTVBnLsF3WFndv9ajL2r/view?usp=sharing)

```jsonc
{
	// workbench
	"workbench.iconTheme": "material-icon-theme",
	"workbench.colorTheme": "Halcyon",
	"workbench.startupEditor": "none",
	"workbench.list.smoothScrolling": true,
	// editor
	"editor.renderWhitespace": "boundary",
	"editor.fontFamily": "Hack NF",
	"editor.cursorStyle": "line",
	"editor.tabSize": 2,
	"editor.formatOnSave": true,
	"editor.smoothScrolling": true,
	"editor.insertSpaces": true,
	"editor.suggest.preview": true,
	"editor.guides.bracketPairs": true,
	// global
	"sort-imports.on-save": true,
	"security.workspace.trust.enabled": false,
	"html-css-class-completion.enableEmmetSupport": true,
	"intelephense.format.braces": "k&r",
	"css.styleSheets": ["https://cdn.jsdelivr.net/npm/bootstrap@5.2.2/dist/css/bootstrap.min.css"],
	// prettier
	"prettier.printWidth": 2048,
	"prettier.singleQuote": false,
	"prettier.jsxSingleQuote": false,
	"prettier.useTabs": true,
	// terminal
	"terminal.integrated.fontFamily": "Hack NF",
	"terminal.integrated.smoothScrolling": true,
	"terminal.integrated.profiles.windows": {
		"PowerShell": {
			"source": "PowerShell",
			"args": ["-noLogo"]
		}
	},
	// emmet
	"emmet.triggerExpansionOnTab": true,
	"emmet.includeLanguages": {
		"javascript": "javascriptreact",
		"vue-html": "html",
		"vue": "html"
	},
	// sass
	"liveSassCompile.settings.formats": [
		{
			"format": "compressed",
			"extensionName": ".min.css",
			"savePath": "/assets/css"
		}
	],
	"[html]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode"
	},
	"[php]": {
		"editor.defaultFormatter": "bmewburn.vscode-intelephense-client"
	},
	"[javascript]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode"
	},
	"[vue]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode"
	},
	"[json]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode"
	},
	"[scss]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode"
	},
	"[jsonc]": {
		"editor.defaultFormatter": "esbenp.prettier-vscode"
	}
}
```

⌨️ keybindings

```jsonc
// Place your key bindings in this file to override the defaults
[
	{
		"key": "ctrl+shift+/",
		"command": "editor.action.blockComment",
		"when": "editorTextFocus && !editorReadonly"
	},
	{
		"key": "shift+alt+a",
		"command": "-editor.action.blockComment",
		"when": "editorTextFocus && !editorReadonly"
	}
]
```

💻 setup terminal

```plaintext
iwr -useb get.scoop.sh | iex
winget install --id Git.Git -e --source winget
scoop install curl sudo jq
scoop install neovim gcc
scoop install fzf
scoop install starship
scoop install https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/oh-my-posh.json
Install-Module posh-git -Scope CurrentUser -Force
Install-Module -Name PSfzf -Scope CurrentUser -Force
Install-Module -Name Terminal-Icons -Repository PSGallery -Force
Install-Module -Name PSReadline -AllowPrerelease -Scope CurrentUser -Force -SkipPublisherCheck

------------------------------------------------------------------------------------------

nvim $profile

# set powershell to utf-8
[console]::InputEncoding = [console]::OutputEncoding = New-Object System.Text.UTF8Encoding

# posh git
Import-Module posh-git

# oh my posh
oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\amro.omp.json" | Invoke-Expression

# terminal icons
Import-Module -Name Terminal-Icons

# psreadline
Set-PSReadLineOption -EditMode Emacs
Set-PSReadLineOption -BellStyle None
Set-PSReadLineKeyHandler -Chord 'Ctrl+d' -Function DeleteChar
Set-PSReadLineOption -PredictionSource History
Set-PSReadLineOption -PredictionViewStyle ListView

# fzf
Import-Module PSFzf
Set-PsFzfOption -PSReadlineChordProvider 'Ctrl+f' -PSReadlineChordReverseHistory 'Ctrl+r'

# alias
Set-Alias -Name vim -Value nvim
Set-Alias ll ls
Set-Alias g git
Set-Alias grep findstr
Set-Alias note notepad

# utilities
function which ($command) {
  Get-Command -Name $command -ErrorAction SilentlyContinue |
    Select-Object -ExpandProperty Path -ErrorAction SilentlyContinue
}
```

💻 terminal config

```json
{
	"$help": "https://aka.ms/terminal-documentation",
	"$schema": "https://aka.ms/terminal-profiles-schema",
	"actions": [
		{
			"command": {
				"action": "copy",
				"singleLine": false
			},
			"keys": "ctrl+c"
		},
		{
			"command": "paste",
			"keys": "ctrl+v"
		},
		{
			"command": "find",
			"keys": "ctrl+shift+f"
		},
		{
			"command": {
				"action": "splitPane",
				"split": "auto",
				"splitMode": "duplicate"
			},
			"keys": "alt+shift+d"
		}
	],
	"copyFormatting": "none",
	"copyOnSelect": true,
	"defaultProfile": "{574e775e-4f2a-5b96-ac1e-a2962a402336}",
	"disableAnimations": true,
	"profiles": {
		"defaults": {
			"colorScheme": "Dracula",
			"cursorShape": "bar",
			"font": {
				"face": "Hack NF"
			},
			"opacity": 50,
			"useAcrylic": true
		},
		"list": [
			{
				"commandline": "%SystemRoot%\\System32\\WindowsPowerShell\\v1.0\\powershell.exe -nologo",
				"guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
				"hidden": false,
				"name": "Windows PowerShell"
			},
			{
				"commandline": "pwsh.exe -nologo",
				"guid": "{574e775e-4f2a-5b96-ac1e-a2962a402336}",
				"hidden": false,
				"name": "PowerShell",
				"source": "Windows.Terminal.PowershellCore"
			},
			{
				"commandline": "%SystemRoot%\\System32\\cmd.exe",
				"guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
				"hidden": false,
				"name": "Command Prompt"
			},
			{
				"guid": "{b453ae62-4e3d-5e58-b989-0a998ec441b8}",
				"hidden": false,
				"name": "Azure Cloud Shell",
				"source": "Windows.Terminal.Azure"
			},
			{
				"guid": "{c6cfa786-b3c8-5411-833f-cf117ac3df84}",
				"hidden": false,
				"name": "Developer Command Prompt for VS 2019",
				"source": "Windows.Terminal.VisualStudio"
			},
			{
				"guid": "{283840bb-8f5c-5f78-96cf-1ba95e862bf6}",
				"hidden": false,
				"name": "Developer PowerShell for VS 2019",
				"source": "Windows.Terminal.VisualStudio"
			}
		]
	},
	"schemes": [
		{
			"background": "#0C0C0C",
			"black": "#0C0C0C",
			"blue": "#0037DA",
			"brightBlack": "#767676",
			"brightBlue": "#3B78FF",
			"brightCyan": "#61D6D6",
			"brightGreen": "#16C60C",
			"brightPurple": "#B4009E",
			"brightRed": "#E74856",
			"brightWhite": "#F2F2F2",
			"brightYellow": "#F9F1A5",
			"cursorColor": "#FFFFFF",
			"cyan": "#3A96DD",
			"foreground": "#CCCCCC",
			"green": "#13A10E",
			"name": "Campbell",
			"purple": "#881798",
			"red": "#C50F1F",
			"selectionBackground": "#FFFFFF",
			"white": "#CCCCCC",
			"yellow": "#C19C00"
		},
		{
			"background": "#012456",
			"black": "#0C0C0C",
			"blue": "#0037DA",
			"brightBlack": "#767676",
			"brightBlue": "#3B78FF",
			"brightCyan": "#61D6D6",
			"brightGreen": "#16C60C",
			"brightPurple": "#B4009E",
			"brightRed": "#E74856",
			"brightWhite": "#F2F2F2",
			"brightYellow": "#F9F1A5",
			"cursorColor": "#FFFFFF",
			"cyan": "#3A96DD",
			"foreground": "#CCCCCC",
			"green": "#13A10E",
			"name": "Campbell Powershell",
			"purple": "#881798",
			"red": "#C50F1F",
			"selectionBackground": "#FFFFFF",
			"white": "#CCCCCC",
			"yellow": "#C19C00"
		},
		{
			"background": "#282A36",
			"black": "#21222C",
			"blue": "#BD93F9",
			"brightBlack": "#6272A4",
			"brightBlue": "#D6ACFF",
			"brightCyan": "#A4FFFF",
			"brightGreen": "#69FF94",
			"brightPurple": "#FF92DF",
			"brightRed": "#FF6E6E",
			"brightWhite": "#FFFFFF",
			"brightYellow": "#FFFFA5",
			"cursorColor": "#F8F8F2",
			"cyan": "#8BE9FD",
			"foreground": "#F8F8F2",
			"green": "#50FA7B",
			"name": "Dracula",
			"purple": "#FF79C6",
			"red": "#FF5555",
			"selectionBackground": "#44475A",
			"white": "#F8F8F2",
			"yellow": "#F1FA8C"
		},
		{
			"background": "#282C34",
			"black": "#282C34",
			"blue": "#61AFEF",
			"brightBlack": "#5A6374",
			"brightBlue": "#61AFEF",
			"brightCyan": "#56B6C2",
			"brightGreen": "#98C379",
			"brightPurple": "#C678DD",
			"brightRed": "#E06C75",
			"brightWhite": "#DCDFE4",
			"brightYellow": "#E5C07B",
			"cursorColor": "#FFFFFF",
			"cyan": "#56B6C2",
			"foreground": "#DCDFE4",
			"green": "#98C379",
			"name": "One Half Dark",
			"purple": "#C678DD",
			"red": "#E06C75",
			"selectionBackground": "#FFFFFF",
			"white": "#DCDFE4",
			"yellow": "#E5C07B"
		},
		{
			"background": "#FAFAFA",
			"black": "#383A42",
			"blue": "#0184BC",
			"brightBlack": "#4F525D",
			"brightBlue": "#61AFEF",
			"brightCyan": "#56B5C1",
			"brightGreen": "#98C379",
			"brightPurple": "#C577DD",
			"brightRed": "#DF6C75",
			"brightWhite": "#FFFFFF",
			"brightYellow": "#E4C07A",
			"cursorColor": "#4F525D",
			"cyan": "#0997B3",
			"foreground": "#383A42",
			"green": "#50A14F",
			"name": "One Half Light",
			"purple": "#A626A4",
			"red": "#E45649",
			"selectionBackground": "#FFFFFF",
			"white": "#FAFAFA",
			"yellow": "#C18301"
		},
		{
			"background": "#002B36",
			"black": "#002B36",
			"blue": "#268BD2",
			"brightBlack": "#073642",
			"brightBlue": "#839496",
			"brightCyan": "#93A1A1",
			"brightGreen": "#586E75",
			"brightPurple": "#6C71C4",
			"brightRed": "#CB4B16",
			"brightWhite": "#FDF6E3",
			"brightYellow": "#657B83",
			"cursorColor": "#FFFFFF",
			"cyan": "#2AA198",
			"foreground": "#839496",
			"green": "#859900",
			"name": "Solarized Dark",
			"purple": "#D33682",
			"red": "#DC322F",
			"selectionBackground": "#FFFFFF",
			"white": "#EEE8D5",
			"yellow": "#B58900"
		},
		{
			"background": "#FDF6E3",
			"black": "#002B36",
			"blue": "#268BD2",
			"brightBlack": "#073642",
			"brightBlue": "#839496",
			"brightCyan": "#93A1A1",
			"brightGreen": "#586E75",
			"brightPurple": "#6C71C4",
			"brightRed": "#CB4B16",
			"brightWhite": "#FDF6E3",
			"brightYellow": "#657B83",
			"cursorColor": "#002B36",
			"cyan": "#2AA198",
			"foreground": "#657B83",
			"green": "#859900",
			"name": "Solarized Light",
			"purple": "#D33682",
			"red": "#DC322F",
			"selectionBackground": "#FFFFFF",
			"white": "#EEE8D5",
			"yellow": "#B58900"
		},
		{
			"background": "#000000",
			"black": "#000000",
			"blue": "#3465A4",
			"brightBlack": "#555753",
			"brightBlue": "#729FCF",
			"brightCyan": "#34E2E2",
			"brightGreen": "#8AE234",
			"brightPurple": "#AD7FA8",
			"brightRed": "#EF2929",
			"brightWhite": "#EEEEEC",
			"brightYellow": "#FCE94F",
			"cursorColor": "#FFFFFF",
			"cyan": "#06989A",
			"foreground": "#D3D7CF",
			"green": "#4E9A06",
			"name": "Tango Dark",
			"purple": "#75507B",
			"red": "#CC0000",
			"selectionBackground": "#FFFFFF",
			"white": "#D3D7CF",
			"yellow": "#C4A000"
		},
		{
			"background": "#FFFFFF",
			"black": "#000000",
			"blue": "#3465A4",
			"brightBlack": "#555753",
			"brightBlue": "#729FCF",
			"brightCyan": "#34E2E2",
			"brightGreen": "#8AE234",
			"brightPurple": "#AD7FA8",
			"brightRed": "#EF2929",
			"brightWhite": "#EEEEEC",
			"brightYellow": "#FCE94F",
			"cursorColor": "#000000",
			"cyan": "#06989A",
			"foreground": "#555753",
			"green": "#4E9A06",
			"name": "Tango Light",
			"purple": "#75507B",
			"red": "#CC0000",
			"selectionBackground": "#FFFFFF",
			"white": "#D3D7CF",
			"yellow": "#C4A000"
		},
		{
			"background": "#000000",
			"black": "#000000",
			"blue": "#000080",
			"brightBlack": "#808080",
			"brightBlue": "#0000FF",
			"brightCyan": "#00FFFF",
			"brightGreen": "#00FF00",
			"brightPurple": "#FF00FF",
			"brightRed": "#FF0000",
			"brightWhite": "#FFFFFF",
			"brightYellow": "#FFFF00",
			"cursorColor": "#FFFFFF",
			"cyan": "#008080",
			"foreground": "#C0C0C0",
			"green": "#008000",
			"name": "Vintage",
			"purple": "#800080",
			"red": "#800000",
			"selectionBackground": "#FFFFFF",
			"white": "#C0C0C0",
			"yellow": "#808000"
		}
	],
	"useAcrylicInTabRow": true
}
```
