cmake_minimum_required(VERSION 3.3.0)

project(pyabc_extension)

include(cmake/pyabc.cmake)

set(ABC_USE_NAMESPACE pyabc)

add_subdirectory(abc EXCLUDE_FROM_ALL)
add_subdirectory(abc-zz EXCLUDE_FROM_ALL)
add_subdirectory(pywrapper EXCLUDE_FROM_ALL)
add_subdirectory(pyzz EXCLUDE_FROM_ALL)
add_subdirectory(pyabc EXCLUDE_FROM_ALL)

install_python_module(pyzz/pyzz)
install_python_module(pyabc/pyabc)
install_python_module(pyaig/src/pyaig)
install_python_module(pyliveness)

install_target(abc DESTINATION bin)
install_target(bip.exe DESTINATION bin RENAME bip)

install_target(_pyzz DESTINATION lib/pyzz)
install_target(_pyabc DESTINATION lib/pyabc)

pyabc_install_support_libraries(_pyzz)
