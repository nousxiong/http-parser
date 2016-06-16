# http-parser
nodejs/http-parser 's cpp port, base on nodejs/http-parser 2.5.0

nodejs/http-parser: https://github.com/nodejs/http-parser

Changes
--------

* http_parser.c change to http_parser.cpp
* http_parser.h remove all integer typedef, instead stdint.hpp
* add stdint.hpp for fit vc <= 11
* add HTTP_HEADER_ONLY macro for making lib to header only, optional

Usage
--------

cmake -G "xxx" 

example for vc9:

* cd [your http_parser src dir]
* cmake -G "Visual Studio 9 2008"
* open http_parser.sln and build everything(static library)
* include http_parser.h/stdint.hpp to your project and link http_parser.lib

If want to use header only mode:

* Copy http_parser.h, http_parser.cpp and stdint.hpp to your project's include dir
* Define HTTP_HEADER_ONLY before include http_parser.h
