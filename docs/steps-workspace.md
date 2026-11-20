## Prepare workspace
### 1. Git repository
  - [x] Initialize local repository<br>
    `git init`
  - [x] Define commit author identity
    ```sh
    git config user.name "<commit author name>"
    git config user.email "<commit author email>"
    ```
  - [x] Make init commit <br>
    `git commit --allow-empty -m"chore: init"`
  - [x] Rename branch `master` to `main`<br>
    `git branch -m master main`
  - [x] Make remote repository on GitHub
  - [x] Add tracked remote repository configuration <br>
    `git remote add origin/gh https://github.com/<repo owner username>/<repo name>.git`
  - [x] Set github HTTPS username for this repository<br>
    `git config credential.https://github.com[/<repo owner username>/<repo name>.git].username <contributor username>`
  - [x] Push init commit and set upstream <br>
    `git push -u origin/gh main`
  - [x] Make .gitignore file for `Visual Studio`,`VSCode`,`dotnet` 
  - [x] Add, commit and push .gitignore
    ```sh
    git add .gitignore
    git commit -m"chore: add .gitignore"
    git push
    ```
### 2. Development tools
  - [x] Add commitlint package and define its config
    ```sh
    npm i -D @commitlint/cli @commitlint/config-conventional 
    npm pkg set scripts.prepare="husky"
    npm i -D husky
    node -e "fs.writeFileSync('commitlint.config.mjs', process.argv[1])" "export default { extends: ['@commitlint/config-conventional'] };"
    #or cmd /A /C "echo export default { extends: ['@commitlint/config-conventional'] }; > commitlint.config.mjs"
    md .husky; 
    node -e "fs.writeFileSync('.husky/commit-msg', 'npx commitlint -s -e')"
    #or: cmd /A /C "echo npx commitlint -s -e > .husky/commit-msg"
    npm run prepare
    ```
  - [x] Add, commit and push<br>
    ```sh
    git add .husky/ commitlint.config.mjs package*.json
    git commit -m"chore: add commitlint to workspace"
    git push
    ```
### 3. Setup git branches
  - [x] main<br>
    protect it, require pull-requests, squash commits
  - [x] dev<br>
    protect it, require pull-requests, never rebase on main
  - [x] dev-by-feature<br>
    always rebase on dev (merge commit, --no-ff) 
  - [x] fix<br>
    branch based on main. branch, cherry-pick to dev

### 4. Define actions to do
  - [x] Add instructions given by the lecturer
  - [x] Define [main steps](steps.md) 
