zhenya@zhenya-VirtualBox:~$ export GITHUB_USERNAME=ZhenyaBukov
zhenya@zhenya-VirtualBox:~$ export GITHUB_TOKEN=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



zhenya@zhenya-VirtualBox:~$ cd ${GITHUB_USERNAME}/workspace
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ pushd .
~/ZhenyaBukov/workspace ~/ZhenyaBukov/workspace
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ source scripts/activate




zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ sudo snap install curl
[sudo] пароль для zhenya:
curl 8.13.0 от hideo aoyama (aoilinux) installed
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ \curl -sSL https://get.rvm.io | bash -s -- --ignore-dotfiles
Turning on ignore dotfiles mode.
Downloading https://github.com/rvm/rvm/archive/master.tar.gz
Installing RVM to /home/zhenya/.rvm/
Installation of RVM in /home/zhenya/.rvm/ is almost complete:
 
  * To start using RVM you need to run `source /home/zhenya/.rvm/scripts/rvm`
    in all your open shell windows, in rare cases you need to reopen all shell windows.
Thanks for installing RVM 🙏
Please consider donating to our open collective to help us maintain RVM.
 
👉  Donate: https://opencollective.com/rvm/donate
 
 
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ echo "source $HOME/.rvm/scripts/rvm" >> scripts/activate
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ . scripts/activate
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ rvm autolibs disable
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ gem install travis
Fetching multi_json-1.15.0.gem
Fetching net-http-pipeline-1.0.1.gem
Fetching net-http-persistent-4.0.5.gem
Fetching faraday-retry-2.3.1.gem
Fetching faraday-2.7.12.gem
Fetching connection_pool-2.5.3.gem
Fetching faraday-typhoeus-1.1.0.gem
Fetching tzinfo-2.0.6.gem
Fetching public_suffix-6.0.2.gem
Fetching faraday-net_http-3.0.2.gem
Fetching ffi-1.17.2-x86_64-linux-gnu.gem
Fetching rack-3.1.15.gem
Fetching typhoeus-1.4.1.gem
Fetching addressable-2.8.7.gem
Fetching travis-gh-0.21.0.gem
Fetching concurrent-ruby-1.3.5.gem
Fetching i18n-1.14.7.gem
Fetching activesupport-7.0.8.7.gem
Fetching pusher-client-0.6.2.gem
Fetching json_pure-2.6.3.gem
Fetching rack-test-2.1.0.gem
Fetching websocket-1.2.11.gem
Fetching faraday-rack-2.1.2.gem
Fetching travis-1.14.0.gem
Fetching ethon-0.16.0.gem
Fetching highline-2.1.0.gem
Fetching launchy-2.5.2.gem
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /var/lib/gems/3.2.0 directory.
    /usr/lib/ruby/vendor_ruby/rubygems/installer.rb:713:in `verify_gem_home'
    /usr/lib/ruby/vendor_ruby/rubygems/installer.rb:903:in `pre_install_checks'
    /usr/lib/ruby/vendor_ruby/rubygems/installer.rb:303:in `install'
    /usr/lib/ruby/vendor_ruby/rubygems/resolver/specification.rb:105:in `install'
    /usr/lib/ruby/vendor_ruby/rubygems/request_set.rb:195:in `block in install'
    /usr/lib/ruby/vendor_ruby/rubygems/request_set.rb:183:in `each'
    /usr/lib/ruby/vendor_ruby/rubygems/request_set.rb:183:in `install'
    /usr/lib/ruby/vendor_ruby/rubygems/commands/install_command.rb:215:in `install_gem'
    /usr/lib/ruby/vendor_ruby/rubygems/commands/install_command.rb:231:in `block in install_gems'
    /usr/lib/ruby/vendor_ruby/rubygems/commands/install_command.rb:224:in `each'
    /usr/lib/ruby/vendor_ruby/rubygems/commands/install_command.rb:224:in `install_gems'
    /usr/lib/ruby/vendor_ruby/rubygems/commands/install_command.rb:170:in `execute'
    /usr/lib/ruby/vendor_ruby/rubygems/command.rb:328:in `invoke_with_build_args'
    /usr/lib/ruby/vendor_ruby/rubygems/command_manager.rb:253:in `invoke_command'
    /usr/lib/ruby/vendor_ruby/rubygems/command_manager.rb:193:in `process_args'
    /usr/lib/ruby/vendor_ruby/rubygems/command_manager.rb:151:in `run'
    /usr/lib/ruby/vendor_ruby/rubygems/gem_runner.rb:52:in `run'
    /usr/bin/gem:12:in `<main>'


    
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ git clone git@github.com:ZhenyaBukov/lab03.git projects/lab04
Клонирование в «projects/lab04»...
remote: Enumerating objects: 2942, done.
remote: Counting objects: 100% (2942/2942), done.
remote: Compressing objects: 100% (2245/2245), done.
remote: Total 2942 (delta 525), reused 2938 (delta 524), pack-reused 0 (from 0)
Получение объектов: 100% (2942/2942), 13.45 МиБ | 2.16 МиБ/с, готово.
Определение изменений: 100% (525/525), готово.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ cd projects/lab04
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git remote remove origin
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git remote add origin git@github.com:ZhenyaBukov/lab04.git



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ cat > .travis.yml <<EOF
> language: cpp
EOF



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ cat >> .travis.yml <<EOF
>
> script:
- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
- cmake --build _build
- cmake --build _build --target install
EOF




zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ cat >> .travis.yml <<EOF
>
> addons:
  apt:
    sources:
      - george-edison55-precise-backports
    packages:
      - cmake
      - cmake-data
EOF




zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ sudo snap install travis
travis 1.8.9 от Travis CI✓ installed
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ travis login --github-token ${GITHUB_TOKEN}
Outdated CLI version, run `gem install travis`.
resource not found ({}
)
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ sudo apt  install travis
Чтение списков пакетов… Готово
Построение дерева зависимостей… Готово
Чтение информации о состоянии… Готово         
Предлагаемые пакеты:
  cp2k gnuplot grace graphviz pymol
Следующие НОВЫЕ пакеты будут установлены:
  travis
Обновлено 0 пакетов, установлено 1 новых пакетов, для удаления отмечено 0 пакетов, и 111 пакетов не обновлено.
Необходимо скачать 1526 kB архивов.
После данной операции объём занятого дискового пространства возрастёт на 3864 kB.
Пол:1 http://ru.archive.ubuntu.com/ubuntu noble/universe amd64 travis amd64 220729-1 [1526 kB]
Получено 1526 kB за 1с (1753 kB/s)    
Выбор ранее не выбранного пакета travis.
(Чтение базы данных … на данный момент установлено 158335 файлов и
 каталогов.)
Подготовка к распаковке …/travis_220729-1_amd64.deb …
Распаковывается travis (220729-1) …
Настраивается пакет travis (220729-1) …
Обрабатываются триггеры для man-db (2.12.0-4build2) …
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ travis login --github-token ${GITHUB_TOKEN}
Outdated CLI version, run `gem install travis`.
resource not found ({}
)
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ travis lint
Outdated CLI version, run `gem install travis`.
405: "<!doctype html>\n<html lang=en>\n<title>405 Method Not Allowed</title>\n<h1>Method Not Allowed</h1>\n<p>The method is not allowed for the requested URL.</p>\n"
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ sudo apt-get install ruby-full
Чтение списков пакетов… Готово
Построение дерева зависимостей… Готово
Чтение информации о состоянии… Готово         
Будут установлены следующие дополнительные пакеты:
  libgmp-dev libgmpxx4ldbl ri ruby-dev ruby3.2-dev ruby3.2-doc
Предлагаемые пакеты:
  gmp-doc libgmp10-doc libmpfr-dev
Следующие НОВЫЕ пакеты будут установлены:
  libgmp-dev libgmpxx4ldbl ri ruby-dev ruby-full ruby3.2-dev
  ruby3.2-doc
Обновлено 0 пакетов, установлено 7 новых пакетов, для удаления отмечено 0 пакетов, и 111 пакетов не обновлено.
Необходимо скачать 2779 kB архивов.
После данной операции объём занятого дискового пространства возрастёт на 23,4 MB.
Хотите продолжить? [Д/н] Д
Пол:1 http://ru.archive.ubuntu.com/ubuntu noble-updates/main amd64 libgmpxx4ldbl amd64 2:6.3.0+dfsg-2ubuntu6.1 [9888 B]
Пол:2 http://ru.archive.ubuntu.com/ubuntu noble-updates/main amd64 libgmp-dev amd64 2:6.3.0+dfsg-2ubuntu6.1 [340 kB]
Пол:3 http://ru.archive.ubuntu.com/ubuntu noble-updates/main amd64 ruby3.2-doc all 3.2.3-1ubuntu0.24.04.5 [2017 kB]
Пол:4 http://ru.archive.ubuntu.com/ubuntu noble/universe amd64 ri all 1:3.2~ubuntu1 [4724 B]
Пол:5 http://ru.archive.ubuntu.com/ubuntu noble-updates/main amd64 ruby3.2-dev amd64 3.2.3-1ubuntu0.24.04.5 [399 kB]
Пол:6 http://ru.archive.ubuntu.com/ubuntu noble/main amd64 ruby-dev amd64 1:3.2~ubuntu1 [4856 B]
Пол:7 http://ru.archive.ubuntu.com/ubuntu noble/universe amd64 ruby-full all 1:3.2~ubuntu1 [2570 B]
Получено 2779 kB за 1с (3274 kB/s)     
Выбор ранее не выбранного пакета libgmpxx4ldbl:amd64.
(Чтение базы данных … на данный момент установлено 158343 файла и каталога.)
Подготовка к распаковке …/0-libgmpxx4ldbl_2%3a6.3.0+dfsg-2ubuntu6.1_amd64.deb …
Распаковывается libgmpxx4ldbl:amd64 (2:6.3.0+dfsg-2ubuntu6.1) …
Выбор ранее не выбранного пакета libgmp-dev:amd64.
Подготовка к распаковке …/1-libgmp-dev_2%3a6.3.0+dfsg-2ubuntu6.1_amd64.deb …
Распаковывается libgmp-dev:amd64 (2:6.3.0+dfsg-2ubuntu6.1) …
Выбор ранее не выбранного пакета ruby3.2-doc.
Подготовка к распаковке …/2-ruby3.2-doc_3.2.3-1ubuntu0.24.04.5_all.deb …
Распаковывается ruby3.2-doc (3.2.3-1ubuntu0.24.04.5) …
Выбор ранее не выбранного пакета ri.
Подготовка к распаковке …/3-ri_1%3a3.2~ubuntu1_all.deb …
Распаковывается ri (1:3.2~ubuntu1) …
Выбор ранее не выбранного пакета ruby3.2-dev:amd64.
Подготовка к распаковке …/4-ruby3.2-dev_3.2.3-1ubuntu0.24.04.5_amd64.deb …
Распаковывается ruby3.2-dev:amd64 (3.2.3-1ubuntu0.24.04.5) …
Выбор ранее не выбранного пакета ruby-dev:amd64.
Подготовка к распаковке …/5-ruby-dev_1%3a3.2~ubuntu1_amd64.deb …
Распаковывается ruby-dev:amd64 (1:3.2~ubuntu1) …
Выбор ранее не выбранного пакета ruby-full.
Подготовка к распаковке …/6-ruby-full_1%3a3.2~ubuntu1_all.deb …
Распаковывается ruby-full (1:3.2~ubuntu1) …
Настраивается пакет ruby3.2-doc (3.2.3-1ubuntu0.24.04.5) …
Настраивается пакет ri (1:3.2~ubuntu1) …
Настраивается пакет libgmpxx4ldbl:amd64 (2:6.3.0+dfsg-2ubuntu6.1) …
Настраивается пакет libgmp-dev:amd64 (2:6.3.0+dfsg-2ubuntu6.1) …
Настраивается пакет ruby3.2-dev:amd64 (3.2.3-1ubuntu0.24.04.5) …
Настраивается пакет ruby-dev:amd64 (1:3.2~ubuntu1) …
Настраивается пакет ruby-full (1:3.2~ubuntu1) …
Обрабатываются триггеры для libc-bin (2.39-0ubuntu8.4) …
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ travis login --github-token ${GITHUB_TOKEN}
 
  ________                                 __
 /        |                               /  |
 ########/ ______    ______    __     __  ##/    _______
    ## |  /      \  /      \  /  \   /  | /  |  /       |
    ## | /######  | ######  | ##  \ /##/  ## | /#######/
    ## | ## |  ##/  /    ## |  ##  /##/   ## | ##      \
    ## | ## |      /####### |   ## ##/    ## |  ######  |
    ## | ## |      ##    ## |    ###/     ## | /     ##/
    ##/  ##/        #######/      #/      ##/  #######/
 
    TRajectory Analyzer and VISualizer  -  Open-source free software under GNU GPL v3
 
    Copyright (c) Martin Brehm      (2009-2022), University of Halle (Saale)
                  Martin Thomas     (2012-2022)
                  Sascha Gehrke     (2016-2022), University of Bonn
                  Barbara Kirchner  (2009-2022), University of Bonn
 
    http://www.travis-analyzer.de
 
    Please cite: J. Chem. Phys. 2020, 152 (16), 164105.         (DOI 10.1063/5.0005078 )
                 J. Chem. Inf. Model. 2011, 51 (8), 2007-2023.  (DOI 10.1021/ci200217w )
 
    There is absolutely no warranty on any results obtained from TRAVIS.
 
 #  Running on zhenya-VirtualBox at Sun May 18 23:42:04 2025 (PID 29522)
 #  Running in /home/zhenya/ZhenyaBukov/workspace/projects/lab04
 #  Version: Jul 29 2022, built at Jan 14 2023, 12:32:45, compiler "12.2.0", GCC 12.2.0
 #  Target platform: Linux, __cplusplus=201703L, Compile flags: NEW_CHARGEVAR DEBUG_ARRAYS
 #  Compiled with OpenMP, but USE_OMP not switched on in "config.h"!
 #  Machine: x86_64, char=1b, int=4b, long=8b, addr=8b, 0xA0B0C0D0=D0,C0,B0,A0.
 #  Home: /home/zhenya,  Executable: /usr/bin/travis
 #  Input from terminal,  Output to terminal
 
    >>> Please use a color scheme with dark background or specify "-nocolor"! <<<
 
    No configuration file found.
    Writing default configuration to /home/zhenya/.travis.conf ...
 
Unknown parameter: "login".
 
    List of supported command line options:
 
      -p <file>       Load position data from specified trajectory file.
                      Format may be *.xyz, *.pdb, *.lmp (LAMMPS), HISTORY (DLPOLY), POSCAR/XDATCAR (VASP),
                                    *.gro, *.dcd, or *.prmtop/*.mdcrd (Amber).
                      The bqb format (*.bqb, *.btr, *.emp, *.blist) as well as *.voronoi are also supported.
      -vel <file>     Read atom velocities from a file in addition to the position trajectory.
                      Currently, only .xyz format is supported for velocity data.
      -i <file>       Read input from specified text file.
      -c <file>       Read and execute control file (experimental).
      cubetool        Execute the CubeTool for modifying Gaussian Cube files.
      -sankey <file>  Create Sankey diagrams (file name is optional).
      -ramanfrompola  Compute Raman spectra from existing polarizability time series.
      (de-)compress   Start built-in bqbtool (compress trajectories to BQB format).
      check           Check BQB file integrity.
 
      -config <file>  Load the specified configuration file.
      -stream         Treat input trajectory as a stream (e.g. named pipe): No fseek, etc.
      -showconf       Show a tree structure of the configuration file.
      -writeconf      Write the default configuration file, including all defines values.
 
      -verbose        Show detailed information about what's going on.
      -nocolor        Execute TRAVIS in monochrome mode (suitable for white background).
      -dimcolor       Use dim instead of bright colors.
 
      -credits        Display a list of persons who contributed to TRAVIS.
      -help, -?       Shows this help.
 
    If only one argument is specified, it is assumed to be the name of a trajectory file.
    If no argument is specified at all, TRAVIS asks for the trajectory file to open.
 
    Note: To show a list of all persons who contributed to TRAVIS,
          please add "-credits" to your command line arguments, or set the
          variable "SHOWCREDITS" to "TRUE" in your travis.conf file.
 
    Source code from other projects used in TRAVIS:
      - lmfit     from Joachim Wuttke
      - kiss_fft  from Mark Borgerding
      - voro++    from Chris Rycroft
 
    http://www.travis-analyzer.de
 
    Please cite all of the following articles for the analyses you have used:
 
  * For TRAVIS in general:
 
    "TRAVIS - A Free Analyzer for Trajectories from Molecular Simulation",
    M. Brehm, M. Thomas, S. Gehrke, B. Kirchner; J. Chem. Phys. 2020, 152 (16), 164105.   (DOI 10.1063/5.0005078 )
 
    "TRAVIS - A Free Analyzer and Visualizer for Monte Carlo and Molecular Dynamics Trajectories",
    M. Brehm, B. Kirchner; J. Chem. Inf. Model. 2011, 51 (8), pp 2007-2023.   (DOI 10.1021/ci200217w )
 
*** The End ***
 
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ travis lint
[Renaming existing File travis.log to #2#travis.log ...OK.]
 
  ________                                 __
 /        |                               /  |
 ########/ ______    ______    __     __  ##/    _______
    ## |  /      \  /      \  /  \   /  | /  |  /       |
    ## | /######  | ######  | ##  \ /##/  ## | /#######/
    ## | ## |  ##/  /    ## |  ##  /##/   ## | ##      \
    ## | ## |      /####### |   ## ##/    ## |  ######  |
    ## | ## |      ##    ## |    ###/     ## | /     ##/
    ##/  ##/        #######/      #/      ##/  #######/
 
    TRajectory Analyzer and VISualizer  -  Open-source free software under GNU GPL v3
 
    Copyright (c) Martin Brehm      (2009-2022), University of Halle (Saale)
                  Martin Thomas     (2012-2022)
                  Sascha Gehrke     (2016-2022), University of Bonn
                  Barbara Kirchner  (2009-2022), University of Bonn
 
    http://www.travis-analyzer.de
 
    Please cite: J. Chem. Phys. 2020, 152 (16), 164105.         (DOI 10.1063/5.0005078 )
                 J. Chem. Inf. Model. 2011, 51 (8), 2007-2023.  (DOI 10.1021/ci200217w )
 
    There is absolutely no warranty on any results obtained from TRAVIS.
 
 #  Running on zhenya-VirtualBox at Sun May 18 23:42:43 2025 (PID 29534)
 #  Running in /home/zhenya/ZhenyaBukov/workspace/projects/lab04
 #  Version: Jul 29 2022, built at Jan 14 2023, 12:32:45, compiler "12.2.0", GCC 12.2.0
 #  Target platform: Linux, __cplusplus=201703L, Compile flags: NEW_CHARGEVAR DEBUG_ARRAYS
 #  Compiled with OpenMP, but USE_OMP not switched on in "config.h"!
 #  Machine: x86_64, char=1b, int=4b, long=8b, addr=8b, 0xA0B0C0D0=D0,C0,B0,A0.
 #  Home: /home/zhenya,  Executable: /usr/bin/travis
 #  Input from terminal,  Output to terminal
 
    >>> Please use a color scheme with dark background or specify "-nocolor"! <<<
 
    Loading configuration from /home/zhenya/.travis.conf ...
 
[Renaming existing File input.txt to #2#input.txt ...OK.]
Unknown parameter: "lint".
 
    List of supported command line options:
 
      -p <file>       Load position data from specified trajectory file.
                      Format may be *.xyz, *.pdb, *.lmp (LAMMPS), HISTORY (DLPOLY), POSCAR/XDATCAR (VASP),
                                    *.gro, *.dcd, or *.prmtop/*.mdcrd (Amber).
                      The bqb format (*.bqb, *.btr, *.emp, *.blist) as well as *.voronoi are also supported.
      -vel <file>     Read atom velocities from a file in addition to the position trajectory.
                      Currently, only .xyz format is supported for velocity data.
      -i <file>       Read input from specified text file.
      -c <file>       Read and execute control file (experimental).
      cubetool        Execute the CubeTool for modifying Gaussian Cube files.
      -sankey <file>  Create Sankey diagrams (file name is optional).
      -ramanfrompola  Compute Raman spectra from existing polarizability time series.
      (de-)compress   Start built-in bqbtool (compress trajectories to BQB format).
      check           Check BQB file integrity.
 
      -config <file>  Load the specified configuration file.
      -stream         Treat input trajectory as a stream (e.g. named pipe): No fseek, etc.
      -showconf       Show a tree structure of the configuration file.
      -writeconf      Write the default configuration file, including all defines values.
 
      -verbose        Show detailed information about what's going on.
      -nocolor        Execute TRAVIS in monochrome mode (suitable for white background).
      -dimcolor       Use dim instead of bright colors.
 
      -credits        Display a list of persons who contributed to TRAVIS.
      -help, -?       Shows this help.
 
    If only one argument is specified, it is assumed to be the name of a trajectory file.
    If no argument is specified at all, TRAVIS asks for the trajectory file to open.
 
    Note: To show a list of all persons who contributed to TRAVIS,
          please add "-credits" to your command line arguments, or set the
          variable "SHOWCREDITS" to "TRUE" in your travis.conf file.
 
    Source code from other projects used in TRAVIS:
      - lmfit     from Joachim Wuttke
      - kiss_fft  from Mark Borgerding
      - voro++    from Chris Rycroft
 
    http://www.travis-analyzer.de
 
    Please cite all of the following articles for the analyses you have used:
 
  * For TRAVIS in general:
 
    "TRAVIS - A Free Analyzer for Trajectories from Molecular Simulation",
    M. Brehm, M. Thomas, S. Gehrke, B. Kirchner; J. Chem. Phys. 2020, 152 (16), 164105.   (DOI 10.1063/5.0005078 )
 
    "TRAVIS - A Free Analyzer and Visualizer for Monte Carlo and Molecular Dynamics Trajectories",
    M. Brehm, B. Kirchner; J. Chem. Inf. Model. 2011, 51 (8), pp 2007-2023.   (DOI 10.1021/ci200217w )
 
*** The End ***
 
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ ex -sc '1i|<фрагмент_вставки_значка>' -cx README.md



zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git add .travis.yml
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git add README.md
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git commit -m"added CI"
[main f8800d7] added CI
 2 files changed, 15 insertions(+)
 create mode 100644 .travis.yml


 
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git push -f origin main
Перечисление объектов: 2946, готово.
Подсчет объектов: 100% (2946/2946), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2248/2248), готово.
Запись объектов: 100% (2946/2946), 13.45 МиБ | 2.71 МиБ/с, готово.
Всего 2946 (изменений 527), повторно использовано 2940 (изменений 525), повторно использовано пакетов 0
remote: Resolving deltas: 100% (527/527), done.
To github.com:ZhenyaBukov/lab04.git
 + 700a4de...f8800d7 main -> main (forced update)
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git push origin master
error: src refspec master ничему не соответствует
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab04.git»
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$ git push origin main
Everything up-to-date
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab04$
 
