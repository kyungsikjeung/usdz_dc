## usdz_dc

# 1. brew 설치
```code
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
# 2. brew로 USD 설치
```code
brew install usd
```

# 3. Draco 압축을 위해, Draco를 GitHub에서 다운로드 및 cmake :
```code
git clone https://github.com/google/draco.git
cd draco

mkdir build
cd build

cmake ..
make -j
```


3. 파이선 편집 
```code
cd /Users/yourusername/Documents
nano myscript.py (이하 내용)
# 5번 항목 참조
Control+X , 그리고 y


```

# 4. 파이선 스크립트 실행
```code
python myscript.py
```
# 5. 파이선 스크립트(USDZ draco compression)
```code
from pxr import Usd, UsdDraco
stage = Usd.Stage.Open('yourfile.usd')

# Draco 압축 옵션 설정

compressionOptions = UsdDraco.CompressionOptions()
compressionOptions.quantizationBitsPosition = 14
compressionOptions.quantizationBitsTexCoords = 12
compressionOptions.quantizationBitsNormals = 10
compressionOptions.quantizationBitsGeneric = 8

# USD 파일을 Draco로 압축하기
compressedStage = UsdDraco.CompressStage(stage, compressionOptions)

# 압축된 파일 저장하기
compressedStage.GetRootLayer().Export('yourfile_compressed.usd')
```
