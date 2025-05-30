zhenya@zhenya-VirtualBox:~$ export GITHUB_USERNAME=ZhenyaBukov
zhenya@zhenya-VirtualBox:~$ alias gsed=sed
zhenya@zhenya-VirtualBox:~$ cd ${GITHUB_USERNAME}/workspace
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ pushd .
~/ZhenyaBukov/workspace ~/ZhenyaBukov/workspace
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ source scripts/activate
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ git clone git@github.com:ZhenyaBukov/lab06.git projects/lab07
Клонирование в «projects/lab07»...
remote: Enumerating objects: 2968, done.
remote: Counting objects: 100% (2968/2968), done.
remote: Compressing objects: 100% (2259/2259), done.
remote: Total 2968 (delta 537), reused 2964 (delta 535), pack-reused 0 (from 0)
Получение объектов: 100% (2968/2968), 13.47 МиБ | 1.44 МиБ/с, готово.
Определение изменений: 100% (537/537), готово.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ cd projects/lab07
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ git remote remove origin
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ git remote add origin git@github.com:ZhenyaBukov/lab07.git
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ mkdir -p cmake
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ get https://raw.githubusercontent.com/cpp-pm/gate/master/cmake/HunterGate.cmake -O cmake/HunterGate.cmake
Команда «get» не найдена, но есть 18 похожих.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ wget https://raw.githubusercontent.com/cpp-pm/gate/master/cmake/HunterGate.cmake -O cmake/HunterGate.cmake
--2025-05-30 17:03:05--  https://raw.githubusercontent.com/cpp-pm/gate/master/cmake/HunterGate.cmake
Распознаётся raw.githubusercontent.com (raw.githubusercontent.com)… 185.199.108.133, 185.199.110.133, 185.199.109.133, ...
Подключение к raw.githubusercontent.com (raw.githubusercontent.com)|185.199.108.133|:443... соединение установлено.
HTTP-запрос отправлен. Ожидание ответа… 200 OK
Длина: 17231 (17K) [text/plain]
Сохранение в: ‘cmake/HunterGate.cmake’

cmake/HunterGate 100%[=======>]  16,83K  --.-KB/s    за 0,02s   

2025-05-30 17:03:06 (1,08 MB/s) - ‘cmake/HunterGate.cmake’ сохранён [17231/17231]

zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ gsed -i '/cmake_minimum_required(VERSION 3.4)/a\
> 
> include("cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/cpp-pm/hunter/archive/v0.23.251.tar.gz"
    SHA1 "5659b15dc0884d4b03dbd95710e6a1fa0fc3258d"
)
' CMakeLists.txt
sed: -e выражение #1, символ 77: лишние символы после команды
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ git rm -rf third-party/gtest
rm 'third-party/gtest'
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ gsed -i '/set(PRINT_VERSION_STRING "v\${PRINT_VERSION}")/a\
> 
> hunter_add_package(GTest)
find_package(GTest CONFIG REQUIRED)
' CMakeLists.txt
sed: -e выражение #1, символ 54: лишние символы после команды
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ gsed -i 's/add_subdirectory(third-party/gtest)//' CMakeLists.txt
sed: -e выражение #1, символ 39: неизвестный модификатор к `s'
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ gsed -i 's/gtest_main/GTest::main/' CMakeLists.txt
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ cmake -H. -B_builds -DBUILD_TESTS=ON
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
CMake Error at CMakeLists.txt:48 (add_subdirectory):
  add_subdirectory given source "third-party/gtest" which is not an existing
  directory.


-- Configuring incomplete, errors occurred!
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ cmake --build _builds
gmake: Makefile: Нет такого файла или каталога
gmake: *** Нет правила для сборки цели «Makefile».  Останов.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ cmake --build _builds --target test
gmake: Makefile: Нет такого файла или каталога
gmake: *** Нет правила для сборки цели «Makefile».  Останов.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ ls -la $HOME/.hunter
ls: невозможно получить доступ к '/home/zhenya/.hunter': Нет такого файла или каталога
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ git clone https://github.com/cpp-pm/hunter $HOME/projects/hunter
Клонирование в «/home/zhenya/projects/hunter»...
remote: Enumerating objects: 54597, done.
remote: Counting objects: 100% (148/148), done.
remote: Compressing objects: 100% (100/100), done.
remote: Total 54597 (delta 58), reused 72 (delta 9), pack-reused 54449 (from 2)
Получение объектов: 100% (54597/54597), 14.07 МиБ | 2.65 МиБ/с, готово.
Определение изменений: 100% (34134/34134), готово.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ export HUNTER_ROOT=$HOME/projects/hunter
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ rm -rf _builds
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ cmake -H. -B_builds -DBUILD_TESTS=ON
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
CMake Error at CMakeLists.txt:48 (add_subdirectory):
  add_subdirectory given source "third-party/gtest" which is not an existing
  directory.


-- Configuring incomplete, errors occurred!
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ cmake --build _builds
gmake: Makefile: Нет такого файла или каталога
gmake: *** Нет правила для сборки цели «Makefile».  Останов.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ cmake --build _builds --target test
gmake: Makefile: Нет такого файла или каталога
gmake: *** Нет правила для сборки цели «Makefile».  Останов.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ cat $HUNTER_ROOT/cmake/configs/default.cmake | grep GTest
  hunter_default_version(GTest VERSION 1.7.0-hunter-6)
  hunter_default_version(GTest VERSION 1.15.2)
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ cat $HUNTER_ROOT/cmake/projects/GTest/hunter.cmake
# Copyright (c) 2013, Ruslan Baratov
# All rights reserved.

# !!! DO NOT PLACE HEADER GUARDS HERE !!!

include(hunter_add_version)
include(hunter_cacheable)
include(hunter_download)
include(hunter_pick_scheme)
include(hunter_cmake_args)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter.tar.gz"
    SHA1
    1ed1c26d11fb592056c1cb912bd3c784afa96eaa
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-1"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-1.tar.gz"
    SHA1
    0cb1dcf75e144ad052d3f1e4923a7773bf9b494f
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-2"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-2.tar.gz"
    SHA1
    e62b2ef70308f63c32c560f7b6e252442eed4d57
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-3"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-3.tar.gz"
    SHA1
    fea7d3020e20f059255484c69755753ccadf6362
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-4"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-4.tar.gz"
    SHA1
    9b439c0c25437a083957b197ac6905662a5d901b
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-5"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-5.tar.gz"
    SHA1
    796804df3facb074087a4d8ba6f652e5ac69ad7f
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-6"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-6.tar.gz"
    SHA1
    64b93147abe287da8fe4e18cfd54ba9297dafb82
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-7"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-7.tar.gz"
    SHA1
    19b5c98747768bcd0622714f2ed40f17aee406b2
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-8"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-8.tar.gz"
    SHA1
    ac4d2215aa1b1d745a096e5e3b2dbe0c0f229ea5
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-9"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-9.tar.gz"
    SHA1
    8a47fe9c4e550f4ed0e2c05388dd291a059223d9
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-10"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-10.tar.gz"
    SHA1
    374e6dbe8619ab467c6b1a0b470a598407b172e9
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-11"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-11.tar.gz"
    SHA1
    c6ae948ca2bea1d734af01b1069491b00933ed31
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    1.8.0-hunter-p2
    URL
    "https://github.com/hunter-packages/googletest/archive/1.8.0-hunter-p2.tar.gz"
    SHA1
    93148cb8850abe78b76ed87158fdb6b9c48e38c4
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    1.8.0-hunter-p5
    URL https://github.com/hunter-packages/googletest/archive/1.8.0-hunter-p5.tar.gz
    SHA1 3325aa4fc8b30e665c9f73a60f19387b7db36f85
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    1.8.0-hunter-p6
    URL
    "https://github.com/hunter-packages/googletest/archive/1.8.0-hunter-p6.tar.gz"
    SHA1
    f57096bd01c6f8cbef043b312d4d1e82f29648b6
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    1.8.0-hunter-p7
    URL
    "https://github.com/hunter-packages/googletest/archive/1.8.0-hunter-p7.tar.gz"
    SHA1
    4fe083a96d7597f7dce6f453dca01e1d94a1e45b
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    1.8.0-hunter-p8
    URL
    "https://github.com/hunter-packages/googletest/archive/1.8.0-hunter-p8.tar.gz"
    SHA1
    1cdd396b20c8d29f7ea08baaa49673b1c261f545
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    1.8.0-hunter-p9
    URL
    "https://github.com/hunter-packages/googletest/archive/1.8.0-hunter-p9.tar.gz"
    SHA1
    a345f16cb610e0b5dfa7778dc2852b784cfede5b
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    1.8.0-hunter-p10
    URL
    "https://github.com/hunter-packages/googletest/archive/1.8.0-hunter-p10.tar.gz"
    SHA1
    1d92c9f51af756410843b13f8c4e4df09e235394
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.8.0-hunter-p11"
    URL
    "https://github.com/hunter-packages/googletest/archive/1.8.0-hunter-p11.tar.gz"
    SHA1
    76c6aec038f7d7258bf5c4f45c4817b34039d285
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.8.1"
    URL
    "https://github.com/google/googletest/archive/release-1.8.1.tar.gz"
    SHA1
    152b849610d91a9dfa1401293f43230c2e0c33f8
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.10.0"
    URL
    "https://github.com/google/googletest/archive/release-1.10.0.tar.gz"
    SHA1
    9c89be7df9c5e8cb0bc20b3c4b39bf7e82686770
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.10.0-p0"
    URL
    "https://github.com/hunter-packages/googletest/archive/v1.10.0-p0.tar.gz"
    SHA1
    f7c72be12120e018f53cda0e0daa26fab5da7dfc
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.10.0-p1"
    URL
    "https://github.com/hunter-packages/googletest/archive/v1.10.0-p1.tar.gz"
    SHA1
    06a1f667f200ff94d38b608e44c3c8061c7b8f2f
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.11.0"
    URL
    "https://github.com/google/googletest/archive/release-1.11.0.tar.gz"
    SHA1
    7b100bb68db8df1060e178c495f3cbe941c9b058
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.12.1"
    URL
    "https://github.com/google/googletest/archive/release-1.12.1.tar.gz"
    SHA1
    cdddd449d4e3aa7bd421d4519c17139ea1890fe7
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.13.0"
    URL
    "https://github.com/google/googletest/archive/v1.13.0.tar.gz"
    SHA1
    bfa4b5131b6eaac06962c251742c96aab3f7aa78
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.14.0"
    URL
    "https://github.com/google/googletest/archive/v1.14.0.tar.gz"
    SHA1
    2b28c2a3a30d86b1759543ef61fac3c4d69f8c4c
)

hunter_add_version(
        PACKAGE_NAME
        GTest
        VERSION
        "1.15.2"
        URL
        "https://github.com/google/googletest/archive/v1.15.2.tar.gz"
        SHA1
        568d58e26bd4e838449ca7ab8ebc152b3cbd210d
)


if(HUNTER_GTest_VERSION VERSION_LESS 1.8.0 OR HUNTER_GTest_VERSION VERSION_GREATER_EQUAL 1.11.0)
  set(_gtest_license "LICENSE")
else()
  set(_gtest_license "googletest/LICENSE")
endif()

# gtest_force_shared_crt prevents GoogleTest from modifying options
# rather than forcing it to use shared libraries
hunter_cmake_args(
    GTest
    CMAKE_ARGS
    HUNTER_INSTALL_LICENSE_FILES=${_gtest_license}
    gtest_force_shared_crt=TRUE
)

hunter_pick_scheme(DEFAULT url_sha1_cmake)
hunter_cacheable(GTest)
hunter_download(PACKAGE_NAME GTest PACKAGE_INTERNAL_DEPS_ID 1)
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ mkdir cmake/Hunter
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ cat > cmake/Hunter/config.cmake <<EOF
> hunter_config(GTest VERSION 1.7.0-hunter-9)
EOF
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ mkdir demo
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ cat > demo/main.cpp <<EOF
> #include <print.hpp>

#include <cstdlib>

int main(int argc, char* argv[])
{
  const char* log_path = std::getenv("LOG_PATH");
  if (log_path == nullptr)
  {
    std::cerr << "undefined environment variable: LOG_PATH" << std::endl;
    return 1;
  }
  std::string text;
  while (std::cin >> text)
  {
    std::ofstream out{log_path, std::ios_base::app};
    print(text, out);
    out << std::endl;
  }
}
EOF
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ gsed -i '/endif()/a\
> 
> add_executable(demo ${CMAKE_CURRENT_SOURCE_DIR}/demo/main.cpp)
target_link_libraries(demo print)
install(TARGETS demo RUNTIME DESTINATION bin)
' CMakeLists.txt
sed: -e выражение #1, символ 105: лишние символы после команды
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ mkdir tools
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ git submodule add https://github.com/ruslo/polly tools/polly
Клонирование в «/home/zhenya/ZhenyaBukov/workspace/projects/lab07/tools/polly»...
remote: Enumerating objects: 6578, done.
remote: Counting objects: 100% (32/32), done.
remote: Compressing objects: 100% (15/15), done.
remote: Total 6578 (delta 21), reused 20 (delta 17), pack-reused 6546 (from 1)
Получение объектов: 100% (6578/6578), 1.68 МиБ | 1.33 МиБ/с, готово.
Определение изменений: 100% (4551/4551), готово.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ tools/polly/bin/polly.py --test
Python version: 3.12
Build dir: /home/zhenya/ZhenyaBukov/workspace/projects/lab07/_builds/default
Execute command: [
  `which`
  `cmake`
]

[/home/zhenya/ZhenyaBukov/workspace/projects/lab07]> "which" "cmake"

/usr/bin/cmake
Execute command: [
  `cmake`
  `--version`
]

[/home/zhenya/ZhenyaBukov/workspace/projects/lab07]> "cmake" "--version"

cmake version 3.28.3

CMake suite maintained and supported by Kitware (kitware.com/cmake).
Execute command: [
  `cmake`
  `-H.`
  `-B/home/zhenya/ZhenyaBukov/workspace/projects/lab07/_builds/default`
  `-DCMAKE_TOOLCHAIN_FILE=/home/zhenya/ZhenyaBukov/workspace/projects/lab07/tools/polly/default.cmake`
]

[/home/zhenya/ZhenyaBukov/workspace/projects/lab07]> "cmake" "-H." "-B/home/zhenya/ZhenyaBukov/workspace/projects/lab07/_builds/default" "-DCMAKE_TOOLCHAIN_FILE=/home/zhenya/ZhenyaBukov/workspace/projects/lab07/tools/polly/default.cmake"

CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- [polly] Used toolchain: Default
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
-- Configuring done (0.4s)
-- Generating done (0.0s)
-- Build files have been written to: /home/zhenya/ZhenyaBukov/workspace/projects/lab07/_builds/default
Execute command: [
  `cmake`
  `--build`
  `/home/zhenya/ZhenyaBukov/workspace/projects/lab07/_builds/default`
  `--`
]

[/home/zhenya/ZhenyaBukov/workspace/projects/lab07]> "cmake" "--build" "/home/zhenya/ZhenyaBukov/workspace/projects/lab07/_builds/default" "--"

[ 50%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
In file included from /home/zhenya/ZhenyaBukov/workspace/projects/lab07/sources/print.cpp:2:
/home/zhenya/ZhenyaBukov/workspace/projects/lab07/include/print.hpp:6:6: error: default argument given for parameter 2 of ‘void print(const std::string&, std::ostream&)’ [-fpermissive]
    6 | void print(const std::string& text, std::ostream& out = std::cout);
      |      ^~~~~
In file included from /home/zhenya/ZhenyaBukov/workspace/projects/lab07/sources/print.cpp:1:
/home/zhenya/ZhenyaBukov/workspace/projects/lab07/include/print.hpp:6:6: note: previous specification in ‘void print(const std::string&, std::ostream&)’ here
    6 | void print(const std::string& text, std::ostream& out = std::cout);
      |      ^~~~~
gmake[2]: *** [CMakeFiles/print.dir/build.make:76: CMakeFiles/print.dir/sources/print.cpp.o] Ошибка 1
gmake[1]: *** [CMakeFiles/Makefile2:83: CMakeFiles/print.dir/all] Ошибка 2
gmake: *** [Makefile:156: all] Ошибка 2
Command exit with status "2": [/home/zhenya/ZhenyaBukov/workspace/projects/lab07]> "cmake" "--build" "/home/zhenya/ZhenyaBukov/workspace/projects/lab07/_builds/default" "--"

Log: /home/zhenya/ZhenyaBukov/workspace/projects/lab07/_logs/polly/default/log.txt
*** FAILED ***
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ tools/polly/bin/polly.py --install
Python version: 3.12
Build dir: /home/zhenya/ZhenyaBukov/workspace/projects/lab07/_builds/default
Execute command: [
  `which`
  `cmake`
]

[/home/zhenya/ZhenyaBukov/workspace/projects/lab07]> "which" "cmake"

/usr/bin/cmake
Execute command: [
  `cmake`
  `--version`
]

[/home/zhenya/ZhenyaBukov/workspace/projects/lab07]> "cmake" "--version"

cmake version 3.28.3

CMake suite maintained and supported by Kitware (kitware.com/cmake).

== WARNING ==

Looks like cmake arguments changed. You have two options to fix it:
  * Remove build directory completely by adding '--clear' (works 100%)
  * Run configure again by adding '--reconfig' (you must understand how CMake cache variables works/updated)

- "cmake" "-H." "-B/home/zhenya/ZhenyaBukov/workspace/projects/lab07/_builds/default" "-DCMAKE_TOOLCHAIN_FILE=/home/zhenya/ZhenyaBukov/workspace/projects/lab07/tools/polly/default.cmake"
+ "cmake" "-H." "-B/home/zhenya/ZhenyaBukov/workspace/projects/lab07/_builds/default" "-DCMAKE_TOOLCHAIN_FILE=/home/zhenya/ZhenyaBukov/workspace/projects/lab07/tools/polly/default.cmake" "-DCMAKE_INSTALL_PREFIX=/home/zhenya/ZhenyaBukov/workspace/projects/lab07/_install/default"
?                                                                                                                                                                                         ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ tools/polly/bin/polly.py --toolchain clang-cxx14
Python version: 3.12
Build dir: /home/zhenya/ZhenyaBukov/workspace/projects/lab07/_builds/clang-cxx14
Execute command: [
  `which`
  `cmake`
]

[/home/zhenya/ZhenyaBukov/workspace/projects/lab07]> "which" "cmake"

/usr/bin/cmake
Execute command: [
  `cmake`
  `--version`
]

[/home/zhenya/ZhenyaBukov/workspace/projects/lab07]> "cmake" "--version"

cmake version 3.28.3

CMake suite maintained and supported by Kitware (kitware.com/cmake).
Execute command: [
  `cmake`
  `-H.`
  `-B/home/zhenya/ZhenyaBukov/workspace/projects/lab07/_builds/clang-cxx14`
  `-GUnix Makefiles`
  `-DCMAKE_TOOLCHAIN_FILE=/home/zhenya/ZhenyaBukov/workspace/projects/lab07/tools/polly/clang-cxx14.cmake`
]

[/home/zhenya/ZhenyaBukov/workspace/projects/lab07]> "cmake" "-H." "-B/home/zhenya/ZhenyaBukov/workspace/projects/lab07/_builds/clang-cxx14" "-GUnix Makefiles" "-DCMAKE_TOOLCHAIN_FILE=/home/zhenya/ZhenyaBukov/workspace/projects/lab07/tools/polly/clang-cxx14.cmake"

CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- [polly] Used toolchain: clang / c++14 support

clang not found

CMake Error at tools/polly/utilities/polly_fatal_error.cmake:10 (message):
Call Stack (most recent call first):
  tools/polly/compiler/clang.cmake:23 (polly_fatal_error)
  tools/polly/clang-cxx14.cmake:20 (include)
  /usr/share/cmake-3.28/Modules/CMakeDetermineSystem.cmake:170 (include)
  CMakeLists.txt:9 (project)


CMake Error: CMake was unable to find a build program corresponding to "Unix Makefiles".  CMAKE_MAKE_PROGRAM is not set.  You probably need to select a different build tool.
-- Configuring incomplete, errors occurred!
Command exit with status "1": [/home/zhenya/ZhenyaBukov/workspace/projects/lab07]> "cmake" "-H." "-B/home/zhenya/ZhenyaBukov/workspace/projects/lab07/_builds/clang-cxx14" "-GUnix Makefiles" "-DCMAKE_TOOLCHAIN_FILE=/home/zhenya/ZhenyaBukov/workspace/projects/lab07/tools/polly/clang-cxx14.cmake"

Log: /home/zhenya/ZhenyaBukov/workspace/projects/lab07/_logs/polly/clang-cxx14/log.txt
*** FAILED ***
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ git push origin main
To github.com:ZhenyaBukov/lab07.git
 ! [rejected]        main -> main (fetch first)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab07.git»
подсказка: Updates were rejected because the remote contains work that you do not
подсказка: have locally. This is usually caused by another repository pushing to
подсказка: the same ref. If you want to integrate the remote changes, use
подсказка: 'git pull' before pushing again.
подсказка: See the 'Note about fast-forwards' in 'git push --help' for details.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ git push -f origin main
Перечисление объектов: 2968, готово.
Подсчет объектов: 100% (2968/2968), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2257/2257), готово.
Запись объектов: 100% (2968/2968), 13.47 МиБ | 1.80 МиБ/с, готово.
Всего 2968 (изменений 537), повторно использовано 2968 (изменений 537), повторно использовано пакетов 0
remote: Resolving deltas: 100% (537/537), done.
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
remote:        https://github.com/ZhenyaBukov/lab07/security/secret-scanning/unblock-secret/2xopggDMohaxSp4LjWVTG5vCDAo
remote:     
remote:     
remote:       —— GitHub Personal Access Token ——————————————————————
remote:        locations:
remote:          - commit: c71fea93dbceb60601f9d9cc6175713b8e8fa5ba
remote:            path: README.md:3
remote:     
remote:        (?) To push, remove secret from commit(s) or follow this URL to allow the secret.
remote:        https://github.com/ZhenyaBukov/lab07/security/secret-scanning/unblock-secret/2xopgbX2Rv0gsnrIwdh74R7tYPY
remote:     
remote: 
remote: 
To github.com:ZhenyaBukov/lab07.git
 ! [remote rejected] main -> main (push declined due to repository rule violations)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab07.git»
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ git push -f origin main
Перечисление объектов: 2968, готово.
Подсчет объектов: 100% (2968/2968), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2257/2257), готово.
Запись объектов: 100% (2968/2968), 13.47 МиБ | 1.58 МиБ/с, готово.
Всего 2968 (изменений 537), повторно использовано 2968 (изменений 537), повторно использовано пакетов 0
remote: Resolving deltas: 100% (537/537), done.
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
remote:        https://github.com/ZhenyaBukov/lab07/security/secret-scanning/unblock-secret/2xopggDMohaxSp4LjWVTG5vCDAo
remote:     
remote: 
remote: 
To github.com:ZhenyaBukov/lab07.git
 ! [remote rejected] main -> main (push declined due to repository rule violations)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab07.git»
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ git push origin main
To github.com:ZhenyaBukov/lab07.git
 ! [rejected]        main -> main (fetch first)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab07.git»
подсказка: Updates were rejected because the remote contains work that you do not
подсказка: have locally. This is usually caused by another repository pushing to
подсказка: the same ref. If you want to integrate the remote changes, use
подсказка: 'git pull' before pushing again.
подсказка: See the 'Note about fast-forwards' in 'git push --help' for details.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$ git push -f origin main
Перечисление объектов: 2968, готово.
Подсчет объектов: 100% (2968/2968), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2257/2257), готово.
Запись объектов: 100% (2968/2968), 13.47 МиБ | 3.88 МиБ/с, готово.
Всего 2968 (изменений 537), повторно использовано 2968 (изменений 537), повторно использовано пакетов 0
remote: Resolving deltas: 100% (537/537), done.
To github.com:ZhenyaBukov/lab07.git
 + b525839...96b99df main -> main (forced update)
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab07$  

