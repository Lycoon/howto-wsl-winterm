![WSL Windows Terminal preview](/banner.png)

# Setup WSL with Windows Terminal
The tutorial assumes you already have a WSL installed on your machine.

## Add WSL to Windows Terminal
1. Open your terminal
```bash
sudo apt install golang-go
go get -u github.com/justjanne/powerline-go
```
2. Execute `cd` and edit `.bashrc` file with your favorite editor
3. Add the following to the file
```bash
GOPATH=$HOME/go
function _update_ps1() {
    PS1="$($GOPATH/bin/powerline-go -error $?)"
}
if [ "$TERM" != "linux" ] && [ -f "$GOPATH/bin/powerline-go" ]; then
    PROMPT_COMMAND="_update_ps1; $PROMPT_COMMAND"
fi
```
4. Your WSL should appear in Windows Terminal

## Customizing Windows Terminal
Accessing Windows Terminal settings can be done either by
- Clicking the down arrow near the plus sign and clicking `Settings `
- `Ctrl + ,`

A custom `settings.json` file is provided in the repository. It includes functional and graphical features that I found interesting to be set as defaults. It adds the following:
- `Ctrl + Space` shortcut to make Windows Terminal stick to the foreground
- Hides the unnecessary terminals from the dropdown list
- Opens your WSL by default when launching Windows Terminal
- Opens your WSL by default in a specific directory
Change `startingDirectory` directory to update the location where WSL will be set by default or remove the line to set it in the default WSL directory.
- Sets a custom tab title by default for your WSL
Change `tabTitle` value to update it or remove both `suppressApplicationTitle` and `tabTitle` lines to keep the default WSL title instead.
- Sets a custom tab icon by default for your WSL
Change `icon` directory to update the picture attached to the WSL or remove the line to keep the default Linux icon
- Sets a custom tab color by default for your WSL.
Change `tabColor` hexadecimal value to update the default color of your WSL tabs or remove the line to keep the default one.
- Sets the `Campbell` theme as default
The theme can be changed in the `profiles > defaults` part of the file.
`useAcrylic` indicates whether or not you want the background to be blurred.
`acrylicOpacity` is the opacity of that background, it ranges from 0 to 1.
`colorScheme` indicates the set of colors to be used by Windows Terminal. It can be adjusted in the `schemes` part.
`cursorColor` indicates the hexidecimal color of the terminal cursor.
`fontFace` refers to the terminal default font.

If you didn't get enough of help, check more [here](https://docs.microsoft.com/en-us/windows/terminal/tutorials/tab-title) about customization.