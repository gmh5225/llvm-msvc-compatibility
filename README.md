# 1.clang/lib/sema/SemaExpr.cpp 

Problem:
```C++
if (StrStr(windows_name_, pInfo->windows_name_) > 0)
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0001-MSVC-Compatibility.patch)



# 2.clang/include/clang/Lex/Preprocessor.h clang/lib/Lex/PPMacroExpansion.cpp

Problem:
```C++
printf(__FUNCTION__ "Hello, world!\n");
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0002-MSVC-Compatibility.patch)

  
  
# 3.lld/COFF/Writer.cpp

Problem:
```C++
Fix the characteristics of some sections like ".voltbl". Or the program will be crash sometimes.
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0003-MSVC-Compatibility.patch)



# 4.clang/lib/AST/ASTContext.cpp

Problem:
```C++
void OutputTrace(int place_holder, ...)
{
	va_list args;
	va_start(args, place_holder);
	bool unicode = va_arg(args, bool);
}
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0004-MSVC-Compatibility.patch)


