zhenya@zhenya-VirtualBox:~$ export GITHUB_USERNAME=ZhenyaBukov
zhenya@zhenya-VirtualBox:~$ alias gsed=sed



zhenya@zhenya-VirtualBox:~$ cd ${GITHUB_USERNAME}/workspace
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ pushd .
~/ZhenyaBukov/workspace ~/ZhenyaBukov/workspace
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ source scripts/activate



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ git clone git@github.com:ZhenyaBukov/lab04.git projects/lab06
Клонирование в «projects/lab06»...
remote: Enumerating objects: 2949, done.
remote: Counting objects: 100% (2949/2949), done.
remote: Compressing objects: 100% (2249/2249), done.
remote: Total 2949 (delta 528), reused 2945 (delta 527), pack-reused 0 (from 0)
Получение объектов: 100% (2949/2949), 13.46 МиБ | 2.72 МиБ/с, готово.
Определение изменений: 100% (528/528), готово.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ cd projects/lab06
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git remote remove origin
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git remote add origin git@github.com:ZhenyaBukov/lab06.git



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ mkdir third-party
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git submodule add https://github.com/google/googletest third-party/gtest
Клонирование в «/home/zhenya/ZhenyaBukov/workspace/projects/lab06/third-party/gtest»...
remote: Enumerating objects: 28100, done.
remote: Counting objects: 100% (318/318), done.
remote: Compressing objects: 100% (200/200), done.
remote: Total 28100 (delta 203), reused 125 (delta 113), pack-reused 27782 (from 4)
Получение объектов: 100% (28100/28100), 13.58 МиБ | 1.77 МиБ/с, готово.
Определение изменений: 100% (20811/20811), готово.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cd third-party/gtest && git checkout release-1.8.1 && cd ../..
Примечание: переключение на «release-1.8.1».

Вы сейчас в состоянии «отсоединённого указателя HEAD». Можете осмотреться,
внести экспериментальные изменения и зафиксировать их, также можете
отменить любые коммиты, созданные в этом состоянии, не затрагивая другие
ветки, переключившись обратно на любую ветку.

Если хотите создать новую ветку для сохранения созданных коммитов, можете
сделать это (сейчас или позже), используя команду switch с параметром -c.
Например:

  git switch -c <новая-ветка>

Или отмените эту операцию с помощью:

  git switch -

Отключите этот совет, установив переменную конфигурации
advice.detachedHead в значение false

HEAD сейчас на 2fe3bd99 Merge pull request #1433 from dsacre/fix-clang-warnings
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git add third-party/gtest
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git commit -m"added gtest framework"
[main 28a5b67] added gtest framework
 2 files changed, 4 insertions(+)
 create mode 100644 .gitmodules
 create mode 160000 third-party/gtest


 
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ gsed -i '/option(BUILD_EXAMPLES "Build examples" OFF)/a\
> option(BUILD_TESTS "Build tests" OFF)
' CMakeLists.txt
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat >> CMakeLists.txt <<EOF
> 
> if(BUILD_TESTS)
  enable_testing()
  add_subdirectory(third-party/gtest)
  file(GLOB \${PROJECT_NAME}_TEST_SOURCES tests/*.cpp)
  add_executable(check \${\${PROJECT_NAME}_TEST_SOURCES})
  target_link_libraries(check \${PROJECT_NAME} gtest_main)
  add_test(NAME check COMMAND check)
endif()
EOF



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ mkdir tests
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat > tests/test1.cpp <<EOF
> #include <print.hpp>

#include <gtest/gtest.h>

TEST(Print, InFileStream)
{
  std::string filepath = "file.txt";
  std::string text = "hello";
  std::ofstream out{filepath};

  print(text, out);
  out.close();

  std::string result;
  std::ifstream in{filepath};
  in >> result;

  EXPECT_EQ(result, text);
}
EOF



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cmake -H. -B_build -DBUILD_TESTS=ON
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- The C compiler identification is GNU 13.3.0
-- The CXX compiler identification is GNU 13.3.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
CMake Deprecation Warning at third-party/gtest/CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


CMake Deprecation Warning at third-party/gtest/googlemock/CMakeLists.txt:42 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


CMake Deprecation Warning at third-party/gtest/googletest/CMakeLists.txt:49 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


CMake Warning (dev) at third-party/gtest/googletest/cmake/internal_utils.cmake:239 (find_package):
  Policy CMP0148 is not set: The FindPythonInterp and FindPythonLibs modules
  are removed.  Run "cmake --help-policy CMP0148" for policy details.  Use
  the cmake_policy command to set the policy and suppress this warning.

Call Stack (most recent call first):
  third-party/gtest/googletest/CMakeLists.txt:84 (include)
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Found PythonInterp: /usr/bin/python3 (found version "3.12.3") 
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE  
-- Configuring done (0.6s)
-- Generating done (0.0s)
-- Build files have been written to: /home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cmake --build _build
[  6%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
In file included from /home/zhenya/ZhenyaBukov/workspace/projects/lab06/sources/print.cpp:2:
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/include/print.hpp:6:6: error: default argument given for parameter 2 of ‘void print(const std::string&, std::ostream&)’ [-fpermissive]
    6 | void print(const std::string& text, std::ostream& out = std::cout);
      |      ^~~~~
In file included from /home/zhenya/ZhenyaBukov/workspace/projects/lab06/sources/print.cpp:1:
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/include/print.hpp:6:6: note: previous specification in ‘void print(const std::string&, std::ostream&)’ here
    6 | void print(const std::string& text, std::ostream& out = std::cout);
      |      ^~~~~
gmake[2]: *** [CMakeFiles/print.dir/build.make:76: CMakeFiles/print.dir/sources/print.cpp.o] Ошибка 1
gmake[1]: *** [CMakeFiles/Makefile2:142: CMakeFiles/print.dir/all] Ошибка 2
gmake: *** [Makefile:146: all] Ошибка 2
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cmake --build _build --target test
Running tests...
Test project /home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build
    Start 1: check
Could not find executable /home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/check
Looked in the following places:
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Release/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Release/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Debug/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Debug/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/MinSizeRel/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/MinSizeRel/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/RelWithDebInfo/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/RelWithDebInfo/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Deployment/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Deployment/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Development/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Development/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Release/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Release/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Debug/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Debug/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/MinSizeRel/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/MinSizeRel/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/RelWithDebInfo/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/RelWithDebInfo/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Deployment/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Deployment/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Development/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Development/check
Unable to find executable: /home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/check
1/1 Test #1: check ............................***Not Run   0.00 sec

0% tests passed, 1 tests failed out of 1

Total Test time (real) =   0.00 sec

The following tests FAILED:
	  1 - check (Not Run)
Errors while running CTest
Output from these tests are in: /home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Testing/Temporary/LastTest.log
Use "--rerun-failed --output-on-failure" to re-run the failed cases verbosely.
gmake: *** [Makefile:71: test] Ошибка 8




zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ _build/check
bash: _build/check: Нет такого файла или каталога
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cmake --build _build --target test -- ARGS=--verbose
Running tests...
UpdateCTestConfiguration  from :/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/DartConfiguration.tcl
UpdateCTestConfiguration  from :/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/DartConfiguration.tcl
Test project /home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build
Constructing a list of tests
Done constructing a list of tests
Updating test list for fixtures
Added 0 tests to meet fixture requirements
Checking test dependency graph...
Checking test dependency graph end
test 1
    Start 1: check
Could not find executable /home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/check
Looked in the following places:
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Release/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Release/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Debug/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Debug/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/MinSizeRel/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/MinSizeRel/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/RelWithDebInfo/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/RelWithDebInfo/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Deployment/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Deployment/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Development/check
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Development/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Release/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Release/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Debug/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Debug/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/MinSizeRel/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/MinSizeRel/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/RelWithDebInfo/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/RelWithDebInfo/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Deployment/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Deployment/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Development/check
home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Development/check

1: Test command: 
1: Working Directory: /home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build
Unable to find executable: /home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/check
1/1 Test #1: check ............................***Not Run   0.00 sec

0% tests passed, 1 tests failed out of 1

Total Test time (real) =   0.00 sec

The following tests FAILED:
	  1 - check (Not Run)
Errors while running CTest
Output from these tests are in: /home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/Testing/Temporary/LastTest.log
Use "--rerun-failed --output-on-failure" to re-run the failed cases verbosely.
gmake: *** [Makefile:71: test] Ошибка 8



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ gsed -i 's/lab04/lab06/g' README.md
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ gsed -i 's/\(DCMAKE_INSTALL_PREFIX=_install\)/\1 -DBUILD_TESTS=ON/' .travis.yml
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ gsed -i '/cmake --build _build --target install/a\
> - cmake --build _build --target test -- ARGS=--verbose
' .travis.yml
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ travis lint

  ________                                 __
 /        |                               /  |
 ########/ ______    ______    __     __  ##/    _______
    ## |  /      \  /      \  /  \   /  | /  |  /       |
    ## | /######  | ######  | ##  \ /##/  ## | /#######/
    ## | ## |  ##/  /    ## |  ##  /##/   ## | ##      \
    ## | ## |      /####### |   ## ##/    ## |  ######  |
    ## | ## |      ##    ## |    ###/     ## | /     ##/
    ##/  ##/        #######/      #/      ##/  #######/

    TRajectory Analyzer and VISualizer  -  Open-source free software under GNU GPL v3

    Copyright (c) Martin Brehm      (2009-2022), University of Halle (Saale)
                  Martin Thomas     (2012-2022)
                  Sascha Gehrke     (2016-2022), University of Bonn
                  Barbara Kirchner  (2009-2022), University of Bonn

    http://www.travis-analyzer.de

    Please cite: J. Chem. Phys. 2020, 152 (16), 164105.         (DOI 10.1063/5.0005078 )
                 J. Chem. Inf. Model. 2011, 51 (8), 2007-2023.  (DOI 10.1021/ci200217w )

    There is absolutely no warranty on any results obtained from TRAVIS.

 #  Running on zhenya-VirtualBox at Sat May 24 22:39:07 2025 (PID 38246)
 #  Running in /home/zhenya/ZhenyaBukov/workspace/projects/lab06
 #  Version: Jul 29 2022, built at Jan 14 2023, 12:32:45, compiler "12.2.0", GCC 12.2.0
 #  Target platform: Linux, __cplusplus=201703L, Compile flags: NEW_CHARGEVAR DEBUG_ARRAYS 
 #  Compiled with OpenMP, but USE_OMP not switched on in "config.h"!
 #  Machine: x86_64, char=1b, int=4b, long=8b, addr=8b, 0xA0B0C0D0=D0,C0,B0,A0.
 #  Home: /home/zhenya,  Executable: /usr/bin/travis
 #  Input from terminal,  Output to terminal

    >>> Please use a color scheme with dark background or specify "-nocolor"! <<<

    Loading configuration from /home/zhenya/.travis.conf ...

Unknown parameter: "lint".

    List of supported command line options:

      -p <file>       Load position data from specified trajectory file.
                      Format may be *.xyz, *.pdb, *.lmp (LAMMPS), HISTORY (DLPOLY), POSCAR/XDATCAR (VASP),
                                    *.gro, *.dcd, or *.prmtop/*.mdcrd (Amber).
                      The bqb format (*.bqb, *.btr, *.emp, *.blist) as well as *.voronoi are also supported.
      -vel <file>     Read atom velocities from a file in addition to the position trajectory.
                      Currently, only .xyz format is supported for velocity data.
      -i <file>       Read input from specified text file.
      -c <file>       Read and execute control file (experimental).
      cubetool        Execute the CubeTool for modifying Gaussian Cube files.
      -sankey <file>  Create Sankey diagrams (file name is optional).
      -ramanfrompola  Compute Raman spectra from existing polarizability time series.
      (de-)compress   Start built-in bqbtool (compress trajectories to BQB format).
      check           Check BQB file integrity.

      -config <file>  Load the specified configuration file.
      -stream         Treat input trajectory as a stream (e.g. named pipe): No fseek, etc.
      -showconf       Show a tree structure of the configuration file.
      -writeconf      Write the default configuration file, including all defines values.

      -verbose        Show detailed information about what's going on.
      -nocolor        Execute TRAVIS in monochrome mode (suitable for white background).
      -dimcolor       Use dim instead of bright colors.

      -credits        Display a list of persons who contributed to TRAVIS.
      -help, -?       Shows this help.

    If only one argument is specified, it is assumed to be the name of a trajectory file.
    If no argument is specified at all, TRAVIS asks for the trajectory file to open.

    Note: To show a list of all persons who contributed to TRAVIS,
          please add "-credits" to your command line arguments, or set the
          variable "SHOWCREDITS" to "TRUE" in your travis.conf file.

    Source code from other projects used in TRAVIS:
      - lmfit     from Joachim Wuttke
      - kiss_fft  from Mark Borgerding
      - voro++    from Chris Rycroft

    http://www.travis-analyzer.de

    Please cite all of the following articles for the analyses you have used:

  * For TRAVIS in general:

    "TRAVIS - A Free Analyzer for Trajectories from Molecular Simulation",
    M. Brehm, M. Thomas, S. Gehrke, B. Kirchner; J. Chem. Phys. 2020, 152 (16), 164105.   (DOI 10.1063/5.0005078 )

    "TRAVIS - A Free Analyzer and Visualizer for Monte Carlo and Molecular Dynamics Trajectories",
    M. Brehm, B. Kirchner; J. Chem. Inf. Model. 2011, 51 (8), pp 2007-2023.   (DOI 10.1021/ci200217w )

*** The End ***

zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git add .travis.yml
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git add tests
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git add -p
diff --git a/CMakeLists.txt b/CMakeLists.txt
index 7bb5578..ae34362 100644
--- a/CMakeLists.txt
+++ b/CMakeLists.txt
@@ -10,3 +10,12 @@ add_executable(example2 ${CMAKE_CURRENT_SOURCE_DIR}/examples/example2.cpp)
 
 target_link_libraries(example1 print)
 target_link_libraries(example2 print)
+
+if(BUILD_TESTS)
+  enable_testing()
+  add_subdirectory(third-party/gtest)
+  file(GLOB ${PROJECT_NAME}_TEST_SOURCES tests/*.cpp)
+  add_executable(check ${${PROJECT_NAME}_TEST_SOURCES})
+  target_link_libraries(check ${PROJECT_NAME} gtest_main)
+  add_test(NAME check COMMAND check)
+endif()
(1/1) Индексировать этот блок [y,n,q,a,d,e,?]? y

diff --git a/README.md b/README.md
index a715d4f..2c3375c 100644
--- a/README.md
+++ b/README.md
@@ -82,27 +82,27 @@ ERROR:  While executing gem ... (Gem::FilePermissionError)
 
 
     
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ git clone git@github.com:ZhenyaBukov/lab03.git projects/lab04
-Клонирование в «projects/lab04»...
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ git clone git@github.com:ZhenyaBukov/lab03.git projects/lab06
+Клонирование в «projects/lab06»...
 remote: Enumerating objects: 2942, done.
 remote: Counting objects: 100% (2942/2942), done.
 remote: Compressing objects: 100% (2245/2245), done.
 remote: Total 2942 (delta 525), reused 2938 (delta 524), pack-reused 0 (from 0)
 Получение объектов: 100% (2942/2942), 13.45 МиБ | 2.16 МиБ/с, готово.
 Определение изменений: 100% (525/525), готово.
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ cd projects/lab04
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git remote remove origin
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git remote add origin git@github.com:ZhenyaBukov/lab04.git
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ cd projects/lab06
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git remote remove origin
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git remote add origin git@github.com:ZhenyaBukov/lab06.git
 
 
 
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ cat > .travis.yml <<EOF
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat > .travis.yml <<EOF
 > language: cpp
 EOF
 
 
 
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ cat >> .travis.yml <<EOF
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat >> .travis.yml <<EOF
 >
 > script:
 - cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
(1/10) Индексировать этот блок [y,n,q,a,d,j,J,g,/,s,e,?]? 
@@ -82,27 +82,27 @@ ERROR:  While executing gem ... (Gem::FilePermissionError)
 
 
     
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ git clone git@github.com:ZhenyaBukov/lab03.git projects/lab04
-Клонирование в «projects/lab04»...
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ git clone git@github.com:ZhenyaBukov/lab03.git projects/lab06
+Клонирование в «projects/lab06»...
 remote: Enumerating objects: 2942, done.
 remote: Counting objects: 100% (2942/2942), done.
 remote: Compressing objects: 100% (2245/2245), done.
 remote: Total 2942 (delta 525), reused 2938 (delta 524), pack-reused 0 (from 0)
 Получение объектов: 100% (2942/2942), 13.45 МиБ | 2.16 МиБ/с, готово.
 Определение изменений: 100% (525/525), готово.
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ cd projects/lab04
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git remote remove origin
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git remote add origin git@github.com:ZhenyaBukov/lab04.git
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ cd projects/lab06
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git remote remove origin
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git remote add origin git@github.com:ZhenyaBukov/lab06.git
 
 
 
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ cat > .travis.yml <<EOF
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat > .travis.yml <<EOF
 > language: cpp
 EOF
 
 
 
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ cat >> .travis.yml <<EOF
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat >> .travis.yml <<EOF
 >
 > script:
 - cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
(1/10) Индексировать этот блок [y,n,q,a,d,j,J,g,/,s,e,?]? 
@@ -82,27 +82,27 @@ ERROR:  While executing gem ... (Gem::FilePermissionError)
 
 
     
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ git clone git@github.com:ZhenyaBukov/lab03.git projects/lab04
-Клонирование в «projects/lab04»...
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ git clone git@github.com:ZhenyaBukov/lab03.git projects/lab06
+Клонирование в «projects/lab06»...
 remote: Enumerating objects: 2942, done.
 remote: Counting objects: 100% (2942/2942), done.
 remote: Compressing objects: 100% (2245/2245), done.
 remote: Total 2942 (delta 525), reused 2938 (delta 524), pack-reused 0 (from 0)
 Получение объектов: 100% (2942/2942), 13.45 МиБ | 2.16 МиБ/с, готово.
 Определение изменений: 100% (525/525), готово.
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ cd projects/lab04
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git remote remove origin
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git remote add origin git@github.com:ZhenyaBukov/lab04.git
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ cd projects/lab06
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git remote remove origin
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git remote add origin git@github.com:ZhenyaBukov/lab06.git
 
 
 
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ cat > .travis.yml <<EOF
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat > .travis.yml <<EOF
 > language: cpp
 EOF
 
 
 
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ cat >> .travis.yml <<EOF
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat >> .travis.yml <<EOF
 >
 > script:
 - cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
(1/10) Индексировать этот блок [y,n,q,a,d,j,J,g,/,s,e,?]? y
@@ -113,7 +113,7 @@ EOF
 
 
 
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ cat >> .travis.yml <<EOF
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat >> .travis.yml <<EOF
 >
 > addons:
   apt:
(2/10) Индексировать этот блок [y,n,q,a,d,K,j,J,g,/,e,?]? y
@@ -127,13 +127,13 @@ EOF
 
 
 
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ sudo snap install travis
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ sudo snap install travis
 travis 1.8.9 от Travis CI✓ installed
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ travis login --github-token ${GITHUB_TOKEN}
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ travis login --github-token ${GITHUB_TOKEN}
 Outdated CLI version, run `gem install travis`.
 resource not found ({}
 )
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ sudo apt  install travis
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ sudo apt  install travis
 Чтение списков пакетов… Готово
 Построение дерева зависимостей… Готово
 Чтение информации о состоянии… Готово         
(3/10) Индексировать этот блок [y,n,q,a,d,K,j,J,g,/,s,e,?]? y
@@ -153,14 +153,14 @@ zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ sudo apt  inst
 Распаковывается travis (220729-1) …
 Настраивается пакет travis (220729-1) …
 Обрабатываются триггеры для man-db (2.12.0-4build2) …
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ travis login --github-token ${GITHUB_TOKEN}
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ travis login --github-token ${GITHUB_TOKEN}
 Outdated CLI version, run `gem install travis`.
 resource not found ({}
 )
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ travis lint
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ travis lint
 Outdated CLI version, run `gem install travis`.
 405: "<!doctype html>\n<html lang=en>\n<title>405 Method Not Allowed</title>\n<h1>Method Not Allowed</h1>\n<p>The method is not allowed for the requested URL.</p>\n"
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ sudo apt-get install ruby-full
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ sudo apt-get install ruby-full
 Чтение списков пакетов… Готово
 Построение дерева зависимостей… Готово
 Чтение информации о состоянии… Готово         
(4/10) Индексировать этот блок [y,n,q,a,d,K,j,J,g,/,s,e,?]? y
@@ -213,7 +213,7 @@ zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ sudo apt-get in
 Настраивается пакет ruby-dev:amd64 (1:3.2~ubuntu1) …
 Настраивается пакет ruby-full (1:3.2~ubuntu1) …
 Обрабатываются триггеры для libc-bin (2.39-0ubuntu8.4) …
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ travis login --github-token ${GITHUB_TOKEN}
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ travis login --github-token ${GITHUB_TOKEN}
  
   ________                                 __
  /        |                               /  |
(5/10) Индексировать этот блок [y,n,q,a,d,K,j,J,g,/,e,?]? y
@@ -240,7 +240,7 @@ zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ travis login --
     There is absolutely no warranty on any results obtained from TRAVIS.
  
  #  Running on zhenya-VirtualBox at Sun May 18 23:42:04 2025 (PID 29522)
- #  Running in /home/zhenya/ZhenyaBukov/workspace/projects/lab04
+ #  Running in /home/zhenya/ZhenyaBukov/workspace/projects/lab06
  #  Version: Jul 29 2022, built at Jan 14 2023, 12:32:45, compiler "12.2.0", GCC 12.2.0
  #  Target platform: Linux, __cplusplus=201703L, Compile flags: NEW_CHARGEVAR DEBUG_ARRAYS
  #  Compiled with OpenMP, but USE_OMP not switched on in "config.h"!
(6/10) Индексировать этот блок [y,n,q,a,d,K,j,J,g,/,e,?]? y
@@ -309,7 +309,7 @@ Unknown parameter: "login".
  
 *** The End ***
  
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ travis lint
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ travis lint
 [Renaming existing File travis.log to #2#travis.log ...OK.]
  
   ________                                 __
(7/10) Индексировать этот блок [y,n,q,a,d,K,j,J,g,/,e,?]? y
@@ -337,7 +337,7 @@ zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ travis lint
     There is absolutely no warranty on any results obtained from TRAVIS.
  
  #  Running on zhenya-VirtualBox at Sun May 18 23:42:43 2025 (PID 29534)
- #  Running in /home/zhenya/ZhenyaBukov/workspace/projects/lab04
+ #  Running in /home/zhenya/ZhenyaBukov/workspace/projects/lab06
  #  Version: Jul 29 2022, built at Jan 14 2023, 12:32:45, compiler "12.2.0", GCC 12.2.0
  #  Target platform: Linux, __cplusplus=201703L, Compile flags: NEW_CHARGEVAR DEBUG_ARRAYS
  #  Compiled with OpenMP, but USE_OMP not switched on in "config.h"!
(8/10) Индексировать этот блок [y,n,q,a,d,K,j,J,g,/,e,?]? y
@@ -406,20 +406,20 @@ Unknown parameter: "lint".
  
 *** The End ***
  
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ ex -sc '1i|<фрагмент_вставки_значка>' -cx README.md
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ ex -sc '1i|<фрагмент_вставки_значка>' -cx README.md
 
 
 
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git add .travis.yml
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git add README.md
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git commit -m"added CI"
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git add .travis.yml
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git add README.md
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git commit -m"added CI"
 [main f8800d7] added CI
  2 files changed, 15 insertions(+)
  create mode 100644 .travis.yml
 
 
  
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git push -f origin main
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git push -f origin main
 Перечисление объектов: 2946, готово.
 Подсчет объектов: 100% (2946/2946), готово.
 При сжатии изменений используется до 2 потоков
(9/10) Индексировать этот блок [y,n,q,a,d,K,j,J,g,/,s,e,?]? y
@@ -427,12 +427,12 @@ zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git push -f ori
 Запись объектов: 100% (2946/2946), 13.45 МиБ | 2.71 МиБ/с, готово.
 Всего 2946 (изменений 527), повторно использовано 2940 (изменений 525), повторно использовано пакетов 0
 remote: Resolving deltas: 100% (527/527), done.
-To github.com:ZhenyaBukov/lab04.git
+To github.com:ZhenyaBukov/lab06.git
  + 700a4de...f8800d7 main -> main (forced update)
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git push origin master
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git push origin master
 error: src refspec master ничему не соответствует
-error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab04.git»
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git push origin main
+error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab06.git»
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git push origin main
 Everything up-to-date
-zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$
+zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$
  
(10/10) Индексировать этот блок [y,n,q,a,d,K,g,/,s,e,?]? y





zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git push origin master
error: src refspec master ничему не соответствует
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab06.git»
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git push origin main
To github.com:ZhenyaBukov/lab06.git
 ! [rejected]        main -> main (fetch first)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab06.git»
подсказка: Updates were rejected because the remote contains work that you do not
подсказка: have locally. This is usually caused by another repository pushing to
подсказка: the same ref. If you want to integrate the remote changes, use
подсказка: 'git pull' before pushing again.
подсказка: See the 'Note about fast-forwards' in 'git push --help' for details.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git push -f origin main
Перечисление объектов: 2953, готово.
Подсчет объектов: 100% (2953/2953), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2251/2251), готово.
Запись объектов: 100% (2953/2953), 13.46 МиБ | 3.63 МиБ/с, готово.
Всего 2953 (изменений 529), повторно использовано 2948 (изменений 528), повторно использовано пакетов 0
remote: Resolving deltas: 100% (529/529), done.
remote: error: GH013: Repository rule violations found for refs/heads/main.
remote: 
remote: - GITHUB PUSH PROTECTION
remote:   —————————————————————————————————————————
remote:     Resolve the following violations before pushing again
remote: 
remote:     - Push cannot contain secrets
remote: 
remote:     
remote:      (?) Learn how to resolve a blocked push
remote:      https://docs.github.com/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/working-with-push-protection-from-the-command-line#resolving-a-blocked-push
remote:     
remote:     
remote:       —— GitHub Personal Access Token ——————————————————————
remote:        locations:
remote:          - commit: d9761b6860846de6c653a920d82595366474a101
remote:            path: README.md:2
remote:     
remote:        (?) To push, remove secret from commit(s) or follow this URL to allow the secret.
remote:        https://github.com/ZhenyaBukov/lab06/security/secret-scanning/unblock-secret/2xYWxpTa863ENgTEzXwGh9N9kHj
remote:     
remote:     
remote:       —— GitHub Personal Access Token ——————————————————————
remote:        locations:
remote:          - commit: c71fea93dbceb60601f9d9cc6175713b8e8fa5ba
remote:            path: README.md:3
remote:     
remote:        (?) To push, remove secret from commit(s) or follow this URL to allow the secret.
remote:        https://github.com/ZhenyaBukov/lab06/security/secret-scanning/unblock-secret/2xYWxrzsPQL6YiDDfX8neRfLaLd
remote:     
remote: 
remote: 
To github.com:ZhenyaBukov/lab06.git
 ! [remote rejected] main -> main (push declined due to repository rule violations)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab06.git»
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git push -f origin main
Перечисление объектов: 2953, готово.
Подсчет объектов: 100% (2953/2953), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2251/2251), готово.
Запись объектов: 100% (2953/2953), 13.46 МиБ | 3.91 МиБ/с, готово.
Всего 2953 (изменений 529), повторно использовано 2948 (изменений 528), повторно использовано пакетов 0
remote: Resolving deltas: 100% (529/529), done.
remote: error: GH013: Repository rule violations found for refs/heads/main.
remote: 
remote: - GITHUB PUSH PROTECTION
remote:   —————————————————————————————————————————
remote:     Resolve the following violations before pushing again
remote: 
remote:     - Push cannot contain secrets
remote: 
remote:     
remote:      (?) Learn how to resolve a blocked push
remote:      https://docs.github.com/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/working-with-push-protection-from-the-command-line#resolving-a-blocked-push
remote:     
remote:     
remote:       —— GitHub Personal Access Token ——————————————————————
remote:        locations:
remote:          - commit: d9761b6860846de6c653a920d82595366474a101
remote:            path: README.md:2
remote:     
remote:        (?) To push, remove secret from commit(s) or follow this URL to allow the secret.
remote:        https://github.com/ZhenyaBukov/lab06/security/secret-scanning/unblock-secret/2xYWxpTa863ENgTEzXwGh9N9kHj
remote:     
remote: 
remote: 
To github.com:ZhenyaBukov/lab06.git
 ! [remote rejected] main -> main (push declined due to repository rule violations)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab06.git»
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$  git push -f origin main
Перечисление объектов: 2953, готово.
Подсчет объектов: 100% (2953/2953), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2251/2251), готово.
Запись объектов: 100% (2953/2953), 13.46 МиБ | 3.34 МиБ/с, готово.
Всего 2953 (изменений 529), повторно использовано 2948 (изменений 528), повторно использовано пакетов 0
remote: Resolving deltas: 100% (529/529), done.
To github.com:ZhenyaBukov/lab06.git
 + 55b3f1d...28a5b67 main -> main (forced update)
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git push origin main
Everything up-to-date
