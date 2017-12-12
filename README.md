# jemalloc.NET: A native memory manager for .NET

![jembench](https://lh3.googleusercontent.com/9zFHRdddwBezYJGb2jgMGHT3lgDTFmBAcJ_s8NgOdmAF1nz1-sF-0p9ZMOjeFVc-HAJHMRyLNmO02aHjWL8F9JWlqPHmiypdcmDhSx8SK8unzENOE7sG7ZCEOZLvI5nSTk_H8DpKoQ=w958-h521-no)
jemalloc.NET is a .NET API over the [jemalloc](http://jemalloc.net/) native memory allocator which provides .NET applications with efficient data structures backed by native memory for large scale in-memory computation scenarios. jemalloc is "a general purpose malloc(3) implementation that emphasizes fragmentation avoidance and scalable concurrency support" that is [widely used](http://highscalability.com/blog/2015/3/17/in-memory-computing-at-aerospike-scale-when-to-choose-and-ho.html) in the industry, particularly in [applications](http://highscalability.com/blog/2015/3/17/in-memory-computing-at-aerospike-scale-when-to-choose-and-ho.html) that must scale and utilize large amounts of memory. In addition to its fragmentation and concurrency optimizations, jemalloc provides an array of developer options for debugging, monitoring and tuning allocations that make it a great choice for use in developing memory-intensive applications. 

The jemalloc.NET project provides:
* A low-level .NET API over the native jemalloc API functions like je_malloc, je_calloc, je_free, je_mallctl...
* A safety-focused high-level .NET API providing data structures like arrays backed by native memory allocated using jemalloc.
* A benchmark CLI program: `jembench` for easily benchmarking operations on native data structures vs managed objects using different parameters.

Data structures provided by the high-level API are more efficient than managed .NET arrays and objects at the scale of millions of elements and memory allocation is more resistant to fragmentation. Large .NET arrays must be allocated on the Large Object Heap which leads to fragmentation and lower performance. Managed .NET arays are also limited to Int32 indexing which puts a maximum size on arrays at about 2.5 billion elements. jemalloc provides huge arrays through the `HugeArray<T>` class which allows you to access all available memory as a flat contiguous buffer using array semantics.

In a .NET application jemalloc.NET native arrays and data structures can be straightforwardly accessed by native libraries without the need to make additional copies. Buffer operations can be SIMD-vectorized which can make a significant performance difference for huge buffers with 10s of billions of values. 

The goal of the jemalloc.NET project is to make accessible to .NET the kind of big-data in-memory numeric, scientific and other computing that typically would require coding in a low=level language like C/C++ or assembler.



## Installation



## Usage

Currently build instuctions are only provided for Windows x64


## Building from source

### Requirements

[Visual Studio 2017 15.5](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#15.5.1)
with at least the following components:
* C# 7.2 compiler
* .NET Core 2.0 SDK
* VC++ 2017 compiler toolset v141 or higher
* Windows 10 SDK for Desktop C++ version 10.0.10.15603 or higher

### Steps
1. Clone the project: `git clone https://github.com/alllisterb/jemalloc.NET`
2. From a Visual Studion 2017 Developer Command prompt run `build.cmd`. The solution should be built without