* [tensorflow 异常](https://blog.csdn.net/magic_spongebob/article/details/79590033)
```
pip uninstall tensorflow
pip install tensorflow==1.5
```

* [dlib 异常](https://github.com/ageitgey/face_recognition/issues/11#issuecomment-287398611)
```
The issue is most likely that dlib was compiled with support for AVX and/or SSE4 instructions, 
but your cpu is too old to support them (pre-2011, I think).

最简单的解决方案是下载dlib并自行编译。但是当你这样做时，你需要做一个改变。

Before compiling dlib, edit dlib's tools/python/CMakeLists.txt file from:

    set(USE_SSE4_INSTRUCTIONS ON CACHE BOOL "Use SSE4 instructions")
to:

    set(USE_SSE2_INSTRUCTIONS ON CACHE BOOL "Use SSE2 instructions")
    
然后编译并安装dlib和dlib python扩展。. Hopefully that should fix it.
```
