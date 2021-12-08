on: [push]

jobs:
  build:
    name: CombinePDFS
    runs-on: ubuntu-latest
    env:
      path: resources //CHANGE THIS
      filename: example //CHANGE THIS
    steps:
      - uses: actions/checkout@v2
      - uses: elMuso/MergePDFs-action@1.1
        with:
          path: ${{env.path}}
          filename: ${{env.filename}}
      - name: Upload combined pdf
        uses: actions/upload-artifact@v2
        with:
          name: ${{env.filename}}
          path: ${{env.path}}/${{env.filename}}.pdf

