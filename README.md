name: Build EXE
on: [push]
jobs:
  build:
    runs-on: windows-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: '3.10'
      - run: pip install pyinstaller
      - run: pyinstaller --onefile asistente_box.py
      - uses: actions/upload-artifact@v3
        with:
          name: asistente_box
          path: dist/asistente_box.exe
