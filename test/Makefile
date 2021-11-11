# makefile written for gnu make
CXX		= /usr/local/gcc-3.1/bin/g++ 
SRC		= ../src
CPPFLAGS	= -I$(SRC)
DEBUG		= -g
#OPTIMIZE	= -O2
GCCWARN		= -Wall -Wstrict-prototypes
CXXFLAGS	= $(DEBUG) $(GCCWARN) $(OPTIMIZE) $(INCLUDES)

LIB		= ../libXmlRpc.a

# Add your system-dependent network libs here
# Solaris: -lsocket -lnsl
SYSTEMLIBS	=

LDLIBS		= $(SYSTEMLIBS) $(LIB)

TESTS		= HelloClient HelloServer TestBase64Client TestBase64Server TestValues TestXml Validator FileClient

all:		$(TESTS) runtest

$(TESTS):	$(LIB)

.PHONY:

runtest:	$(TESTS)
		@echo Running "hello" test...
		@(./HelloServer localhost 13131 > /dev/null 2>&1 &)
		@./HelloClient localhost 13131 > /dev/null 2>&1

		@echo Running "base64" test...
		@(./TestBase64Server 13133 > /dev/null 2>&1 &)
		@./TestBase64Client localhost 13133 output.png > /dev/null 2>&1
		@shasum -s -U -a 224 -c pngcksum

		@echo Running "values" test...
		@./TestValues

		@echo Skipping "xml" test...
#		@./TestXml

		@echo Running "validator" test...
		@(./Validator 13135 > /dev/null 2>&1 &)
		@for i in *.xml; do echo "  w/ $$i" ; ./FileClient localhost 13135 $$i > /dev/null 2>&1 ; done

clean:
		@rm -rf *.o .dSYM/
		@rm -f $(TESTS) output.png
