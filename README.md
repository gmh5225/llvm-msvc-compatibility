
# LLVM_MSVC_Compatibility
This project was aimed to be used for llvm-msvc [[link]](https://github.com/NewWorldComingSoon/llvm-msvc-build)

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



# 5.lld/COFF/Driver.cpp

Problem:
```C++
1>lld-link : error : could not open '/RELEASE': no such file or directory
1>lld-link : error : could not open '/kernel': no such file or directory
1>lld-link : error : could not open '/pdbcompress': no such file or directory
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0005-MSVC-Compatibility.patch)



# 6.lld/COFF/SymbolTable.cpp

Problem:
```C++
1>lld-link : error : duplicate symbol: g_GlobalNotifyRecord
1>>>> defined at x64\Debug\Broadcast.obj
1>>>> defined at x64\Debug\Vpid.obj
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0006-MSVC-Compatibility.patch)



# 7.clang/include/clang/Driver/Options.td

Problem:
```C++
Null ptr is invalid.
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0007-MSVC-Compatibility.patch)



# 8.lld/COFF/Writer.cpp

Problem:
```C++
Unused IMAGE_DLL_CHARACTERISTICS_TERMINAL_SERVER_AWARE
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0008-MSVC-Compatibility.patch)



# 9.llvm/lib/Transforms/Scalar/LoopIdiomRecognize.cpp

Problem:
```C++
#define ZERO_MEMORY(addr,size) while (size-->0)\
								{\
									*addr++ = 0;\
								}\
->>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
will be optimized to 'memset'.
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0009-MSVC-Compatibility.patch)



# 10.clang/lib/Parse/ParseDecl.cpp clang/lib/Parse/ParseDecl.cpp

Problem:
```C++
template <typename R, typename... Args>
struct MyTestTemplate;

template <typename R, typename... Args>
struct MyTestTemplate<R(__stdcall)(Args...)>
{
};
->>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
error : function cannot return function type 'R (Args...)'
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0010-MSVC-Compatibility.patch)



# 11.clang/tools/driver/driver.cpp

Problem:
```C++
 __m128i x1, x2;
 __m128i x3 = _mm_shuffle_epi8(x1, x2);
 ->>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
 _mm_shuffle_epi8 needs '-mssse3'
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0011-MSVC-Compatibility.patch)



# 12.lld/COFF/Driver.cpp

Problem:
```C++
#pragma comment(linker, "/ALIGN:0x10000")
->>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
Error:/ALIGN: is not allowed in .drectve
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0012-MSVC-Compatibility.patch)



# 13.clang\include\clang\Basic\DiagnosticSemaKinds.td

Problem:
```C++
error : invalid application of 'sizeof' to an incomplete type 'xxx'
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0013-MSVC-Compatibility.patch)



# 14.clang\include\clang\Basic\DiagnosticSemaKinds.td

Problem:
```C++
error : static_cast from a to b, which are not related by inheritance, is not allowed
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0014-MSVC-Compatibility.patch)



# 15.clang/lib/Lex/TokenLexer.cpp

Problem:
```C++
#define MY_TEST 6
#define TEST_222(major) (0x##major)
int
main()
{
    int test2 = TEST_222(MY_TEST);
    return 0;
}
->>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
error : invalid suffix 'xMY_TEST' on integer constant
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0015-MSVC-Compatibility.patch)



# 16.clang/lib/Basic/SourceManager.cpp

Problem:
```C++
1>util\log.c(492,10): fatal error : UTF-16 (LE) byte order mark detected in 'util/ioctl.inc', but encoding is not supported
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0016-MSVC-Compatibility.patch)



# 17.clang/lib/Lex/TokenLexer.cpp

Problem:
```C++
#define DBGKP_FIELD_FROM_IMAGE_OPTIONAL_HEADER(hdrs, field) ((hdrs)->OptionalHeader.##field)
CreateThreadArgs->StartAddress = UlongToPtr(
                            DBGKP_FIELD_FROM_IMAGE_OPTIONAL_HEADER((PIMAGE_NT_HEADERS32)NtHeaders, ImageBase) +
                            DBGKP_FIELD_FROM_IMAGE_OPTIONAL_HEADER(
                                (PIMAGE_NT_HEADERS32)NtHeaders, AddressOfEntryPoint));
->>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>				
error : pasting formed '.AddressOfEntryPoint', an invalid preprocessing token [-Winvalid-token-paste]
```

[Patch](https://github.com/gmh5225/LLVM_MSVC_Compatibility/blob/main/0017-MSVC-Compatibility.patch)





