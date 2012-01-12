  XmlRpc++ Library

   This is version 0.7 of XmlRpc++, an implementation of the [1]XmlRpc
   protocol written in C++, based upon Shilad Sen's excellent [2]py-xmlrpc
   library. XmlRpc++ is designed to make it easy to incorporate XmlRpc
   client and server support into C++ applications. Or use both client and
   server objects in your app for easy peer-to-peer support.

  Features

     * Easy   This library is easy to incorporate into C++ applications.
       No other libraries are required, other than your system's socket
       libraries. Simple XML parsing and HTTP support are built in.
     * Fast   All IO is non-blocking, so a slow client or network will not
       slow down the server.
     * Portable Written in standard C++ to the POSIX and Windows sockets
       APIs. You do need a fairly recent compiler (g++ 3.1 or MSVC++ .Net
       or MSVC++ 6 with the [3]STL patches.)
     * Free   This library is released under the [4]GNU [5]LGPL.


  Changes

     * Better handling of fault responses: server methods can throw an
       XmlRpcException to return a fault and XmlRpcClient has a new method
       to test whether the last response was a fault.
     * Support for system.listMethods and system.methodHelp from the
       introspection API.
     * Support for system.multicall to process multiple requests in a
       single transaction.
     * Fixed a problem in the XmlRpcServer destructor (it should not have
       been deleting the methods).
     * The server ensures a valid result value is returned even if the
       method does not set the result. The default result is an empty
       string.
     * Doxygen comments in header files and a doc target in the makefile.


  Installation

   There are VC++ 6 and VC++ .Net project files building on Windows. If
   you are using VC++ 6, you should apply SP3 and the fixes at
   [6]http://www.dinkumware.com/vc_fixes.html. Be sure to set the
   appropriate code generation switches. In particular, ensure that the
   runtime library (single/multi-threaded, static library/DLL) used is the
   same for the XmlRpc++ code and whatever application it will be linked
   to.

   For Linux, Solaris, and other Unix-like platforms there is a GNU
   Makefile which can be edited to suit your system. Specify your C++
   compiler, compiler flags, and your system's socket libraries.

   In the test directory there are various test programs that are built by
   default. To verify that the library built correctly, you can start the
   HelloServer example:
HelloServer 8000

   and the HelloClient example in another terminal window:
HelloClient localhost 8000

   You should see two Hello messages and a sum displayed (amongst a bunch
   of debug output). You can also try the XML server validator program
   (eg, "Validator 80") and then attempt to connect to it from
   [7]http://validator.xmlrpc.com (if you have access to the internet and
   are not behind a firewall etc).

  Author

   [8]Chris Morley

   Although no code was re-used, the design and structure of the library
   is based upon the py-xmlrpc library implementation.
   The base64 decoder/encoder is by [9]Konstantin Pilipchuk.

  License

   A full copy of the LGPL license is included in the file COPYING. The
   source code is Copyright (c) 2002-2003 by Chris Morley. This library is
   free software; you can redistribute it and/or modify it under the terms
   of the GNU Lesser General Public License as published by the Free
   Software Foundation; either version 2.1 of the License, or (at your
   option) any later version. This library is distributed in the hope that
   it will be useful, but WITHOUT ANY WARRANTY; without even the implied
   warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See
   the GNU Lesser General Public License for more details. You should have
   received a copy of the GNU Lesser General Public License along with
   this library; if not, write to the Free Software Foundation, Inc., 59
   Temple Place, Suite 330, Boston, MA 02111-1307 USA

References

   1. http://www.xmlrpc.org/
   2. http://py-xmlrpc.sourceforge.net/
   3. http://www.dinkumware.com/vc_fixes.html
   4. http://www.gnu.org/
   5. http://www.gnu.org/copyleft/lesser.html
   6. http://www.dinkumware.com/vc_fixes.html
   7. http://validator.xmlrpc.com/
   8. mailto:cmorley@users.sourceforge.net
   9. mailto:lostd@ukr.net
