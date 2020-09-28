# Setup WSL with Windows Terminal
This repository aims to provide simple step-by-step process to access your favorite WSL through the Windows Terminal. It also includes a configuration file that I estimate containing most interesting features. The tutorial assumes you already have a WSL installed on your machine.

![WSL Windows Terminal preview](/banner.png)

### Add WSL to Windows Terminal
1. Open your terminal and execute the following.
```bash
sudo apt install golang-go
go get -u github.com/justjanne/powerline-go
```
2. Execute `cd` and edit `.bashrc` file with your favorite editor.
3. Add the following to the file.
```bash
GOPATH=$HOME/go
function _update_ps1() {
    PS1="$($GOPATH/bin/powerline-go -error $?)"
}
if [ "$TERM" != "linux" ] && [ -f "$GOPATH/bin/powerline-go" ]; then
    PROMPT_COMMAND="_update_ps1; $PROMPT_COMMAND"
fi
```
4. Your WSL should now appear in Windows Terminal dropdown menu by clicking the down arrow.

### Customizing Windows Terminal
Accessing Windows Terminal settings can be done either by clicking the down arrow near the plus sign and `Settings`, or with `Ctrl + ,` shortcut.

A custom `settings.json` file is provided in the repository. It includes functional and graphical features that I found interesting to be set as defaults. It adds the following:
<ul>
<li>"Ctrl + Space" shortcut to make Windows Terminal stick to the foreground</li>
<li>Hides the unnecessary terminals from the dropdown list</li>
<li>Opens your WSL by default when launching Windows Terminal</li>

<li>Opens your WSL by default in a specific directory</li>
<ul><li>Change "startingDirectory" directory to update the location where WSL will be set by default or remove the line to set it in the default WSL directory.</li></ul>

<li>Sets a custom tab title by default for your WSL</li>
<ul><li>Change "tabTitle" value to update it or remove both "suppressApplicationTitle" and "tabTitle" lines to keep the default WSL title instead.</li></ul>

<li>Sets a custom tab icon by default for your WSL</li>
<ul><li>Change "icon" directory to update the picture attached to the WSL or remove the line to keep the default Linux icon.</li></ul>

<li>Sets a custom tab color by default for your WSL.</li>
<ul><li>Change "tabColor" hexadecimal value to update the default color of your WSL tabs or remove the line to keep the default one.</li></ul>

<li>Sets the Campbell theme as default. The theme can be changed in the "profiles > defaults" part of the file.</li>
<ul><li>"useAcrylic" indicates whether or not you want the background to be blurred.</li>
<li>"acrylicOpacity" is the opacity of that background, it ranges from 0 to 1.</li>
<li>"colorScheme" indicates the set of colors to be used by Windows Terminal. It can be adjusted in the "schemes" part.</li>
<li>"cursorColor" indicates the hexidecimal color of the terminal cursor.</li>
<li>"fontFace" refers to the terminal default font.</li></ul>
</ul>

If you didn't get enough of help, check more <a href="https://docs.microsoft.com/en-us/windows/terminal/tutorials/tab-title" target="_blank">here</a> about customization.