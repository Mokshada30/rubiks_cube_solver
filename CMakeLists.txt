cmake_minimum_required(VERSION 3.20)
project(rubiks_cube_solver)

set(CMAKE_CXX_STANDARD 14)

# --- Find OpenCV from vcpkg ---
find_package(OpenCV REQUIRED)

# --- Includes ---
include_directories(${OpenCV_INCLUDE_DIRS})
include_directories(Model)
include_directories(${CMAKE_SOURCE_DIR})

# --- Executable ---
add_executable(rubiks_cube_solver
        Model/RubiksCube.cpp
        Model/RubiksCube.h
        main.cpp
        Model/RubiksCube3dArray.cpp
        Model/RubiksCube1dArray.cpp
        Model/RubiksCubeBitboard.cpp
        Solver/DFSSolver.h
        Solver/BFSSolver.h
        Solver/IDDFSSolver.h
        Model/PatternDatabase/PatternDatabase.h
        Solver/IDAstarSolver.h
        PatternDatabases/NibbleArray.cpp
        PatternDatabases/NibbleArray.h
        PatternDatabases/PatternDatabase.cpp
        PatternDatabases/PatternDatabase.h
        PatternDatabases/PermutationIndexer.h
        PatternDatabases/CornerPatternDatabase.cpp
        PatternDatabases/CornerPatternDatabase.h
        PatternDatabases/CornerDBMaker.cpp
        PatternDatabases/CornerDBMaker.h
        PatternDatabases/math.cpp
        PatternDatabases/math.h
        Scanner/CubeScanner.cpp
        Scanner/CubeScanner.h)

# --- Link OpenCV ---
target_link_libraries(rubiks_cube_solver PRIVATE ${OpenCV_LIBS})
