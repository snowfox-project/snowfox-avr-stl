snowfox-avr-stl
===============
[![GPLv3 License](.ci/badge/license-gplv3-blue.svg)](LICENSE)

<p align="center"> 
<img src=".ci/logo/snowfox-os-logo-v2.jpg">
</p>

### What?
This repository contains the SGI STL library for usage with the Snowfox embedded framework without iostreams.

### How-to-use without the Snowfox embedded framework?
Create a file `src/new.cpp` with the following content and compile it with your application.
```C++
#include <new>

void * operator new(size_t size)
{
  return malloc(size);
}

void * operator new(size_t size, void * ptr)
{
  (void)size;
  return ptr;
}

void operator delete(void * ptr)
{
  if(ptr)
  {
    free(ptr);
  }
}

void operator delete(void * ptr, size_t /* size */)
{
  return ::operator delete(ptr);
}

void * operator new[] (size_t size)
{
  return ::operator new(size);
}

void operator delete[] (void *ptr)
{
  return ::operator delete(ptr);
}

void operator delete[](void * ptr, size_t /* size */)
{
  return ::operator delete(ptr);
}
```
