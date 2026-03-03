# 1. Setup Process

You'll now create a new documentation project folder.

## 1.1 Choose where to create the project folder.

    For example, on your /documents folder.

    - Open Finder
    - Navigate to your /documents folder
    - Press `Cmd + Shift + N` to create a new folder
    - Name the folder "RAGprojects"
    - Now, open that folder "RAGprojects" and inside that create one more folder named as "Rag-notes".
    - Now your folder structure should look like this:

    ~/Documents/RAGprojects/Rag-notes


## 1.2 Open Terminal at your project folder

    - Open Finder
    - Navigate to your "Rag-notes" folder
    - Press `Cmd + Shift + .` to show the path bar
    - Press `Cmd + Option + P` to show the path bar
    - Right click on the folder and select "New Terminal at Folder"
    - Now you should see a terminal window open at your project folder.

    In the Terminal window, copy and paste the following code blocks one by one:

    ```bash
    uv init --no-package
    uv add mkdocs mkdocs-material
    uv run mkdocs new .

    Inside Rag-notes folder, it creates:
    > mkdocs.yml  -  the configuration file for mkdocs
    > docs/  -  the folder where you will store your Markdown files
    > .venv/  -  the virtual environment for mkdocs
    > docs/index.md - the main page of your documentation site
    
    You can check the folder structure by running the following command in the terminal:

        ```bash
        ls
        ```
    You should see the following output:
    > docs/  mkdocs.yml  .venv/

    And inside docs folder you should see:

    > index.md
    ``` 

## 1.3 Configure mkdocs.yml

    - Go to the folder "Rag-notes" and you will see a file named "mkdocs.yml". 
    - Open the mkdocs.yml file in your text editor
    - Replace the contents of the file with the following code:

        ```yaml
        theme:
        name: material
        palette:
            - scheme: default
            toggle:
                icon: material/brightness-7
                name: Switch to dark mode
            - scheme: slate
            toggle:
                icon: material/brightness-4
                name: Switch to light mode
        ```
    - Now save the file and close it.
    

    - Your folder structure should look like this:

    


## 1.4 Run the server   

    To view your site locally, run:

        ```bash
        uv run mkdocs serve
        ```

    - This will start a local web server. Open your browser and go to http://127.0.0.1:8000
    
    - You should see your documentation site live!

If the page doesnt load, check that "uv run mkdocs serve" is running in the terminal.

# Edit Content and Configuration

Now you'll change the homepage, add a new page, and configure navigation.

## 1. Edit the Homepage (index.md)

    - Go to the folder "Rag-notes". 
    - Open the docs/index.md file in your text editor
    - Replace the contents of the file with the following code:

        > Welcome to My Docs

        This is my first MkDocs site on macOS.

        > Getting Started

        - This is a bullet point.
        - This is another one.

    - Now save the file and close it.

Switch back to your browser; the page should auto-refresh and show your new content.

# Create a second page

## 1. Create a new Markdown file

    - Go to the folder "Rag-notes". 
    - Open the docs/ folder and create a new file named as "about.md"
    - Now open that file "about.md" in your text editor
    - Replace the contents of the file with the following code:

        > About Me

        This is my second page.

        > Getting Started

        - This is a bullet point.
        - This is another one.
    
    - Save the file and close it.
    
Right now, if you check your browser, you'll see the homepage but no link to "About Me". You need to update the navigation in `mkdocs.yml`.

## 2. Update Navigation (mkdocs.yml)

    - Go back to the folder "Rag-notes". 
    - Open the mkdocs.yml file in your text editor
    - Replace the contents of the file with the following code:

        ```yaml
        site_name: My Docs
        nav:
        - Home: index.md
        - About Me: about.md
        theme:
        name: material
        palette:
            - scheme: default
            toggle:
                icon: material/brightness-7
                name: Switch to dark mode
            - scheme: slate
            toggle:
                icon: material/brightness-4
                name: Switch to light mode
        ```
    - Now save the file and close it.

    Explanation:
        > site_name is the title shown in the top-left.
        > nav defines the menu:
            > Each line - Title: filename.md is one menu item.
            > The file is relative to the docs/ folder.
    
    - Switch back to your browser. You should now see a "About Me" link in the top navigation bar. Click it to see your second page!    

