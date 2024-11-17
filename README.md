# TestVNCinCodespace
Spike to try out a VNC server in a codespace.

## Open a Codespace

[![Open in a GitHub Codespace](https://github.com/codespaces/badge.svg)](https://codespaces.new/braughtg/TestVNCinCodespace?quickstart=1)
- Note: Gives option to resume most recent codespace if one exists.

## Connect via noVNC

- Click *Ports* in the Codespace window.
- Wait for port 6080 (NoVNC) to open
- Right click the URL for port 6080 and choose:
  - "Preivew in Editor" to open in a tab in the VSCode interface.
  - "Open in Browser" to open in its own browser tab.
- Click "Connect"
- Right click on the desktop to launch applications from the pop-up menu.

## Notes:
       
- Copy and paste between host and noVNC is via their clunky clipboard.

- Can only connect with VNC client if connected using a local a local tool (e.g. VSCode).
  - We may be able to make this work using the `gh` cli?
    - Requires a token with "codespace" scope
    - Use terminal commands on the local machine to:
      - create or start the codespace.
      - forward the port to the local machine.
      - then connect to it with VNC.
      - stop the codespace.

## ToDo

- Would be great to have the NoVNC client open automatically in a preview or browser tab.
  - Seems like this should be possible with something like a task (https://code.visualstudio.com/docs/editor/tasks) that opens a browser (https://stackoverflow.com/questions/34205481/how-to-open-browser-from-visual-studio-code-api/44967017)

- Can easily configure the pop-up menu to include whatever we want.

- Possibly consider installing the gh cli so that they can stop the codespace from the command line in noVNC.
  - Will require that they login to github via gh.
