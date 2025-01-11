# 👻 Anzugs

**`Digital Version (Developer/Staff)`**

Hey, I’m Anzugs! When I’m not busy with everyday stuff, I spend a lot of my free time coding and working on different development projects. I also run a Minecraft server called SteamMines(.minehut.gg), where I try to create fun, unique experiences for players. 


<!-- Discord Profile Button -->
<a href="https://discordapp.com/users/1071072739579932785" target="_blank">
  <img align="left" alt="Discord" width="30px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/npm/simple-icons@v6/icons/discord.svg" />
</a> My Discord Account


---
### 💼 Coding Languages & Editors
<img align="left" alt="Java" width="30px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg"/>
<img align="left" alt="HTML" width="30px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-plain.svg" />
<img align="left" alt="Python" width="30px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-plain.svg" /> 
<img align="left" alt="VS Code" width="30px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg" />
<img align="left" alt="Atom" width="30px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/atom/atom-original.svg" />
<img align="left" alt="Discord" width="30px" style="padding-right:10px;" src="https://cdn.jsdelivr.net/npm/simple-icons@v6/icons/discord.svg" />

Questions? - DM me on Discord!

---

### 📊 Stats

![Forrest's GitHub stats](https://github-readme-stats.vercel.app/api?username=anzugs&show_icons=true&theme=gruvbox)

<!-- ![GitHub Streak](https://streak-stats.demolab.com?user=ForrestKnight&theme=gruvbox&border_radius=4.5) -->
<summary><h3>🧑‍💻 My Development Journey</h3><summary>
In the end, I just love computers and wanted to know what they can do... So I tried. From my first Hello World! in Phython to countless of hours infront of YouTube Videos I am now here. Able to code Skript, and learning more and more.
I don´t know where, when and how I am going to use that knowladge in the future but I do know I will. I am not really good at anything, but atleast I can do *something* and well: Practise makes Perfect!

name: GitHub Snake Game

on:
  # Schedule the workflow to run daily at midnight UTC
  schedule:
    - cron: "0 0 * * *"
  # Allow manual triggering of the workflow
  workflow_dispatch:
  # Trigger the workflow on pushes to the main branch
  push:
    branches:
      - main
jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    steps:
      # Step 1: Checkout the repository
      - name: Checkout Repository
        uses: actions/checkout@v3
      # Step 2: Generate the snake animations
      - name: Generate GitHub Contributions Snake Animations
        uses: Platane/snk@v3
        with:
          # GitHub username to generate the animation for
          github_user_name: ${{ github.repository_owner }}
          # Define the output files and their configurations
          outputs: |
            dist/github-snake.svg
            dist/github-snake-dark.svg?palette=github-dark
            dist/ocean.gif?color_snake=orange&color_dots=#bfd6f6,#8dbdff,#64a1f4,#4b91f1,#3c7dd9
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      # Step 3: Deploy the generated files to the 'output' branch
      - name: Deploy to Output Branch
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
          publish_branch: output
          # Optionally, you can set a custom commit message
          commit_message: "Update snake animation [skip ci]"
        
