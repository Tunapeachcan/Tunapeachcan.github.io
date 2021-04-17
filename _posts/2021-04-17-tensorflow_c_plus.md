---
title: "Tensorflow C++ DLL for visual studio 2019"
date: 2021-04-17 22:00:00 -0400
categories: tensorflow
---

# Tensorflow C++ DLL 사용법(Visual Studio 2019)

## 1. DLL Download

- 아래 경로에서 DLL 파일을 다운로드한다 (다운로드 시점에서는 2.4버전)
- tensorflow 2.x 다운로드 위치 : <https://www.tensorflow.org/install/lang_c?hl=ko>  

![이미지](/2021-04-17-tensorflow_c_plus/1.tensorflowDownload.PNG "tensorflowDownload")

- 추가 다운로드 파일
- 위의 파일만 다운 받아서는 .h 파일이 부족해서 컴파일이 되지 않는다
- 깃허브 텐서 플로우 공식 페이지의 코드를 모두 다운 받는다
- 다운로드 위치 : <https://github.com/tensorflow/tensorflow>

![이미지](/2021-04-17-tensorflow_c_plus/1-1.tensorflow.PNG "tensorflowDownload")

## 2. Visual studio 프로젝트 생성 (Visual Studio 2019 이용)

- Visaul Studio 2019 C++ 프로젝트를 생성합니다.
- 여기서는 console project로 생성합니다.

![이미지](/2021-04-17-tensorflow_c_plus/2.VisualStudioProject1.PNG "vusalstudio1")

- 프로젝트 이름은 tf로 생성합니다.

![이미지](/2021-04-17-tensorflow_c_plus/3.VisualStudioProject2.PNG "vusalstudio1")

- 다 만들어 지면 아래와 같이 나옵니다.

![이미지](/2021-04-17-tensorflow_c_plus/4.VisualStudioProject3.PNG "visualstudio1")

## 3. File Copy 

- 다운 받은 libtensorflow-cpu-windows-x86_64-2.4.0.zip 파일에서 include 폴더 내부의 tensorflow 폴더를 Visual studio 프로젝트(cpp 파일이 있는 위치)에 복사합니다

![이미지](/2021-04-17-tensorflow_c_plus/5.Copy.png "include 복사")

- 다운 받은 libtensorflow-cpu-windows-x86_64-2.4.0.zip 파일에서 lib 폴더 내부의 파일들을 Visual studio 프로젝트에 x64/Debug에 복사합니다 (폴더가 없을 경우 만들어야 합니다)

![이미지](/2021-04-17-tensorflow_c_plus/6.libcopy.png "lib 복사")

- Github에서 다운받은 tensorflow-master.zip 파일 압축을 푼다
- 압축푼 파일에 tensorflow-master\tensorflow\c 에 있는 파일을 visual stdio 프로젝트 tensorflow\c 폴더에 붙여넣기 한다

![이미지](/2021-04-17-tensorflow_c_plus/7.includecopy.png "lib 복사")

- Github에서 다운받은 tensorflow-master.zip 압축푼 파일에 tensorflow-master\tensorflow\core\platform 에 있는 파일을 visual stdio 프로젝트 tensorflow\ 폴더에 붙여넣기 한다

![이미지](/2021-04-17-tensorflow_c_plus/8.platformcopy.png "lib 복사")

## 4. Code 작성

- 아래와 같이 작성하고 실행을 눌러본다.

``` cpp
#include <iostream>
#include <stdio.h>
#pragma comment(lib, "../x64/Debug/tensorflow.lib")

#include "tensorflow/c/c_api.h"

int main()
{
    printf("Hello from TensorFlow C library version %s\n", TF_Version());
}
```
- 아래와 같이 나오면 연동 성공

![이미지](/2021-04-17-tensorflow_c_plus/9.result.png "lib 복사")