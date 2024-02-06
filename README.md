software engineering method


Hi there!My name is Blessing.

[![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=BlessingAyoola)](https://github.com/anuraghazra/github-readme-stats)

![GitHub Workflow Status (branch)](https://img.shields.io/github/actions/workflow/status/BlessingAyoola/sem/main.yml?branch=master)

name: A workflow for my Hello World App
on: push

jobs:
  build:
    name: Hello world action
    runs-on: ubuntu-20.04
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Set up JDK 11
        uses: actions/setup-java@v2
        with:
          java-version: '11'
          distribution: 'adopt'
      - name: Compile with Maven
        run: mvn compile
      - name: Build Docker Image
        run: docker build -t semimage .
      - name: Run image
        run: docker run --name semcontainer -d semimage
      - name: view logs
        run: docker logs semcontainer