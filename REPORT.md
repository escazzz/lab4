# Лабораторная работа №4

### Цель - изучениe систем непрерывной интеграции на примере сервиса GitHub Actions

Создам *fork* репозитория LAB33 (https://github.com/a0730c/LAB3)<br />
Создам локальный репозиторий и сделаю **pull**<br />

Создам workflow:
```
$ mkgir .github
$ cd .github
$ mkdir workflows 
$ cd workflows
$ touch cmake.yml
```
Открою его для внесения изменений:```$ nano cmake.yml```<br />
Отредактирую:
```
name: CMake

on:
  push:
    branches: [ "master" ]
  pull_request:
    branches: [ "master" ]

env:
# Customize the CMake build type here (Release, Debug, RelWithDebInfo, etc.)
  BUILD_TYPE: Release

jobs:
  build_Linux:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3
    - name: hello
      run: |
        cd ${{ github.workspace }}/hello_world_application
        mkdir build_test
        cd build_test
        cmake ..
        cmake —build . —config ${{env.BUILD_TYPE}}

    - name: formatter_lib
      run: |
        cd ${{ github.workspace }}/formatter_lib
        mkdir build_test
        cd build_test
        cmake ..
        cmake —build . —config ${{env.BUILD_TYPE}}

    - name: formatter_ex_lib
      run: |
        cd ${{ github.workspace }}/formatter_ex_lib
        mkdir build_test
        cd build_test
        cmake ..
        cmake —build . —config ${{env.BUILD_TYPE}}
    - name: solver_application
      run: |
        cd ${{ github.workspace }}/solver_application
        mkdir build_test
        cd build_test
        cmake ..
        cmake —build . —config ${{env.BUILD_TYPE}}
```

Добавлю изменения в удаленный репозиторий:<br />
```
$ git add all
$ git commit -m "cmake.yml created"
$ git push origin master
```
