cmake_minimum_required(VERSION 3.10)

# Установка версии проекта
set(PATCH_VERSION "1" CACHE INTERNAL "Patch version")
set(PROJECT_VERSION 0.0.${PATCH_VERSION})

project(laba3 VERSION ${PROJECT_VERSION})

# Установка стандартов C++
set(CMAKE_CXX_STANDARD 17)
set(CXX_STANDARD_REQUIRED ON)

# Добавление исполняемого файла
add_executable(laba3 main.cpp)

# Настройка CPack
if(APPLE)
    # Генератор DMG для macOS
    set(CPACK_GENERATOR "DragNDrop;DMG")
    set(CPACK_DMG_BACKGROUND_IMAGE "${CMAKE_SOURCE_DIR}/background.png") # Фон для DMG
    set(CPACK_DMG_VOLUME_NAME "${PROJECT_NAME} ${PROJECT_VERSION}")
elseif(UNIX AND NOT APPLE)
    # Генератор DEB для Ubuntu
    set(CPACK_GENERATOR "DEB")
endif()

# Общие параметры пакета
set(CPACK_PACKAGE_NAME ${PROJECT_NAME})
set(CPACK_PACKAGE_VERSION ${PROJECT_VERSION})
set(CPACK_PACKAGE_CONTACT "example@example.com")
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "Example project for C++ CI/CD")
set(CPACK_PACKAGE_VENDOR "Example Vendor")
set(CPACK_PACKAGE_FILE_NAME "${PROJECT_NAME}-${PROJECT_VERSION}-${CMAKE_SYSTEM_NAME}")

# Включение CPack
include(CPack)

# Установка файлов для инсталляции
install(TARGETS laba3 DESTINATION bin)

# Включение тестирования
enable_testing()
