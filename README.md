# LLVM_MSVC_Compatibility
LLVM_MSVC_Compatibility

1.clang/lib/sema/SemaExpr.cpp
Problem:
```C++
if (StrStr(windows_name_, pInfo->windows_name_) > 0)
```
Patch:
