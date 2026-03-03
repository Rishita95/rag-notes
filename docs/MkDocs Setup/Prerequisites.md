# 1. Prerequisites

1.1 Open Terminal
    - Press Cmd + Space
    - Type "Terminal" and hit "Enter"
    - You'll use this window for all commands.

1.2 Check Python

    > Run the following command to check if Python is installed:

        ```bash
        python3 --version
        ```

        If you see something like Python 3.11.7, you’re good. MkDocs needs Python 3.
    
        If you see “command not found” or only an old Python 2.x, install Python.

    > To install Python via Homebrew exists (recommended):

        1. Check if Homebrew is installed:
            - brew --version

        2. If not installed, install Homebrew:

        - /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

    >   Install Python 3:

        - brew install python3

        This gives you Python 3 and pip (the package installer) together.

1.3 Check pip:

    > Run the following command to check if pip is installed:

        ```bash
        pip3 --version
        ```

        If you see something like pip 23.3.1, you’re good. MkDocs needs pip.
