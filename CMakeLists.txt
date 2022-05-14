cmake_minimum_required(VERSION 3.20)

project(pyabc_extension)

include(cmake/pyabc.cmake)
add_subdirectory(external/pybind11 EXCLUDE_FROM_ALL)

add_subdirectory(abc EXCLUDE_FROM_ALL)

set(ZZ_USE_EXTERNAL_LIBABC TRUE)
add_subdirectory(abc-zz EXCLUDE_FROM_ALL)
add_subdirectory(pyabc EXCLUDE_FROM_ALL)

# install_python_module(pyzz/pyzz)
install_python_module(pyabc/pyabc)
install_python_module(pyaig/src/pyaig)
install_python_module(pyliveness)

install_target(abc DESTINATION bin)
install_target(bip.exe DESTINATION bin RENAME bip)

# install_target(_pyzz DESTINATION lib/pyzz)
install_target(_pyabc DESTINATION lib/pyabc)
