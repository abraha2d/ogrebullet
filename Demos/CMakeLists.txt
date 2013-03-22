#cmake_minimum_required(VERSION 2.6.2)

#set(PROJ "ogrebulletdemos")

set(DEMOS "demos")

message(STATUS "Building demos!")

#project(${PROJ})

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake/)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/lib)

#find_package(OGRE REQUIRED)
#find_package(OpenGL REQUIRED)
#find_package(Bullet REQUIRED)
#find_package(OgreBullet REQUIRED)
#find_package(Threads REQUIRED)
find_package(OIS REQUIRED)

set(LIBS
	${OGRE_LIBRARIES}
#	${OPENGL_glu_LIBRARY}
	${COLLISIONS_LIB}
	${DYNAMICS_LIB}
	${BULLET_LIBRARIES}
#	${LUA_LIBRARY}
#	${CMAKE_THREAD_LIBS_INIT}
	${OIS_LIBRARIES})

message(STATUS "LIBS: ${LIBS}")

set(INCLUDE_DIRS
#	${OGRE_INCLUDE_DIRS}
#	${OGREPROCEDURAL_INCLUDE_DIRS}
#	${BULLET_INCLUDE_DIR}
#	${OGREBULLET_INCLUDE_DIRS}
#	${LUA_INCLUDE_DIR}
	${OIS_INCLUDE_DIRS}
#	${CMAKE_CURRENT_SOURCE_DIR}
	${CMAKE_CURRENT_SOURCE_DIR}/include
	${CMAKE_CURRENT_SOURCE_DIR}/common/include)


#if(MSVC)
#	add_definitions (/W3)
#elseif(CMAKE_COMPILER_IS_GNUCXX)
#	add_definitions (-Wall)
#	add_definitions (-std=c++0x)
#	add_definitions (-D__GXX_EXPERIMENTAL_CXX0X__)
#endif()

set(SOURCES
	common/src/BetaGUI.cpp
	common/src/OgreBulletGuiListener.cpp
	common/src/OgreBulletInputListener.cpp
	common/src/OgreBulletListener.cpp
	common/src/OgreBulletApplication.cpp
	src/Terrain_Demo.cpp
	src/Vehicle_Demo.cpp
	src/Constraints_Demo.cpp
	src/Primitives_Demo.cpp
	src/Ragdoll_Demo.cpp
	src/main.cpp
	src/TriMesh_Demo.cpp
)

include_directories(${INCLUDE_DIRS})

link_directories(${LIB_DIR})

add_executable(${DEMOS} ${SOURCES})
target_link_libraries(${DEMOS} ${LIBS})
