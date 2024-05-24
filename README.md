## olá meu nome e Gabriel Oliveira 
- 🔭 Atualmente não estou trabalhando , mas estou focado para entrar na área
- 🌱 Estou estudando Desenvolvimento web
-  <div>
  <a href="https://github.com/Gabrielryu1">
  <img height="180em" src="https://github-readme-stats.vercel.app/api?username=Gabrielryu1&show_icons=true&theme=dark&include_all_commits=true&count_private=true"/>
  <img height="180em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Gabrielryu1&layout=compact&langs_count=16&theme=dark"/>
</div>
<div style="display: inline_block"><br>

  <img align="center" alt="Gabriel-Csharp" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/csharp/csharp-original.svg">
  <img align="center" alt="Gabriel-HTML" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original.svg">
    <img align="center" alt="Gabriel-Java" height="30" width="40"src= "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/java/java-original.svg" />
          
              
 
<div> 
  <a href="https://www.instagram.com/gabriel_moraes23/" target="_blank"><img src="https://img.shields.io/badge/-Instagram-%23E4405F?style=for-the-badge&logo=instagram&logoColor=white" target="_blank"></a>
  <a href="https://www.linkedin.com/in/gabriel-leoncio-5b4885182/" target="_blank"><img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"></a> 
 
  ![Snake animation](https://github.com/rafaballerini/rafaballerini/blob/output/github-contribution-grid-snake.svg)
 
</div>

# GitHub Action for generating a contribution graph with a snake eating your contributions.

# ![snake gif](https://github.com/your-user-name/your-user-name/blob/output/github-contribution-grid-snake.gif)

name: Generate Snake

# Controls when the action will run.
on:
  schedule:
      # every 12 hours
    - cron: "0 */12 * * *"

  # This command allows us to run the Action automatically from the Actions tab.
  workflow_dispatch:
  
  # Also run on every push on the master branch
  push:
    branches:
    - main

# The sequence of runs in this workflow:
jobs:
  # This workflow contains a single job called "build"
  build:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
      - name: Clone repo
        uses: actions/checkout@v3
    
      - name: Generate the snake files in './dist/'
        uses: Platane/snk@v3
        id: snake-gif
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |     
            dist/github-contribution-grid-snake.gif
            dist/github-contribution-grid-snake.svg
        env:
           GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

      - name: Show build status
        run: git status

      - name: Push new files to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
          commit_message: Update snake animations
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
