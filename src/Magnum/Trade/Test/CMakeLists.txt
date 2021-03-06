#
#   This file is part of Magnum.
#
#   Copyright © 2010, 2011, 2012, 2013, 2014, 2015, 2016
#             Vladimír Vondruš <mosra@centrum.cz>
#
#   Permission is hereby granted, free of charge, to any person obtaining a
#   copy of this software and associated documentation files (the "Software"),
#   to deal in the Software without restriction, including without limitation
#   the rights to use, copy, modify, merge, publish, distribute, sublicense,
#   and/or sell copies of the Software, and to permit persons to whom the
#   Software is furnished to do so, subject to the following conditions:
#
#   The above copyright notice and this permission notice shall be included
#   in all copies or substantial portions of the Software.
#
#   THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
#   IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
#   FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL
#   THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
#   LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
#   FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
#   DEALINGS IN THE SOFTWARE.
#

if(CORRADE_TARGET_EMSCRIPTEN OR CORRADE_TARGET_ANDROID)
    set(TRADE_TEST_DIR ".")
    set(TRADE_TEST_OUTPUT_DIR "./write")
else()
    set(TRADE_TEST_DIR ${CMAKE_CURRENT_SOURCE_DIR})
    set(TRADE_TEST_OUTPUT_DIR ${CMAKE_CURRENT_BINARY_DIR})
endif()

configure_file(${CMAKE_CURRENT_SOURCE_DIR}/configure.h.cmake
               ${CMAKE_CURRENT_BINARY_DIR}/configure.h)

corrade_add_test(TradeAbstractImageConverterTest AbstractImageConverterTest.cpp LIBRARIES Magnum)
target_include_directories(TradeAbstractImageConverterTest PRIVATE ${CMAKE_CURRENT_BINARY_DIR})
corrade_add_test(TradeAbstractImporterTest AbstractImporterTest.cpp
    LIBRARIES Magnum
    FILES file.bin)
target_include_directories(TradeAbstractImporterTest PRIVATE ${CMAKE_CURRENT_BINARY_DIR})
corrade_add_test(TradeCameraDataTest CameraDataTest.cpp LIBRARIES Magnum)
corrade_add_test(TradeImageDataTest ImageDataTest.cpp LIBRARIES Magnum)
corrade_add_test(TradeLightDataTest LightDataTest.cpp LIBRARIES Magnum)
corrade_add_test(TradeMaterialDataTest MaterialDataTest.cpp LIBRARIES Magnum)
corrade_add_test(TradeMeshData2DTest MeshData2DTest.cpp LIBRARIES Magnum)
corrade_add_test(TradeMeshData3DTest MeshData3DTest.cpp LIBRARIES Magnum)
corrade_add_test(TradeObjectData2DTest ObjectData2DTest.cpp LIBRARIES Magnum)
corrade_add_test(TradeObjectData3DTest ObjectData3DTest.cpp LIBRARIES Magnum)
corrade_add_test(TradeSceneDataTest SceneDataTest.cpp LIBRARIES Magnum)
corrade_add_test(TradeTextureDataTest TextureDataTest.cpp LIBRARIES Magnum)
