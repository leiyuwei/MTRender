set ( common_src Source/esShader.cpp 
                 Source/esShapes.cpp
                 Source/esTransform.cpp
                 Source/esUtil.cpp
				 Source/ThreadBufferESDevice.cpp
				 Source/ThreadESDeviceBase.cpp
				 Source/ESDevice.cpp
				 Source/ThreadESDevice.cpp
				 Source/Mesh.cpp
				 Source/DemoBase.cpp
				 Source/RingBuffer.cpp)


# Win32 Platform files
if(WIN32)
    set( common_platform_src Source/Win32/esUtil_win32.cpp )
    add_library( Common STATIC ${common_src} ${common_platform_src} )
    target_link_libraries( Common ${OPENGLES3_LIBRARY} ${EGL_LIBRARY} )
else()
    find_package(X11)
    find_library(M_LIB m)
    set( common_platform_src Source/LinuxX11/esUtil_X11.c )
    add_library( Common STATIC ${common_src} ${common_platform_src} )
    target_link_libraries( Common ${OPENGLES3_LIBRARY} ${EGL_LIBRARY} ${X11_LIBRARIES} ${M_LIB} )
endif()

             


