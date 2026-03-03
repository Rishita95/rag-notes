# Publishing Site to GitHub Pages

You publish MkDocs to GitHub Pages with mkdocs gh-deploy command, which pushes the build site to a gh-pages branch and serves it from there. 

1. Prepare your GitHub repository

Create a new repository on GitHub. Let's call it "RAGprojects". In the Path bar at the bottom of the window

2. Initialize Git in your project

    ```bash
    git init
    ```

3. Add your project files to Git

    ```bash
    git add .
    ```

4. Commit your changes

    ```bash
    git commit -m "Initial commit"
    ```

5. Add the remote repository

    ```bash
    git remote add origin <repository-url>
    ```

6. Push your changes to GitHub

    ```bash
    git push -u origin main
    ```

7. Deploy your site

    ```bash
    mkdocs gh-deploy
    ```

8. View your site

    ```bash
    http://<your-username>.github.io/<repository-name>
    ```



