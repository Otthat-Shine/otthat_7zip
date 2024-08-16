cmake_minimum_required(VERSION 3.18)
project(otthat_7zip)

set(CMAKE_CXX_STANDARD 17)

if (IS_WINDOWS)
    install(FILES "${CMAKE_CURRENT_SOURCE_DIR}/prebuilt/windows/${TARGET_ARCH}/7z.dll" DESTINATION "${INSTALL_BUNDLE_LIB_DIR}")
endif ()

if (IS_ANDROID)
    add_library(7zip SHARED IMPORTED GLOBAL)

    set_target_properties(7zip PROPERTIES
            IMPORTED_LOCATION "${CMAKE_CURRENT_SOURCE_DIR}/prebuilt/android/${ANDROID_ABI}/lib7z.so"
            IMPORTED_NO_SONAME ON
    )
endif ()
