cmake_minimum_required(VERSION 3.10) # Устанавливает минимальную версию CMake, необходимую для этого проекта.
set(PATCH_VERSION "1" CACHE INTERNAL "Patch version")
set(PROJECT_VERSION 0.0.${PATCH_VERSION})
# Создает переменные PATCH_VERSION и PROJECT_VESRION для управления версиями проекта.

set(CMAKE_CXX_STANDARD 17)
set(CXX_STANDARD_REQUIRED ON)

project(laba3 VERSION ${PROJECT_VESRION}) # Определяет имя проекта laba3 и использует переменную PROJECT_VESRION для указания версии проекта.
add_executable(laba3 main.cpp)


# Установка файлов для инсталляции
install(TARGETS laba3 DESTINATION bin)

set(CPACK_PROJECT_NAME laba3)

set(CPACK_GENERATOR "DEB")
set(CPACK_PACKAGE_VERSION "${CPACK_PACKAGE_VERSION_MAJOR}.${CPACK_PACKAGE_VERSION_MINOR}.${CPACK_PACKAGE_VERSION_PATCH}")

set(CPACK_PACKAGE_VERSION_MAJOR "${PROJECT_VERSION_MAJOR}")
set(CPACK_PACKAGE_VERSION_MINOR "${PROJECT_VERSION_MINOR}")
set(CPACK_PACKAGE_VERSION_PATCH "${PROJECT_VERSION_PATCH}")

set(CPACK_PACKAGE_CONTACT example@example.com)

include(CPack)

enable_testing() # Включает тестирование

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})