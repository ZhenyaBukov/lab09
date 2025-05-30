zhenya@zhenya-VirtualBox:~$ export GITHUB_USERNAME=ZhenyaBukov
zhenya@zhenya-VirtualBox:~$ export GITHUB_EMAIL=zhenya.bukov.06@mail.ru
zhenya@zhenya-VirtualBox:~$ alias edit=nano
zhenya@zhenya-VirtualBox:~$ alias gsed=sed



zhenya@zhenya-VirtualBox:~$ cd ${GITHUB_USERNAME}/workspace
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ pushd .
~/ZhenyaBukov/workspace ~/ZhenyaBukov/workspace
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ source scripts/activate



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ git clone git@github.com:ZhenyaBukov/lab05.git projects/lab06
Клонирование в «projects/lab06»...
remote: Enumerating objects: 2959, done.
remote: Counting objects: 100% (2959/2959), done.
remote: Compressing objects: 100% (2256/2256), done.
remote: Total 2959 (delta 532), reused 2951 (delta 529), pack-reused 0 (from 0)
Получение объектов: 100% (2959/2959), 13.47 МиБ | 2.04 МиБ/с, готово.
Определение изменений: 100% (532/532), готово.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ cd projects/lab06
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git remote remove origin



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git remote add origin git@github.com:ZhenyaBukov/lab06.git
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ gsed -i '/project(print)/a\
> set(PRINT_VERSION_STRING "v\${PRINT_VERSION}")
> ' CMakeLists.txt
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ gsed -i '/project(print)/a\
> set(PRINT_VERSION\
  \${PRINT_VERSION_MAJOR}.\${PRINT_VERSION_MINOR}.\${PRINT_VERSION_PATCH}.\${PRINT_VERSION_TWEAK})
' CMakeLists.txt
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ gsed -i '/project(print)/a\
> set(PRINT_VERSION_TWEAK 0)
' CMakeLists.txt
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ gsed -i '/project(print)/a\
> set(PRINT_VERSION_PATCH 0)
' CMakeLists.txt
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ gsed -i '/project(print)/a\
> set(PRINT_VERSION_MINOR 1)
' CMakeLists.txt
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ gsed -i '/project(print)/a\
> set(PRINT_VERSION_MAJOR 0)
' CMakeLists.txt
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git diff
diff --git a/CMakeLists.txt b/CMakeLists.txt
index aa7a323..71b64e3 100644
--- a/CMakeLists.txt
+++ b/CMakeLists.txt
@@ -7,6 +7,13 @@ option(BUILD_EXAMPLES "Build examples" OFF)
 option(BUILD_TESTS "Build tests" OFF)
 
 project(print)
+set(PRINT_VERSION_MAJOR 0)
+set(PRINT_VERSION_MINOR 1)
+set(PRINT_VERSION_PATCH 0)
+set(PRINT_VERSION_TWEAK 0)
+set(PRINT_VERSION
+  ${PRINT_VERSION_MAJOR}.${PRINT_VERSION_MINOR}.${PRINT_VERSION_PATCH}.${PRINT_VERSION_TWEAK})
+set(PRINT_VERSION_STRING "v${PRINT_VERSION}")
 
 add_library(print STATIC ${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)
 


zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ touch DESCRIPTION && edit DESCRIPTION
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ touch ChangeLog.md
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ export DATE="`LANG=en_US date +'%a %b %d %Y'`"
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat > ChangeLog.md <<EOF
> * ${DATE} ${GITHUB_USERNAME} <${GITHUB_EMAIL}> 0.1.0.0
- Initial RPM release
EOF



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat > CPackConfig.cmake <<EOF
> include(InstallRequiredSystemLibraries)
EOF



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat >> CPackConfig.cmake <<EOF
> set(CPACK_PACKAGE_CONTACT ${GITHUB_EMAIL})
set(CPACK_PACKAGE_VERSION_MAJOR \${PRINT_VERSION_MAJOR})
set(CPACK_PACKAGE_VERSION_MINOR \${PRINT_VERSION_MINOR})
set(CPACK_PACKAGE_VERSION_PATCH \${PRINT_VERSION_PATCH})
set(CPACK_PACKAGE_VERSION_TWEAK \${PRINT_VERSION_TWEAK})
set(CPACK_PACKAGE_VERSION \${PRINT_VERSION})
set(CPACK_PACKAGE_DESCRIPTION_FILE \${CMAKE_CURRENT_SOURCE_DIR}/DESCRIPTION)
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "static C++ library for printing")
EOF



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat >> CPackConfig.cmake <<EOF
> 
> set(CPACK_RESOURCE_FILE_LICENSE \${CMAKE_CURRENT_SOURCE_DIR}/LICENSE)
set(CPACK_RESOURCE_FILE_README \${CMAKE_CURRENT_SOURCE_DIR}/README.md) 
EOF



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat >> CPackConfig.cmake <<EOF
> 
> set(CPACK_RPM_PACKAGE_NAME "print-devel")
set(CPACK_RPM_PACKAGE_LICENSE "MIT")
set(CPACK_RPM_PACKAGE_GROUP "print")
set(CPACK_RPM_CHANGELOG_FILE \${CMAKE_CURRENT_SOURCE_DIR}/ChangeLog.md)
set(CPACK_RPM_PACKAGE_RELEASE 1)
EOF



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat >> CPackConfig.cmake <<EOF
> 
> set(CPACK_DEBIAN_PACKAGE_NAME "libprint-dev")
set(CPACK_DEBIAN_PACKAGE_PREDEPENDS "cmake >= 3.0")
set(CPACK_DEBIAN_PACKAGE_RELEASE 1)
EOF



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat >> CPackConfig.cmake <<EOF
> 
> include(CPack)
EOF



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cat >> CMakeLists.txt <<EOF
> 
> include(CPackConfig.cmake)
EOF



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ gsed -i 's/lab05/lab06/g' README.md



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git add .
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git commit -m"added cpack config"
[main f5ca419] added cpack config
 5 files changed, 194 insertions(+), 159 deletions(-)
 create mode 100644 CPackConfig.cmake
 create mode 100644 ChangeLog.md
 create mode 100644 DESCRIPTION
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git tag v0.1.0.0
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git push origin main --tags
Перечисление объектов: 2965, готово.
Подсчет объектов: 100% (2965/2965), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2259/2259), готово.
Запись объектов: 100% (2965/2965), 13.47 МиБ | 3.47 МиБ/с, готово.
Всего 2965 (изменений 535), повторно использовано 2956 (изменений 532), повторно использовано пакетов 0
remote: Resolving deltas: 100% (535/535), done.
remote: error: GH013: Repository rule violations found for refs/tags/v0.1.0.0.
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
remote:        https://github.com/ZhenyaBukov/lab06/security/secret-scanning/unblock-secret/2xomUIjouEI0gu2J0Hs6V24I9gt
remote:     
remote:     
remote:       —— GitHub Personal Access Token ——————————————————————
remote:        locations:
remote:          - commit: c71fea93dbceb60601f9d9cc6175713b8e8fa5ba
remote:            path: README.md:3
remote:     
remote:        (?) To push, remove secret from commit(s) or follow this URL to allow the secret.
remote:        https://github.com/ZhenyaBukov/lab06/security/secret-scanning/unblock-secret/2xomUJlbuUPzEKRl7V1UPfXhD95
remote:     
remote: 
remote: 
To github.com:ZhenyaBukov/lab06.git
 ! [rejected]        main -> main (fetch first)
 ! [remote rejected] v0.1.0.0 -> v0.1.0.0 (push declined due to repository rule violations)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab06.git»
подсказка: Updates were rejected because the remote contains work that you do not
подсказка: have locally. This is usually caused by another repository pushing to
подсказка: the same ref. If you want to integrate the remote changes, use
подсказка: 'git pull' before pushing again.
подсказка: See the 'Note about fast-forwards' in 'git push --help' for details.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git push origin main --tags
Перечисление объектов: 2965, готово.
Подсчет объектов: 100% (2965/2965), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2259/2259), готово.
Запись объектов: 100% (2965/2965), 13.47 МиБ | 1.64 МиБ/с, готово.
Всего 2965 (изменений 535), повторно использовано 2956 (изменений 532), повторно использовано пакетов 0
remote: Resolving deltas: 100% (535/535), done.
remote: error: GH013: Repository rule violations found for refs/tags/v0.1.0.0.
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
remote:        https://github.com/ZhenyaBukov/lab06/security/secret-scanning/unblock-secret/2xomUIjouEI0gu2J0Hs6V24I9gt
remote:     
remote: 
remote: 
To github.com:ZhenyaBukov/lab06.git
 ! [rejected]        main -> main (fetch first)
 ! [remote rejected] v0.1.0.0 -> v0.1.0.0 (push declined due to repository rule violations)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab06.git»
подсказка: Updates were rejected because the remote contains work that you do not
подсказка: have locally. This is usually caused by another repository pushing to
подсказка: the same ref. If you want to integrate the remote changes, use
подсказка: 'git pull' before pushing again.
подсказка: See the 'Note about fast-forwards' in 'git push --help' for details.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git push -f origin main
Перечисление объектов: 2965, готово.
Подсчет объектов: 100% (2965/2965), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2259/2259), готово.
Запись объектов: 100% (2965/2965), 13.47 МиБ | 1.99 МиБ/с, готово.
Всего 2965 (изменений 535), повторно использовано 2956 (изменений 532), повторно использовано пакетов 0
remote: Resolving deltas: 100% (535/535), done.
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
remote:        https://github.com/ZhenyaBukov/lab06/security/secret-scanning/unblock-secret/2xomUIjouEI0gu2J0Hs6V24I9gt
remote:     
remote: 
remote: 
To github.com:ZhenyaBukov/lab06.git
 ! [remote rejected] main -> main (push declined due to repository rule violations)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab06.git»
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ git push -f origin main
Перечисление объектов: 2965, готово.
Подсчет объектов: 100% (2965/2965), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2259/2259), готово.
Запись объектов: 100% (2965/2965), 13.47 МиБ | 2.62 МиБ/с, готово.
Всего 2965 (изменений 535), повторно использовано 2956 (изменений 532), повторно использовано пакетов 0
remote: Resolving deltas: 100% (535/535), done.
To github.com:ZhenyaBukov/lab06.git
 + 11e22b9...f5ca419 main -> main (forced update)
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ travis login --auto

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

 #  Running on zhenya-VirtualBox at Fri May 30 16:50:05 2025 (PID 50266)
 #  Running in /home/zhenya/ZhenyaBukov/workspace/projects/lab06
 #  Version: Jul 29 2022, built at Jan 14 2023, 12:32:45, compiler "12.2.0", GCC 12.2.0
 #  Target platform: Linux, __cplusplus=201703L, Compile flags: NEW_CHARGEVAR DEBUG_ARRAYS 
 #  Compiled with OpenMP, but USE_OMP not switched on in "config.h"!
 #  Machine: x86_64, char=1b, int=4b, long=8b, addr=8b, 0xA0B0C0D0=D0,C0,B0,A0.
 #  Home: /home/zhenya,  Executable: /usr/bin/travis
 #  Input from terminal,  Output to terminal

    >>> Please use a color scheme with dark background or specify "-nocolor"! <<<

    Loading configuration from /home/zhenya/.travis.conf ...

Unknown parameter: "login".

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

zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cmake -H. -B_build
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
-- Configuring done (0.5s)
-- Generating done (0.0s)
-- Build files have been written to: /home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cmake --build _build
[ 50%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
In file included from /home/zhenya/ZhenyaBukov/workspace/projects/lab06/sources/print.cpp:2:
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/include/print.hpp:6:6: error: default argument given for parameter 2 of ‘void print(const std::string&, std::ostream&)’ [-fpermissive]
    6 | void print(const std::string& text, std::ostream& out = std::cout);
      |      ^~~~~
In file included from /home/zhenya/ZhenyaBukov/workspace/projects/lab06/sources/print.cpp:1:
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/include/print.hpp:6:6: note: previous specification in ‘void print(const std::string&, std::ostream&)’ here
    6 | void print(const std::string& text, std::ostream& out = std::cout);
      |      ^~~~~
gmake[2]: *** [CMakeFiles/print.dir/build.make:76: CMakeFiles/print.dir/sources/print.cpp.o] Ошибка 1
gmake[1]: *** [CMakeFiles/Makefile2:83: CMakeFiles/print.dir/all] Ошибка 2
gmake: *** [Makefile:156: all] Ошибка 2
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cd _build
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06/_build$ cpack -G "TGZ"
CPack: Create package using TGZ
CPack: Install projects
CPack: - Run preinstall target for: print
CPack Error: Problem running install command: /usr/bin/cmake --build . --target "preinstall"
Please check /home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build/_CPack_Packages/Linux/TGZ/PreinstallOutput.log for errors
CPack Error: Error when generating package: print
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06/_build$ cd ..
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cmake -H. -B_build -DCPACK_GENERATOR="TGZ"
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (0.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/zhenya/ZhenyaBukov/workspace/projects/lab06/_build
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ cmake --build _build --target package
[ 50%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
In file included from /home/zhenya/ZhenyaBukov/workspace/projects/lab06/sources/print.cpp:2:
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/include/print.hpp:6:6: error: default argument given for parameter 2 of ‘void print(const std::string&, std::ostream&)’ [-fpermissive]
    6 | void print(const std::string& text, std::ostream& out = std::cout);
      |      ^~~~~
In file included from /home/zhenya/ZhenyaBukov/workspace/projects/lab06/sources/print.cpp:1:
/home/zhenya/ZhenyaBukov/workspace/projects/lab06/include/print.hpp:6:6: note: previous specification in ‘void print(const std::string&, std::ostream&)’ here
    6 | void print(const std::string& text, std::ostream& out = std::cout);
      |      ^~~~~
gmake[2]: *** [CMakeFiles/print.dir/build.make:76: CMakeFiles/print.dir/sources/print.cpp.o] Ошибка 1
gmake[1]: *** [CMakeFiles/Makefile2:83: CMakeFiles/print.dir/all] Ошибка 2
gmake: *** [Makefile:156: all] Ошибка 2
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ mkdir artifacts
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ mv _build/*.tar.gz artifacts
mv: не удалось выполнить stat для '_build/*.tar.gz': Нет такого файла или каталога
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lzzzzzhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab06$ 

