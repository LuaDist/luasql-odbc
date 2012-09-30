# Copyright (C) 2007-2012 LuaDist.
# Created by Peter Kapec
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

project ( luasql C )
cmake_minimum_required ( VERSION 2.8 )
include ( cmake/dist.cmake )
include ( lua )

find_package ( ODBC REQUIRED )
include_directories ( ${ODBC_INCLUDE_DIRECTORIES} src )

if ( UNIX )
  add_definitions ( -DUNIXODBC )
endif ( )

install_lua_module ( luasql.odbc src/ls_odbc.c src/luasql.c LINK ${ODBC_LIBRARIES} )
