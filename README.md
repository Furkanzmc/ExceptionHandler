# ExceptionHandler
This is a class to handle unhandled exceptions in a Windowns application. This is entirely based on [Jerry Coffin's](http://stackoverflow.com/questions/15372962/in-the-handler-of-setunhandledexceptionfilter-how-to-print-a-stacktrace) code. This is just a slightly modified and easier to read version. All credit goes to Jerry Coffin. Thanks Jerry!

#How to use
Don't forget to build the project with debug info.
With CMake, use `-DCMAKE_BUILD_TYPE=RelWithDebInfo`
```
#include "ExceptionHandler.h"

LONG Win32FaultHandler(struct _EXCEPTION_POINTERS *ExInfo);
int main()
{
    SetUnhandledExceptionFilter((LPTOP_LEVEL_EXCEPTION_FILTER)Win32FaultHandler);
    std::string *str = nullptr;
    str->append("s");
    return 0;
}

LONG Win32FaultHandler(struct _EXCEPTION_POINTERS *ExInfo)
{
    std::cerr << filterCrash(ExInfo);
    return EXCEPTION_EXECUTE_HANDLER;
}
```
*Output:*
```
Walking stack.
0: main -> c:\users\furkanzmc\sourcetree\matchingjungle\proj.win32\main.cpp(20)
1: __tmainCRTStartup -> f:\dd\vctools\crt\crtw32\dllstuff\crtexe.c(626)
2: BaseThreadInitThunk -> 
3: RtlInitializeExceptionChain -> 
4: RtlInitializeExceptionChain -> 
End of stack walk.
```
