# ExceptionHandler
This is a class to handle unhandled exceptions in a Windowns application. This is entirely based on [Jerry Coffin's](https://www.elastic.co/downloads/elasticsearch) code. This is just a slightly modified and easier to read version. All credit goes to Jerry Coffin. Thanks Jerry!

#How to use
```
#include "ExceptionHandler.h"

LONG Win32FaultHandler(struct _EXCEPTION_POINTERS *ExInfo);
int main()
{
    SetUnhandledExceptionFilter((LPTOP_LEVEL_EXCEPTION_FILTER)Win32FaultHandler);
    std::string *str = nullptr;
    std->append("s");
    return 0;
}

LONG Win32FaultHandler(struct _EXCEPTION_POINTERS *ExInfo)
{
    std::cerr << FileLogger::LogType::LOG_ERROR << filterCrash(ExInfo);
    return EXCEPTION_EXECUTE_HANDLER;
}
```
