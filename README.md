<фрагмент_вставки_значка>
$ export GITHUB_USERNAME=ZhenyaBukov

$ cd ${GITHUB_USERNAME}/workspace
/ZhenyaBukov/workspace$ pushd .
~/ZhenyaBukov/workspace ~/ZhenyaBukov/workspace
/ZhenyaBukov/workspace$ source scripts/activate

/ZhenyaBukov/workspace$ git clone git@github.com:ZhenyaBukov/lab02.git projects/lab03
Клонирование в «projects/lab03»...
remote: Enumerating objects: 2936, done.
remote: Counting objects: 100% (2936/2936), done.
remote: Compressing objects: 100% (2244/2244), done.
remote: Total 2936 (delta 523), reused 2925 (delta 519), pack-reused 0 (from 0)
Получение объектов: 100% (2936/2936), 13.45 МиБ | 1.87 МиБ/с, готово.
Определение изменений: 100% (523/523), готово.
/ZhenyaBukov/workspace$ cd projects/lab03
/ZhenyaBukov/workspace$ git remote remove origin
/ZhenyaBukov/workspace/projects/lab03$ git remote add origin git@github.com:ZhenyaBukov/lab03.git

/ZhenyaBukov/workspace/projects/lab03$ g++ -std=c++11 -I./include -c sources/print.cpp
/ZhenyaBukov/workspace/projects/lab03$ ls print.o
print.o
/ZhenyaBukov/workspace/projects/lab03$ nm print.o | grep print
0000000000000000 T _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSo
000000000000002a T _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSt14basic_ofstreamIcS2_E
/ZhenyaBukov/workspace/projects/lab03$ ar rvs print.a print.o
ar: создаётся print.a
a - print.o
/ZhenyaBukov/workspace/projects/lab03$ file print.a
print.a: current ar archive
/ZhenyaBukov/workspace/projects/lab03$ g++ -std=c++11 -I./include -c examples/example1.cpp
/ZhenyaBukov/workspace/projects/lab03$ ls example1.o
example1.o
/ZhenyaBukov/workspace/projects/lab03$ g++ example1.o print.a -o example
/ZhenyaBukov/workspace/projects/lab03$ ./example1 && echo
hello

/ZhenyaBukov/workspace/projects/lab03$ g++ -std=c++11 -I./include -c examples/example2.cpp
/ZhenyaBukov/workspace/projects/lab03$ nm example2.o
0000000000000000 V DW.ref.__gxx_personality_v0
                 U __gxx_personality_v0
0000000000000000 T main
                 U __stack_chk_fail
                 U _Unwind_Resume
                 U _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSt14basic_ofstreamIcS2_E
                 U _ZNSt14basic_ofstreamIcSt11char_traitsIcEEC1EPKcSt13_Ios_Openmode
                 U _ZNSt14basic_ofstreamIcSt11char_traitsIcEED1Ev
0000000000000000 W _ZNSt15__new_allocatorIcED1Ev
0000000000000000 W _ZNSt15__new_allocatorIcED2Ev
0000000000000000 n _ZNSt15__new_allocatorIcED5Ev
                 U _ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEC1EPKcRKS3_
                 U _ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEED1Ev
                 U _ZSt21ios_base_library_initv
0000000000000000 r _ZStL19piecewise_construct
/ZhenyaBukov/workspace/projects/lab03$ g++ example2.o print.a -o example2
/ZhenyaBukov/workspace/projects/lab03$ ./example2
/ZhenyaBukov/workspace/projects/lab03$ cat log.txt && echo
hello

/ZhenyaBukov/workspace/projects/lab03$ rm -rf example1.o example2.o print.o
/ZhenyaBukov/workspace/projects/lab03$ rm -rf print.a
/ZhenyaBukov/workspace/projects/lab03$ rm -rf example1 example2
/ZhenyaBukov/workspace/projects/lab03$ rm -rf log.txt

/ZhenyaBukov/workspace/projects/lab03$ cat > CMakeLists.txt <<EOF
> cmake_minimum_required(VERSION 3.4)
project(print)
EOF

/ZhenyaBukov/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
> set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
EOF

/ZhenyaBukov/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
> add_library(print STATIC \${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)
EOF

/ZhenyaBukov/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
> include_directories(\${CMAKE_CURRENT_SOURCE_DIR}/include)
EOF

/ZhenyaBukov/workspace/projects/lab03$ cmake -H. -B_build
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
-- Configuring done (0.4s)
-- Generating done (0.0s)
-- Build files have been written to: /home/zhenya/ZhenyaBukov/workspace/projects/lab03/_build
/ZhenyaBukov/workspace/projects/lab03$ cmake --build _build
[ 50%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[100%] Linking CXX static library libprint.a
[100%] Built target print

/ZhenyaBukov/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
> 
> add_executable(example1 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example1.cpp)
add_executable(example2 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example2.cpp)
EOF

/ZhenyaBukov/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
> 
> target_link_libraries(example1 print)
target_link_libraries(example2 print)
EOF

/ZhenyaBukov/workspace/projects/lab03$ cmake --build _build
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (0.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/zhenya/ZhenyaBukov/workspace/projects/lab03/_build
[ 33%] Built target print
[ 50%] Building CXX object CMakeFiles/example1.dir/examples/example1.cpp.o
[ 66%] Linking CXX executable example1
[ 66%] Built target example1
[ 83%] Building CXX object CMakeFiles/example2.dir/examples/example2.cpp.o
[100%] Linking CXX executable example2
[100%] Built target example2
/ZhenyaBukov/workspace/projects/lab03$ cmake --build _build --target print
[100%] Built target print
/ZhenyaBukov/workspace/projects/lab03$ cmake --build _build --target example1
[ 50%] Built target print
[100%] Built target example1
/ZhenyaBukov/workspace/projects/lab03$ cmake --build _build --target example2
[ 50%] Built target print
[100%] Built target example2

/ZhenyaBukov/workspace/projects/lab03$ ls -la _build/libprint.a
-rw-rw-r-- 1 zhenya zhenya 2246 мая 18 01:26 _build/libprint.a
/ZhenyaBukov/workspace/projects/lab03$ _build/example1 && echo
hello
/ZhenyaBukov/workspace/projects/lab03$ _build/example2
/ZhenyaBukov/workspace/projects/lab03$ cat log.txt && echo
hello
/ZhenyaBukov/workspace/projects/lab03$ rm -rf log.txt

/ZhenyaBukov/workspace/projects/lab03$ git clone git@github.com:ZhenyaBukov/lab03.git tmp
Клонирование в «tmp»...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Получение объектов: 100% (3/3), готово.
/ZhenyaBukov/workspace/projects/lab03$ mv -f tmp/CMakeLists.txt .
mv: не удалось выполнить stat для 'tmp/CMakeLists.txt': Нет такого файла или каталога
/ZhenyaBukov/workspace/projects/lab03$ rm -rf tmp

/ZhenyaBukov/workspace/projects/lab03$ cat CMakeLists.txt
cmake_minimum_required(VERSION 3.4)
project(print)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_library(print STATIC ${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

add_executable(example1 ${CMAKE_CURRENT_SOURCE_DIR}/examples/example1.cpp)
add_executable(example2 ${CMAKE_CURRENT_SOURCE_DIR}/examples/example2.cpp)

target_link_libraries(example1 print)
target_link_libraries(example2 print)
/ZhenyaBukov/workspace/projects/lab03$ cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (0.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/zhenya/ZhenyaBukov/workspace/projects/lab03/_build
/ZhenyaBukov/workspace/projects/lab03$ cmake --build _build --target install
gmake: *** Нет правила для сборки цели «install».  Останов.
/ZhenyaBukov/workspace/projects/lab03$ tree _install
_install  [error opening dir]

0 directories, 0 files

/ZhenyaBukov/workspace/projects/lab03$ git add CMakeLists.txt
/ZhenyaBukov/workspace/projects/lab03$ git commit -m"added CMakeLists.txt"
[main 39df7fa] added CMakeLists.txt
 1 file changed, 12 insertions(+)
 create mode 100644 CMakeLists.txt
/ZhenyaBukov/workspace/projects/lab03$ git push -f origin main
Перечисление объектов: 2939, готово.
Подсчет объектов: 100% (2939/2939), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2243/2243), готово.
Запись объектов: 100% (2939/2939), 13.45 МиБ | 926.00 КиБ/с, готово.
Всего 2939 (изменений 524), повторно использовано 2935 (изменений 523), повторно использовано пакетов 0
remote: Resolving deltas: 100% (524/524), done.
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
remote:          - commit: c71fea93dbceb60601f9d9cc6175713b8e8fa5ba
remote:            path: README.md:3
remote:     
remote:        (?) To push, remove secret from commit(s) or follow this URL to allow the secret.
remote:        https://github.com/ZhenyaBukov/lab03/security/secret-scanning/unblock-secret/2xHSPLtAuP7j3Y3oII6BgXUtTGa
remote:     
remote: 
remote: 
To github.com:ZhenyaBukov/lab03.git
 ! [remote rejected] main -> main (push declined due to repository rule violations)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab03.git»
/ZhenyaBukov/workspace/projects/lab03$ git push -f origin main
Перечисление объектов: 2939, готово.
Подсчет объектов: 100% (2939/2939), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2243/2243), готово.
Запись объектов: 100% (2939/2939), 13.45 МиБ | 1.16 МиБ/с, готово.
Всего 2939 (изменений 524), повторно использовано 2935 (изменений 523), повторно использовано пакетов 0
remote: Resolving deltas: 100% (524/524), done.
To github.com:ZhenyaBukov/lab03.git
 + e050b8d...39df7fa main -> main (forced update)
/ZhenyaBukov/workspace/projects/lab03$ git push origin main
Everything up-to-date

