TOP = ../..
include $(TOP)/scripts/Makefile.common

SRCS=versionString.cpp Globals.cpp
OBJS = $(SRCS:.cpp=.o)
CFLAGS += -I$(MTL) -I$(SOLVER_INCLUDE)

LIBS = 	-L../STPManager -lstpmgr \
	-L../absrefine_counterexample -labstractionrefinement \
	-L../to-sat -ltosat \
	-L../simplifier -lsimplifier \
	-L../printer -lprinter \
	-L../AST -last \
	-L../extlib-constbv -lconstantbv \
	-L../sat -lminisat  \
	-L../parser -lparser \
	-L../extlib-abc -labc 	
	
# This rebuilds each time, because the target "parser" is not created
# Until the dependencies on each of the libraries is included, that's safest.
parser:  $(OBJS) depend
#	$(CXX) $(CXXFLAGS) -I$(MTL) $(LDFLAGS) $(OBJS) $(LIBS) -o stp
#	@mv stp ../../bin/stp

#.PHONY: clean
clean:	
	rm -rf *.o *~ *.a .#* depend versionString.cpp

# Use svnversion to output the global revision number. 
# This will be updated every time make is called. 
# Because main.cpp depends on this, 
# it will in turn be rebuilt every time.
versionString.cpp:
	@echo "#include <string>"  > versionString.cpp
	@echo "namespace BEEV{extern const std::string version=\"" $(shell svnversion ..) "\";}" >> versionString.cpp

ALWAYS_RUN:


depend: $(SRCS)
	@$(CXX) -MM $(CXXFLAGS) $(SRCS) > $@



#-include depend
