cmake_minimum_required(VERSION 2.8.12)

project(Baloo-Fuse)

include(FeatureSummary)
find_package(ECM 5.14.0 REQUIRED NO_MODULE)
#set_package_properties(ECM PROPERTIES TYPE REQUIRED DESCRIPTION "Extra CMake Modules." URL "https://projects.kde.org/projects/kdesupport/extra-cmake-modules")
feature_summary(WHAT REQUIRED_PACKAGES_NOT_FOUND FATAL_ON_MISSING_REQUIRED_PACKAGES)

set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake" ${ECM_MODULE_PATH} ${ECM_KDE_MODULE_DIR})
set(PROJECT_VERSION "0.1")

#include(ECMPackageConfigHelpers)
#include(ECMSetupVersion)
include(KDEInstallDirs)
include(KDECMakeSettings)
include(KDEFrameworkCompilerSettings)
include(ECMAddTests)

# Build dependencies
#set(REQUIRED_QT_VERSION 5.3.0)
set(KF5_DEP_VERSION 5.14)
#find_package(Qt5 ${REQUIRED_QT_VERSION} REQUIRED NO_MODULE COMPONENTS Core Test)
#find_package(KF5 ${KF5_DEP_VERSION} REQUIRED COMPONENTS Baloo)
find_package(KF5Baloo ${KF5_DEP_VERSION})
find_package(Fuse)

include_directories(
    ${FUSE_INCLUDE_DIRS}
)
add_subdirectory(src)

feature_summary(WHAT ALL
    INCLUDE_QUIET_PACKAGES
    FATAL_ON_MISSING_REQUIRED_PACKAGES
)
