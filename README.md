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
- Onetime Setup
  - Create GitHub token with `repo`, `read:org`, `workflow`, `codespaces`
  - `gh auth login` and paste the token
  - Open the Codespace using the button above.
    - Or use `gh codespace create --repo braughtg/TestVNCinCodespace --web`
      - note: can also set idle timeout using `--idle-timeout "10m"`
- Use
  - In a terminal on the local machine, forward the VNC port from the Codespace:
    - `gh codespace ports forward 5901:5901 --repo braughtg/TestVNCinCodespace`
      - remotePort:localPort
      - Note: Once the Codespace exists, this both starts it and forwards the ports.
  - Use VNC on the local machine to connect to the localPort
  - Stop the Codespace from a terminal on the local machine (or via GitHub).
    - `gh codespace stop --repo braughtg/TestVNCinCodespace`

Note: If there is more than one Codespace on `braughtg/TestVNCinCodespace` you will be prompted to choose one when using the `gh` commands.

## ToDo

- Would be great to have the NoVNC client open automatically in a preview or browser tab.
  - Seems like this should be possible with something like a task (https://code.visualstudio.com/docs/editor/tasks) that opens a browser (https://stackoverflow.com/questions/34205481/how-to-open-browser-from-visual-studio-code-api/44967017)

- Would be nice to streamline connecting with VNC on the local machine.
  - Not clear if there is a way to start an existing codespace with `gh`???
  
- Can easily configure the pop-up menu to include whatever we want.

