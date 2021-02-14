# Customize Windows Terminal

- Get started: [Install and set up Windows Terminal](https://docs.microsoft.com/en-us/windows/terminal/get-started)
- Install from the Microsoft Store: [Terminal in Microsoft Store](https://aka.ms/terminal)

![PowerShell](Screenshot_ps.png)

- Better to install the new PowerShell: https://docs.microsoft.com/en-us/powershell/
- You can do it via Microsoft Store: https://www.microsoft.com/store/apps/9MZ1SNWT0N5D

-------------------------

## Keyboard shortcuts
- Keyboard shortcuts are listed in "defaults.json" (in Terminal:  hold <kbd>Alt</kbd> and click on Settings)
- They are also listed in the command pallete: <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>

-------------------------

## Themes
- Default themes are in "defaults.json"

### * Additional Themes
- There are good themes in https://windowsterminalthemes.dev/
- Add your theme's code to the "Schemes" part of the Terminal "settings.json" (normal settings of Terminal)
- Use the name of the desired theme at desired profile:
    ``` "colorScheme": "Horizon" ```

> **Using Acrylic**
    ```
    "useAcrylic": true,
    "acrylicOpacity": 0.7
    ```

-------------------------

## Customize command prompt

![Kali-Linux](Screenshot_kali.png)

- Add <a href="CascadiaCodePL.ttf">Cascadia Code PL</a> font to Terminal profiles in "settings.json":
"fontFace": "Cascadia Code PL"

- Install posh and oh-my-posh from Powershell (should be done in both "PowerShell" & "Windows PowerShell"):
    ```
    > Install-Module posh-git -Scope CurrentUser
    > Install-Module oh-my-posh -Scope CurrentUser
    ```

> - For "Windows PowerShell", you should run as admin & change ExecutionPolicy for further steps:
    ``` > Set-ExecutionPolicy RemoteSigned ```

- Create PowerShell profile if not exists:
    - for "PowerShell":
    %HOMEPATH%\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
    - for "Windows PowerShell":
    %HOMEPATH%\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1

- Put these lines in profile and save it:
    ```
    Import-Module posh-git
    Import-Module oh-my-posh
    Set-Theme Zash
    ```

> - Change Set-Theme parameter to your desired theme's name
    Theme names are listed in: https://github.com/JanDeDobbeleer/oh-my-posh#themes

-------------------------
## Tab icons

- Example:
    - Place the icon image "ubuntu.ico" or "ubuntu.png" in the folder located at
    ``` %LOCALAPPDATA%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\RoamingState ```
    - you can display the icon by adding this line to the ubuntu profile in the settings.json:

    ```
    "icon": "ms-appdata:///roaming/ubuntu.ico"
    or
    "icon": "ms-appdata:///roaming/ubuntu.png"
    ```

-------------------------
## Remove PowerShell welcome message

- Add the following line to the profile:
- For PowerShell: ``` "commandline": "pwsh.exe /nologo" ```
- For Windows PowerShell: ``` "commandline": "powershell.exe /nologo" ```

-------------------------
## Show Anaconda environments

- To show the conda env name in the prompt, change the "commandline" section to execute the conda script at PowerShel startup
- Example for miniconda:
```
"commandline": "pwsh.exe /nologo -NoExit -Command \"& 'C:\\Users\\%USERNAME%\\miniconda3\\shell\\condabin\\conda-hook.ps1' ; conda activate 'C:\\Users\\%USERNAME%\\miniconda3' \""
```
![PowerShell](Screenshot_conda.png)
> Note that not all the oh-my-posh themes support this! I use Honukai theme ( ``` Set-Theme Honukai ``` in the $PROFILE file), that supports it .
