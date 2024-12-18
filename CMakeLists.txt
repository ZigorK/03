cmake_minimum_required(VERSION 3.10)

# Настройка версии проекта
set(PATCH_VERSION "1" CACHE INTERNAL "Patch version")
set(PROJECT_VERSION 0.0.${PATCH_VERSION})

project(laba3 VERSION ${PROJECT_VERSION})

# Установка стандартов C++
set(CMAKE_CXX_STANDARD 17)
set(CXX_STANDARD_REQUIRED ON)

# Добавление исполняемого файла
add_executable(laba3 main.cpp)

# Установка файлов для инсталляции
install(TARGETS laba3 DESTINATION bin)

# Настройка CPack
set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})

# Указание генераторов для macOS и Ubuntu
if(APPLE)
    set(CPACK_GENERATOR "DMG")  # Используем только DMG, без DragNDrop
elseif(UNIX AND NOT APPLE)
    set(CPACK_GENERATOR "DEB")
endif()

# Указание версии пакета
set(CPACK_PACKAGE_VERSION_MAJOR "${PROJECT_VERSION_MAJOR}")
set(CPACK_PACKAGE_VERSION_MINOR "${PROJECT_VERSION_MINOR}")
set(CPACK_PACKAGE_VERSION_PATCH "${PROJECT_VERSION_PATCH}")
set(CPACK_PACKAGE_VERSION "${PROJECT_VERSION}")
set(CPACK_PACKAGE_CONTACT "example@example.com")

include(CPack)

# Включение тестирования
enable_testing()
