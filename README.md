## Hi there 👋

<!--
**Rachel-XMR/Rachel-XMR** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->

<picture>
  <source
    srcset="https://github-readme-stats.vercel.app/api?username=Rachel-XMR&show_icons=true&theme=dark&rank_icon=github"
    media="(prefers-color-scheme: dark)"
  />
  <source
    srcset="https://github-readme-stats.vercel.app/api?username=Rachel-XMR&show_icons=true&rank_icon=github"
    media="(prefers-color-scheme: light), (prefers-color-scheme: no-preference)"
  />
  <img src="https://github-readme-stats.vercel.app/api?username=Rachel-XMR&show_icons=true" />
</picture>

![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=Rachel-XMR&layout=compact)


<img src="https://img.shields.io/badge/-HTML5-E34F26?style=flat-square&logo=html5&logoColor=white" /> 
<img src="https://img.shields.io/badge/-CSS3-1572B6?style=flat-square&logo=css3" /> 
<img src="https://img.shields.io/badge/-JavaScript-oringe?style=flat-square&logo=javascript" />

![visitors](https://visitor-badge.glitch.me/badge?page_id=Rachel-XMR&left_color=green&right_color=red)

<!-- PIN card
[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=anuraghazra&repo=github-readme-stats)](https://github.com/anuraghazra/github-readme-stats)
-->
![Murui Xiao's github activity graph](https://github-readme-activity-graph.vercel.app/graph?username=Rachel-XMR)


![Typing SVG](https://readme-typing-svg.demolab.com/?lines=HELLO+!;NICE+TO+MEET+YOU+!;HAVE+A+GOOD+DAY+!;STUDY+WITH+ME+~)

name: generate animation

on:
  # run automatically every 2 hours
  schedule:
    - cron: "0 */2 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - master
  
  

jobs:
  generate:
    permissions: 
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
  
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
  
  
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}



