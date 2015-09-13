XMLCC C++ XML library for SAX & DOM
===================================
A C++ XML library for SAX & DOM.

README
------
XMLCC is a C++ library for the extensible markup language (XML). It is strongly
object-oriented and based on software design patterns for generating, searching,
and parsing even malformed XML files.

Two parsers are available: a simple API for XML (SAX) parser for an event based
parsing and a document object model (DOM) parser generating an object model
tree.

This library is - yet - a non validating, not speed optimized, and explicit not
dealing with file encodings; those are overcome by C++'s local standard template
libraries (STL). It just provides an easy access to XML files.

LICENSE
-------
XMLCC is distributed under the MIT License (MIT); this file is part of.

Copyright (c) 2008-2015 Christian Scheiblich (cscheiblich@gmail.com)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

CHANGELOG
---------
XMLCC is in version 1.00 20150101 Amara Faith:

2015XXXX version 1.XX :
- changed Makefile from subversion (svn) to git
- added search() methods to DOM::Controller; searching up to seven hierarchies
- CFG::Config class
 - first attempt for getting information from config DOM tree
 - implemented getters for section Config, Info, and System
- TEST::Test class
 - added config file reader
 - implemented reading boolean values for test run
- SYS::Exception removed the "SYS::Excpetion::" water marking
 - added / updated comments & minor changes in SYS::List<T>() template class 

20150101 version 1.00 :
- Release of version 1.00
- changed copyright in the MIT License (MIT) to new year 2015
- publicated at https://github.com/cscheiblich/xmlcc for swarm development

20141231 version 0.95 :
- added getTag() to class Node for receiving XML tag recursively as std::string
- DOM::Controller is extended by
 - erase() for deleting Node*; safe
 - view() for printing Node* to std::cout; skipping '\n'@end
 - write() for writing an XML DOM tree or any XML structure (Node*)
 - removed static doTag() while ported to Node*
- DOM::Tokenizer is extended by
 - buildDomTreeOfTagList() for building DOM tree by given list of strings
 - convert XML tag to DOM Node* object recursively
- DOM::Core is extened by
 - parseFile2TagList() for reading file to list of strings; XML tags
 - parseFile2DomTree() for rading file to DOM tree; passing back a Root* (Node*)
 - buildDomTreeOfTagList() for building DOM tree for any XML structure; by Node*
- cleaned code due to old exmaples

20141230 version 0.94 :
- added namespace CFG::
 - added class Config
  - generates xmlcc's configuration file using DOM::
  - writes xmlcc's configuration file by DOM::
  - reads xmlcc' configuration with DOM::Parser( DOM::Handler )
- hacked on DOM::Controller
 - better functionality of support methods
 - renamend methods for better functionality and in better code style
  - isComment( Node* ), isElement(), isValue, and so on ..
  - genArrOfComments( ) and genListOfComments( ) instead get..( )
  - added static method doTag( Node* ) for converting to XML tag
- added TEST::Controller for unit tests of DOM::Controller
 - added tests the mainly used methods class
 - added tests for XML tag generation by static doTag() method
 - not 100 % test verfication provided yet
- added generation of a DOM:: example for html web page to main()
 - view it by std::cout << xml << ..
 - write it by std::fstream << xml << ..
 - added 'using namespace XMLCC;'
- XMLCC is keeping namespaces DOM::, SAX::, and CFG::; (SYS:: & TEST::)

20141229 version 0.93 :
- ported complete namespace OBJ:: to namespace DOM::
 - deleted namespace OBJ::
 - cleaned all code due to XMLCC::DOM:: ..

20141229 version 0.92 :
- namespace OBJ::
 - (!) renamed class OBJ::Object* to class OBJ::Node*
  - typedef available as XMLCC::Node* & XMLCC::NodeList*
 - moving methods from DOM::Grabber to OBJ::Controller
  - deleted DOM:Grabber
 - moved Types:: to OBJ::Types::

20141229 version 0.91 :
- changed XMLCC's license from 'Apache 2.0' to 'The MIT License (MIT)'
- minor bug fixes
- namespace OBJ::
 - moved DOM::Viewer to OBJ::Viewer
 - moved DOM::Writer to OBJ::Writer

20141228 version 0.90 :
- xmlcc's package name 'Elsie Fox'
- rehacked XML parser
 - SYS::XmlParser keeping algorithm for filtering XML tags
  - SYS::XmlHandler called by parser in known SAX implemenation
   - startDoc( ) method is called directly before reading first character
   - startTag( Str tag ) method is called by < >, < />, <? ?> or <!-- -->, etc.
   - characters( Str txt ) method is called by each value or text > .. < 
   - endTag( Str tag ) method is called by each ending tag </ >
   - endDoc( ) method is called directly after reading last character
  - TEST::XmlParser Test; still to be implemented
 - DOM::Parser using SYS::XmlParser by implementing an own handler in static way
  - DOM::Handler inherits from SYS::XmlHandler and fills smart array XmlList*
  - rehacked Exception handling
 - SAX::Parser using SYS::XmlParser
  - SAX::Handler is available for own handler implementations by inheritance
   - startDoc( ), startTag( tag ), characters( txt ), endTag( tag ), endDoc( )
  - Sax::HandlerExample is printing out an XML file by using one indentation
  - rehacked Exception handling
- renamed XMLCC::String to XMLCC::Str
 - renamed class SYS::StringTool to SYS::StrTool
 - renamed class TEST::StringTool to TEST::StrTool
- moved XMLCC::Builder to OBJ::Builder
- start implementing unit tests for SYS::StrTool
- added memory optimization of smart list in DOM::Parser
- cleaned main.cpp, due to keeping commented code

20141223 version 0.80 :
- xmlcc's package name 'Melany Zax'
 - from WWW: http://www.namegenerator.biz/female-name-generator.php
- added simple unit test case framework
 - added unit tests for SYS::List<T>; smart array template class
 - added unit tests for SYS::XmlTool; formats malformed XML tags
 - added unit tests for SYS::StrTool; easy going with std::string and char*
 - added unit tests for DEV::Tokenizer; mapping XML tags 2 XMLCC::Objects 
 - added class for XMLCC::; moved methods from main() to unit test case class
- rehacked the DOM (Document Object Model) parser
 - bug fixes for some malformed MXL tags
 - added more flexibility by separating functionality to different classes
- extended Makefile by a make refresh for cleaning, an update, and a build
- switched IDE for developing
 - kicked all Microsoft Visual Studio projects files; not necessary anymore
 - added eclipse CDT projects files and cleaned subversion control files
 - still updating Makefile for having a build and quick check; on raspbian e.g.
 - removed the SAX parser while it has to be rehacked; no need for at moment

20141122 version 0.73 :

Started a new dev parser with xml file 2 tag list 2 tokenizer 2 objects strategy
- added XMLCC::DEV::Cleaner class
 - added remove and add spikes methods
 - added check4Tag, ..4Starting, ..4Ending, ..4StanAlone returning boolean
 - added check4Header, ..4Comment, and ..4CDATA returning boolean

20130904 version 0.72 :

Compiled, fixed, and tested on rapberian GNU/Linux using gxx 4.6.3.

20130209 version 0.71 :
- Updated copyright information towards 2012 and removed old email address
- Added constructors to XMLCC::OBJ::Element to support an infinite number of
  objects (XMLCC::OBJ::Attribute, ..::Comment, ..::CDATA, and ..::Element)
  at generating an XML structure but one has to give the number of Elements
  yet if there are more than 20 objects passed.
- Added methods for each section to be parsed but actually not in a very elegant
  way.

20100812 version 0.70 :
- New package release called: Vivian Creighton
- Added overloaded constructors to XMLCC::OBJ::Element for directly building
  XML structure with elements, Attributes and Comments; see:
  http://www.hookedonlinq.com/LINQtoXML5MinuteOverview.ashx
  - Easy generation of XML and HTML files using object constructors directly
  - Added support for std::cout << object << std::flush; and support for
    std::fstream file; ...   file << object << std::flush; by overloading
    std::ostream operator << ( std::ostream&, .. ) operator
  - Rehacked examples in main method
  - Removed class XMLCC::DOM::Dumper while is became obsolete
  - Rehacked classes XMLCC::DOM::Writer and XMLCC::DOM::Viewer; actually they
    are obsolete too
- Added support for <!DOCTYPE .. > for generating and parsing HTML in
  XMLCC::DEV::Parser but parsing is still in development
- Added support fot <![CDATA[ .. ]]> for generating and parsing RSS in
  XMLCC::DEV::Parser but parsing is still in development


20100808 version 0.67 :
- Implemented whole new logic based on more booleans within XMLCC::DEV::Parser
  later allowing for XML syntax check and parsing <![CDATA[ .. ]]> sections

20100808 version 0.66 :
- added header file xmlccDefines.h for common STL includes and common typedefs
  for XMLCC::
- Restructed all includes of headers
- updated internal template List XMLCC::SYS::List<T> for data storage. 
  Therefore, the void store( T ) method renames to void add( t )
- Renamed storeObejct to addObject( ) for the complete project
- Renamed tyedef ObjectList to ObjectList
- Renamed typedef StrList to StrList
- Added horizontal spacers to all headers
- Reformatted class XMLCC::DOM::Tokenizer for a clearer source
- renamed RSS 2.0 file to xmlccFeed.rss 

20100727 version 0.65 :
- Added a second Microsoft Visual Studio 2005 project called 'Example' keeping
  several examples in a main.cpp
- Changed main project 'XMLCC' to be compiled as a static .lib file and linked
  then

20100116 version 0.64 :
- fixed bug of missing include for g++ compiler
- added file support to main function
 - binary xmlcc can be called like: xmlcc <fileName.xml>
 - the file fileName.xml is parsed an printed to console out
 - indentation is set to two whitespaces
 - can be used to reformat xml or html files
 - try in dir trunk/XMLCC: ./xmlcc XMLCC.vcproj ; is an XML file too ~8> 
- removed the MSDOS ending tags from Makefile using flip -u <file>
- added to SAX parser the parsing from a buffer (char* or std::string)

20090926 version 0.63 :
- changed License to the Apache License, Version 2.0

20090926 version 0.62 :
- renamed XMLCC::DOM::Sorter to XMLCC::DOM::Grabber
- added class XMLCC::SYS::Str and
- added MS Visual Studio 2005 Project files including AnkhSVN Config for plugin
- ported Project to http://code.google.com/p/xmlcc
- added subversion repository at code.google.com
- try: svn checkout http://xmlcc.googlecode.com/svn/trunk/ xmlcc-read-only
- added remarks for new development users ...

20090515 version 0.61 :
- added a new class named DOM::BUFFER which reads from a std::string and
  returns a XMLCC::Object* of type XMLCC::ROOT* keeping all XML syntax
- renamed class DOM::Converter 2 DOM::Tokenizer in case of better naming
- added 80 sign comment bars for grouping code
- changed includes in headers due to defines for compiler
- added comments at DOM:: class
- added DEV namespace for new developemetns and tryouts
 - added a parser 2 DEV for splitting it to functions
- reprogramed at DEV namespace the parser with common member vars and functions
  for files and buffers
- added get functions to DOM::Grabber for getting values and attributes from
  an object
- extended example in main
- bug fix for empty attributes in class Builder
- added directory XMLCC keeping xmlccMalformed.xml and newFeed.rss for execution
  test binary xmlcc

20090106 version 0.60 :
- added two sub name spaces DOM and SAX to group new functionality
 - renamed several files -> *Dom* & *Sax*
 - renamed several classes -> DOM:: & SAX::
- added name space OBJ for the multidim composite pattern
 - renamed several files -> *Obj*
 - renamed several classes -> OBJ::
- added name space ERR for the exceptions, errors, and failures
 - renamed several files -> *Err*
 - renamed several classes -> SYS::
- added name space SYS for stringTools ans template List<T>
 - renamed several files *Sys*
 - renamed several classes -> SYS::
- changed internal structure of class Object*
 - renamed functions get( % ) -> getObject( % )
 - renamed functions store( % ) -> storeObject( % )
 - renamed functions size( % ) -> getNoOfObjects( % )
 - renamed functions arr( % ) -> getObjects( % )
 - changed to protected member for the list of Object* objects

20081207 version 0.52 :
- created subversion repository for XMLCC MSVS 2005 project
- added test and by the way an example for class XMLCC::List<T> 
- fixed bug in XMLCC::List<T>::ins( ) function
- added some 80 symbol spacers for better overview in VIM editor
- replaced copyright symbol with (C)

20081115 version 0.51 :
- fixed bugs
  - tags could now store a single comment only
  - exception handling bug is removed for correct line numbers
- added class Dumper as base class for Viewer and Writer
 - migrated double functinonality 2 one single class Dumper
 - Viewer and Writer are changed to single output functions
 - Now dumping data can be easily extended
- reprocessed some comments
- changed example for catching exceptions

20081114 version 0.50 :
- new package release called Jenell Oz
- added an event based parser and an handler as an API
 - API like the one known from XML SAX Java Parser
 - create an own handler to handle the parsed data at each event
 - added an example for a console out to shown functionality of the parser
 - the event based API Parser is leightweigted and not a memory eater so
- extended main function for an API Parser example
- added and fixed some comments
- fixed minor bugs

20081109 version 0.43 :
- the parser is extended towards exceptions
 - added try catch block to handle exceptions
 - parser hands back line number and char position if xml syntax is corrupted
 - parser is getting intelligent; tells about wrong tags and where
- renamed some internal function of class Converter and extended exceptions
- extended malformed xml file xmlccMalformed.xml

20081103 version 0.42 :
- the parser (class Parser) is extended
 - can read mixed tags now
 - also allows any char in a value of an attribute, eg. < or >
 - more logic is put to the parser, to check while parsing
- class Writer and class Viewer are reimplemented
 - main recursive functions are reimplemented and simpilied
 - supports a simpler logic and a fast drive on huge xml files
- the << operator is overload as a friend for class Object
 - can push an object or a pointer to an object to std::cout
 - internal function for getTag() is renamed to neutral getStr()
- internal extra class Error::Exception is migrated to XMLCC::Exception
- minror bugs were found and fixed
 - more logic to the convert functions of attributes with values
 - meta object functions are not necessary yet and were removed

20081102 version 0.41 :
- the parser (Parser) and the Converter are revised
 - Parser class received more logic for parsing elements
   keeping attributes like: att="><val><" and att=""
 - Converter checks with more logic for faults
- changed xmlccMalformed.xml for a harder example
- fixed minor bugs; comments
- TODO: tags in "multi-elements" keep their position; see xmlccMalformed.xml

20081029 version 0.40 :
- fixed minor bugs
- the parser is revised
 - parser can read break lines
 - parser is not fixed to syntax
  - can read <   !  -    -   -- ! >
  - can read <   ?     ? >
  - can read < tag   >    <  / tag >
 - attributes whitespaces are now saved
 - values whitespaces are now saved
- aded search functions
 - search for no of tags in XML structure
 - search for no of values in XML structure
 - search for no of tags with value in XML structure
 - search for objects keeping a tag
 - search for objects keeping a value
 - search for objects keeping a tag with a value

20081028 version 0.31 :
- fixed minor bugs
- the parser is revised
 - some bugs are fixed
 - functions are sorted
 - comments are added
 - added some more exceptions
- strongly malformed XML files can be read

20081026 version 0.30 :
- a prototype of the parser is ready
 - supports placed comments
 - supports standalone tags
 - tabulators are supported
 - ATTENTION: white spaces in arguments are not supported yet
 - ATTENTION: white spaces in values are not supported yet
- fixed minor bugs
- added more comments

20081025 version 0.20 :
- changes values from being Strs 2 XMLCC::Objects
 - added multiple values
 - allows for writing mixed values/tags later
- reimplemented new versions or Writer and Viewer
- fixed minor bugs

20081024 version 0.12 :
- XMLCC::Root represents a file now
- fixed minor bugs

20081022 verison 0.11 :
- added file open and closing
- some bugs were fixed

20081020 version 0.10 :
- created software project XMLCC
- added basic object model; root, header, element, comment, ..