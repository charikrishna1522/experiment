# experiment
name: Stragety Matrix Sample
on:
  push:
    branches:
      - main
  pull_request:
jobs:
  ivi_test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        BRAND: ["T"]
        REGION: ["na", "jp"]
        SCREEN: ["10.5_1280x720", "12.3_1920x720", "14_1920x1080"]
        LOCALE: ["en", "ja"]
    steps:
      - name: run test
        run: echo "Running tests for ${{matrix.BRAND}} ${{matrix.REGION}} ${{matrix.SCREEN}} ${{matrix.LOCALE}}"
  ivi_coverage:
    needs: ivi_test
    runs-on: ubuntu-latest
    steps:
      - name: coverage
        run: echo "Running coverage"
