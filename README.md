# LLVM MSVC Compatibility

1.clang/lib/sema/SemaExpr.cpp
Problem:
```C++
if (StrStr(windows_name_, pInfo->windows_name_) > 0)
```
[Patch:](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0001-MSVC-Compatibility.patch)

