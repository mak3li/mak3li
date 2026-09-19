# Save this file as .github/workflows/tetris.yml in your profile repo (USERNAME/USERNAME)
name: Generate Tetris

on:
  schedule:
    - cron: "0 */5 * * *" # every 5 hours: 00:00, 05:00, 10:00, 15:00, 20:00 UTC
  workflow_dispatch: # lets you run it manually from the Actions tab
  push:
    branches: [main]

jobs:
  generate:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v4

      - name: Generate Tetris animation
        uses: leereilly/contribution-graph-art@v1
        with:
          github_user_name: ${{ github.repository_owner }}
          animation_mode: "tetromino"
          tetromino_count: "5"
          palette: "auto"
          output_path: dist/tetris.svg

      - name: Push to output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
