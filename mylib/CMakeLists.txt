add_library(mylib MyLib.cpp)
install(TARGETS mylib DESTINATION lib)
install(FILES Mylib.h DESTINATION include)
