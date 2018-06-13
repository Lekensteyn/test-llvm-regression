# Investigation for macOS test failure
Investigating regression after https://reviews.llvm.org/D46545

```
Building remotely on green-dragon-21 (Zorg MacPro xcode9.2 10.13.3) in workspace /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA
```

## FAIL: AddressSanitizer-i386-darwin :: TestCases/Posix/fgets_fputs.cc (623 of 3107)
Failed Build r334644 (#46117) (Jun 13, 2018 12:47:22 PM)
http://green.lab.llvm.org/green/job/clang-stage1-configure-RA/46117/

```
Script:
--
: 'RUN: at line 1';      /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/clang-build/./bin/clang  --driver-mode=g++ -fsanitize=address -mno-omit-leaf-frame-pointer -fno-omit-frame-pointer -fno-optimize-sibling-calls -gline-tables-only  -arch i386 -stdlib=libc++ -mmacosx-version-min=10.9 -isysroot /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.13.sdk  -g /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/llvm/projects/compiler-rt/test/asan/TestCases/Posix/fgets_fputs.cc -o /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/clang-build/tools/clang/runtime/compiler-rt-bins/test/asan/I386DarwinConfig/TestCases/Posix/Output/fgets_fputs.cc.tmp
: 'RUN: at line 2';   echo data > /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/clang-build/tools/clang/runtime/compiler-rt-bins/test/asan/I386DarwinConfig/TestCases/Posix/Output/fgets_fputs.cc.tmp-testdata
: 'RUN: at line 3';   not  /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/clang-build/tools/clang/runtime/compiler-rt-bins/test/asan/I386DarwinConfig/TestCases/Posix/Output/fgets_fputs.cc.tmp 1 /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/clang-build/tools/clang/runtime/compiler-rt-bins/test/asan/I386DarwinConfig/TestCases/Posix/Output/fgets_fputs.cc.tmp-testdata 2>&1 | FileCheck /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/llvm/projects/compiler-rt/test/asan/TestCases/Posix/fgets_fputs.cc --check-prefix=CHECK-FGETS
: 'RUN: at line 4';   not  /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/clang-build/tools/clang/runtime/compiler-rt-bins/test/asan/I386DarwinConfig/TestCases/Posix/Output/fgets_fputs.cc.tmp 2 2>&1 | FileCheck /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/llvm/projects/compiler-rt/test/asan/TestCases/Posix/fgets_fputs.cc --check-prefix=CHECK-FPUTS
: 'RUN: at line 5';   not  /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/clang-build/tools/clang/runtime/compiler-rt-bins/test/asan/I386DarwinConfig/TestCases/Posix/Output/fgets_fputs.cc.tmp 3 2>&1 | FileCheck /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/llvm/projects/compiler-rt/test/asan/TestCases/Posix/fgets_fputs.cc --check-prefix=CHECK-PUTS
--
Exit Code: 2

Command Output (stderr):
--
FileCheck error: '-' is empty.
FileCheck command line:  FileCheck /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/llvm/projects/compiler-rt/test/asan/TestCases/Posix/fgets_fputs.cc --check-prefix=CHECK-FPUTS
```

## PASS: AddressSanitizer-x86_64-darwin :: TestCases/Posix/fgets_fputs.cc (1064 of 3107)
Failed Build r334623 (#46109) (Jun 13, 2018 10:36:51 AM)
http://green.lab.llvm.org/green/job/clang-stage1-configure-RA/46109/

```
Script:
--
: 'RUN: at line 1';      /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/clang-build/./bin/clang  --driver-mode=g++ -fsanitize=address -mno-omit-leaf-frame-pointer -fno-omit-frame-pointer -fno-optimize-sibling-calls -gline-tables-only  -arch x86_64 -stdlib=libc++ -mmacosx-version-min=10.9 -isysroot /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.13.sdk  -g /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/llvm/projects/compiler-rt/test/asan/TestCases/Posix/fgets_fputs.cc -o /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/clang-build/tools/clang/runtime/compiler-rt-bins/test/asan/X86_64DarwinConfig/TestCases/Posix/Output/fgets_fputs.cc.tmp
: 'RUN: at line 2';   echo data > /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/clang-build/tools/clang/runtime/compiler-rt-bins/test/asan/X86_64DarwinConfig/TestCases/Posix/Output/fgets_fputs.cc.tmp-testdata
: 'RUN: at line 3';   not  /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/clang-build/tools/clang/runtime/compiler-rt-bins/test/asan/X86_64DarwinConfig/TestCases/Posix/Output/fgets_fputs.cc.tmp 1 /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/clang-build/tools/clang/runtime/compiler-rt-bins/test/asan/X86_64DarwinConfig/TestCases/Posix/Output/fgets_fputs.cc.tmp-testdata 2>&1 | FileCheck /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/llvm/projects/compiler-rt/test/asan/TestCases/Posix/fgets_fputs.cc --check-prefix=CHECK-FGETS
: 'RUN: at line 4';   not  /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/clang-build/tools/clang/runtime/compiler-rt-bins/test/asan/X86_64DarwinConfig/TestCases/Posix/Output/fgets_fputs.cc.tmp 2 2>&1 | FileCheck /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/llvm/projects/compiler-rt/test/asan/TestCases/Posix/fgets_fputs.cc --check-prefix=CHECK-FPUTS
: 'RUN: at line 5';   not  /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/clang-build/tools/clang/runtime/compiler-rt-bins/test/asan/X86_64DarwinConfig/TestCases/Posix/Output/fgets_fputs.cc.tmp 3 2>&1 | FileCheck /Users/buildslave/jenkins/workspace/clang-stage1-configure-RA/llvm/projects/compiler-rt/test/asan/TestCases/Posix/fgets_fputs.cc --check-prefix=CHECK-PUTS
--
Exit Code: 0
```
