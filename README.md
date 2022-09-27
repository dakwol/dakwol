<div id="header" align="center">
  <img src="https://media.giphy.com/media/lbcLMX9B6sTsGjUmS3/giphy-downsized.gif" width="100%" height="200"/>
</div>
<h1 align="center">
  Welcome
  <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="30px"/>
</h1>


### :man_technologist: About Me :
I am a Web Developer <img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="30"> from Russia.

 :telescope: I’m working as a Web developer and contributing to frontend for building web applications.

- :seedling: Exploring Technical Content Writing.

- :zap: In my free time, I solve logic puzzles and pet a cat:3

- :mailbox:How to reach me: [![Telegram Badge](https://img.shields.io/badge/Telegram-white?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/Dakwol)

### :hammer_and_wrench: Languages and Tools :

<div align="center">
  
  <img src="https://github.com/devicons/devicon/blob/master/icons/html5/html5-original.svg" title="HTML5" alt="HTML" width="60" height="60"/>
  <img src="https://github.com/devicons/devicon/blob/master/icons/css3/css3-plain-wordmark.svg"  title="CSS3" alt="CSS" width="60" height="60"/>
  <img src="https://github.com/devicons/devicon/blob/master/icons/javascript/javascript-original.svg" title="JavaScript" alt="JavaScript" width="60" height="60"/>
  
  <img src="https://github.com/devicons/devicon/blob/master/icons/gulp/gulp-plain.svg" title="Gulp" alt="Gulp" width="60" height="60"/>
  <img src="https://github.com/devicons/devicon/blob/master/icons/sass/sass-original.svg" title="Sass" alt="Sass" width="60" height="60"/>
  <img src="https://github.com/devicons/devicon/blob/master/icons/typescript/typescript-original.svg" title="TS" alt="TS" width="60" height="60"/>
  
  
  <img src="https://github.com/devicons/devicon/blob/master/icons/jquery/jquery-original-wordmark.svg" title="JQuery" alt="JQuery" width="60" height="60"/>
  
  <img src="https://github.com/devicons/devicon/blob/master/icons/react/react-original-wordmark.svg" title="React" alt="React" width="60" height="60"/>
  <img src="https://github.com/devicons/devicon/blob/master/icons/figma/figma-original.svg" title="Figma" alt="Figma" width="60" height="60"/>
  <img src="https://github.com/devicons/devicon/blob/master/icons/vscode/vscode-original-wordmark.svg" title="VSCode" alt="VSCode" width="60" height="60"/>
  
</div>

  ### :fire: My Stats :
<div  align="center" flex-direction="row">
  
[![GitHub Streak](http://github-readme-streak-stats.herokuapp.com?user=dakwol&theme=tokyonight&border_radius=10)](https://git.io/streak-stats)

[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=dakwol&layout=compact&theme=tokyonight&border_radius=10)](https://github.com/anuraghazra/github-readme-stats)
</div>
name: generate animation

on:
  # run automatically every 12 hours
  schedule:
    - cron: "0 */12 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - master
    
  

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v2
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v2.6.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
