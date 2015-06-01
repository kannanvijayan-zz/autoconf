
bin_PROGRAMS = test
AM_CXXFLAGS = -Wall -std=c++14
if DEBUG
  AM_CXXFLAGS += -g -O0 -gdwarf-4
endif
if WARNERR
  AM_CXXFLAGS += -Werror
endif

shared_cpp = \
    test.cpp \

test_SOURCES = \
    $(shared_cpp) \
    test/test.cpp
