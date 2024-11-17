# TestVNCinCodespace
Spike to try out a VNC server in a codespace.

## Open a Codespace

[![Open in a GitHub Codespace](https://github.com/codespaces/badge.svg)](https://codespaces.new/braughtg/TestVNCinCodespace?quickstart=1)
- Note: Gives option to resume most recent codespace if one exists.

## Connect via noVNC

Note: Copy and paste between host and noVNC is via their clunky clipboard.

- Open the Codespace using the button above.
- Click *Ports* in the Codespace window when it appears.
- Wait for port 6080 (NoVNC) to open
- Right click the URL for port 6080 and choose:
  - "Preivew in Editor" to open in a tab in the VSCode interface.
  - "Open in Browser" to open in its own browser tab.
- Click "Connect" to open the desktop.
- Right click on the desktop to launch applications from the pop-up menu.

## Connect via VNC with `gh` on Local Machine

- Requires
  - `gh`
  - TigerVNC client
- Setup
  - Create GitHub token with `repo`, `read:org`, `workflow`, `codespaces`
  - `gh auth login` and paste the token
- Open the Codespace using the button above
  - Or alternatively using `gh`
    - `gh codespace create --repo braughtg/TestVNCinCodespace --display-name "vnctest" --web` (to create it the first time)
      - note: can also set idle timeout using `--idle-timeout "10m"`
    - `gh codespace code --repo braughtg/TestVNCinCodespace --web` (to restart an existing codespace)
      - Choose the codespace from the options presented.
- Click "Ports" in the browsesr window where the Codespace is opening and wait for port 5901 to open.
- In a terminal on the local machine, forward the VNC port from the Codespace:
  - `gh codespace ports forward 5901:5901 --repo braughtg/TestVNCinCodespace`
    - remotePort:localPort
  - Choose the Codespace from the options presented.
- Use VNC on the local machine to connect to the localPort
- Stop the Codespace from a terminal on the local machine (or via GitHub).
  - `gh codespace stop --repo braughtg/TestVNCinCodespace`
    - Choose the codespace from the options presented.

Note: If we know the name (not the display name) of the Codespace we can use `--codespace "name"` instead of `--repo braughtg/TestVNCinCodespace` and skip the step of choosing the codespace. But note that the Codespace names contain a hash so are not convenient to type. 

## ToDo

- Would be great to have the NoVNC client open automatically in a preview or browser tab.
  - Seems like this should be possible with something like a task (https://code.visualstudio.com/docs/editor/tasks) that opens a browser (https://stackoverflow.com/questions/34205481/how-to-open-browser-from-visual-studio-code-api/44967017)

- Would be nice to streamline connecting with VNC on the local machine.
  - Not clear if there is a way to start an existing codespace with `gh`???
  
- Can easily configure the pop-up menu to include whatever we want.

