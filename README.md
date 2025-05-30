zhenya@zhenya-VirtualBox:~$ export GITHUB_TOKEN=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
zhenya@zhenya-VirtualBox:~$ export GITHUB_USERNAME=ZhenyaBukov
zhenya@zhenya-VirtualBox:~$ export PACKAGE_MANAGER=apt
zhenya@zhenya-VirtualBox:~$ GPG_PACKAGE_NAME=gpg
zhenya@zhenya-VirtualBox:~$ $PACKAGE_MANAGER install xclip
E: Не удалось открыть файл блокировки /var/lib/dpkg/lock-frontend - open (13: Отказано в доступе)
E: Невозможно получить блокировку внешнего интерфейса dpkg (/var/lib/dpkg/lock-frontend); у вас есть права суперпользователя?
zhenya@zhenya-VirtualBox:~$ sudo apt install xclip
[sudo] пароль для zhenya: 
Чтение списков пакетов… Готово
Построение дерева зависимостей… Готово
Чтение информации о состоянии… Готово         
Следующие НОВЫЕ пакеты будут установлены:
  xclip
Обновлено 0 пакетов, установлено 1 новых пакетов, для удаления отмечено 0 пакетов, и 112 пакетов не обновлено.
Необходимо скачать 17,6 kB архивов.
После данной операции объём занятого дискового пространства возрастёт на 54,3 kB.
Пол:1 http://ru.archive.ubuntu.com/ubuntu noble/universe amd64 xclip amd64 0.13-3 [17,6 kB]
Получено 17,6 kB за 0с (72,0 kB/s) 
Выбор ранее не выбранного пакета xclip.
(Чтение базы данных … на данный момент установлено 210953 файла и каталога.)
Подготовка к распаковке …/xclip_0.13-3_amd64.deb …
Распаковывается xclip (0.13-3) …
Настраивается пакет xclip (0.13-3) …
Обрабатываются триггеры для man-db (2.12.0-4build2) …
zhenya@zhenya-VirtualBox:~$ $PACKAGE_MANAGER install xclip
E: Не удалось открыть файл блокировки /var/lib/dpkg/lock-frontend - open (13: Отказано в доступе)
E: Невозможно получить блокировку внешнего интерфейса dpkg (/var/lib/dpkg/lock-frontend); у вас есть права суперпользователя?
zhenya@zhenya-VirtualBox:~$ alias gsed=sed
zhenya@zhenya-VirtualBox:~$ alias pbcopy='xclip -selection clipboard'
zhenya@zhenya-VirtualBox:~$ alias pbpaste='xclip -selection clipboard -o'
zhenya@zhenya-VirtualBox:~$ cd ${GITHUB_USERNAME}/workspace
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ pushd .
~/ZhenyaBukov/workspace ~/ZhenyaBukov/workspace
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ source scripts/activate
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ go get github.com/aktau/github-release
Команда «go» не найдена, но может быть установлена с помощью:
sudo snap install go         # version 1.24.2, or
sudo apt  install golang-go  # version 2:1.21~2
sudo apt  install gccgo-go   # version 2:1.21~2
См. 'snap info go', чтобы посмотреть дополнительные версии.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ sudo apt update
Сущ:1 http://ru.archive.ubuntu.com/ubuntu noble InRelease
Пол:2 http://ru.archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]
Пол:3 http://security.ubuntu.com/ubuntu noble-security InRelease [126 kB]
Пол:4 http://ru.archive.ubuntu.com/ubuntu noble-backports InRelease [126 kB]
Чтение списков пакетов… Готово                            
E: Файл Release для http://ru.archive.ubuntu.com/ubuntu/dists/noble-updates/InRelease пока не действителен (недостоверный ещё 3ч 20мин 43с). Обновление этого репозитория производиться не будет.
E: Файл Release для http://ru.archive.ubuntu.com/ubuntu/dists/noble-backports/InRelease пока не действителен (недостоверный ещё 27мин 52с). Обновление этого репозитория производиться не будет.
E: Файл Release для http://security.ubuntu.com/ubuntu/dists/noble-security/InRelease пока не действителен (недостоверный ещё 25мин 57с). Обновление этого репозитория производиться не будет.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ sudo snap install go
ошибка: This revision of snap "go" was published
              using classic confinement and thus may
              perform arbitrary system changes outside of
              the security sandbox that snaps are usually
              confined to, which may put your system at
              risk.

              If you understand and want to proceed repeat
              the command including --classic.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ git clone
fatal: Вы должны указать репозиторий для клонирования.

использование: git clone [<опции>] [--] <репозиторий> [<каталог>]

    -v, --[no-]verbose    быть многословнее
    -q, --[no-]quiet      тихий режим
    --[no-]progress       принудительно выводить прогресс
    --[no-]reject-shallow don't clone shallow repository
    -n, --no-checkout     не переключать рабочую копию на HEAD
    --checkout            opposite of --no-checkout
    --[no-]bare           создать голый репозиторий
    --[no-]mirror         создать зеркало репозитория (включает в себя и параметр bare)
    -l, --[no-]local      для клонирования из локального репозитория
    --no-hardlinks        не использовать жесткие ссылки, всегда копировать файлы
    --hardlinks           opposite of --no-hardlinks
    -s, --[no-]shared     настроить как общедоступный репозиторий
    --[no-]recurse-submodules[=<спецификатор-пути>]
                          инициализировать подмодули в клоне
    --[no-]recursive ...  alias of --recurse-submodules
    -j, --[no-]jobs <n>   количество подмодулей, которые будут клонированы парралельно
    --[no-]template <каталог-шаблонов>
                          каталог, шаблоны из которого будут использованы
    --[no-]reference <репозиторий>
                          ссылаемый репозиторий
    --[no-]reference-if-able <репозиторий>
                          ссылаемый репозиторий
    --[no-]dissociate     используйте --reference только при клонировании
    -o, --[no-]origin <имя>
                          использовать <имя> вместо «origin» для отслеживания вышестоящего репозитория
    -b, --[no-]branch <ветка>
                          переключиться на <ветку>, вместо HEAD внешнего репозитория
    -u, --[no-]upload-pack <путь>
                          путь к git-upload-pack на внешнем репозитории
    --[no-]depth <глубина>
                          сделать частичный клон указанной глубины
    --[no-]shallow-since <время>
                          сделать частичный клон до определенного времени
    --[no-]shallow-exclude <редакция>
                          углубить историю частичного клона исключая редакцию
    --[no-]single-branch  клонировать только одну ветку, HEAD или --branch
    --no-tags             не клонировать метки, а также настроить, чтобы не клонировались и в дальнейшем
    --tags                opposite of --no-tags
    --[no-]shallow-submodules
                          все склонированные подмодули будут частичными клонами
    --[no-]separate-git-dir <каталог-git>
                          разместить каталог git отдельно от рабочей копии
    -c, --[no-]config <ключ=значение>
                          установить параметры внутри нового репозитория
    --[no-]server-option <зависит-от-сервера>
                          передаваемые опции
    -4, --ipv4            использовать только IPv4 адреса
    -6, --ipv6            использовать только IPv6 адреса
    --[no-]filter <аргументы>
                          фильтрация объектов
    --[no-]also-filter-submodules
                          apply partial clone filters to submodules
    --[no-]remote-submodules
                          any cloned submodules will use their remote-tracking branch
    --[no-]sparse         initialize sparse-checkout file to include only files at root
    --[no-]bundle-uri <uri>
                          a URI for downloading bundles before fetching from origin remote

zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ git clone git@github.com:ZhenyaBukov/lab08.git projects/lab09
Клонирование в «projects/lab09»...
remote: Enumerating objects: 2977, done.
remote: Counting objects: 100% (2977/2977), done.
remote: Compressing objects: 100% (2264/2264), done.
Получение объектов:  34% (1013/2977), 10.33 МиБ | 2.49 МиБ/Получение объектов:  35% (1042/2977), 10.33 МиБ | 2.49 МиБ/Получение объектов:  36% (1072/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  37% (1102/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  38% (1132/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  39% (1162/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  40% (1191/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  41% (1221/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  42% (1251/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  43% (1281/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  44% (1310/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  45% (1340/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  46% (1370/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  47% (1400/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  48% (1429/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  49% (1459/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  50% (1489/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  51% (1519/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  52% (1549/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  53% (1578/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  54% (1608/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  55% (1638/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  56% (1668/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  57% (1697/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  58% (1727/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  59% (1757/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  60% (1787/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  61% (1816/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  62% (1846/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  63% (1876/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  64% (1906/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  65% (1936/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  66% (1965/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  67% (1995/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  68% (2025/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  69% (2055/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  70% (2084/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  71% (2114/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  72% (2144/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  73% (2174/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  74% (2203/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  75% (2233/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  76% (2263/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  77% (2293/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  78% (2323/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  79% (2352/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  80% (2382/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  81% (2412/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  82% (2442/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  83% (2471/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  84% (2501/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  85% (2531/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  86% (2561/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  87% (2590/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  88% (2620/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  88% (2621/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  89% (2650/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  90% (2680/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  91% (2710/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  92% (2739/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  93% (2769/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  94% (2799/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  95% (2829/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  96% (2858/2977), 12.05 МиБ | 2.56 МиБ/Получение объектов:  97% (2888/2977), 13.43 МиБ | 2.76 МиБ/remote: Total 2977 (delta 541), reused 2973 (delta 539), pack-reused 0 (from 0)
Получение объектов:  98% (2918/2977), 13.43 МиБ | 2.76 МиБ/Получение объектов:  99% (2948/2977), 13.43 МиБ | 2.76 МиБ/Получение объектов: 100% (2977/2977), 13.43 МиБ | 2.76 МиБ/Получение объектов: 100% (2977/2977), 13.48 МиБ | 2.58 МиБ/с, готово.
Определение изменений: 100% (541/541), готово.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace$ cd projects/lab09
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ git remote remove origin
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ git remote add origin git@github.com:ZhenyaBukov/lab09.git
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ gsed -i 's/lab08/lab09/g' README.md
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ $PACKAGE_MANAGER install ${GPG_PACKAGE_NAME}
E: Не удалось открыть файл блокировки /var/lib/dpkg/lock-frontend - open (13: Отказано в доступе)
E: Невозможно получить блокировку внешнего интерфейса dpkg (/var/lib/dpkg/lock-frontend); у вас есть права суперпользователя?
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ gpg --list-secret-keys --keyid-format LONG
gpg: создан каталог '/home/zhenya/.gnupg'
gpg: создан щит с ключами '/home/zhenya/.gnupg/pubring.kbx'
gpg: /home/zhenya/.gnupg/trustdb.gpg: создана таблица доверия
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ gpg --full-generate-key
gpg (GnuPG) 2.4.4; Copyright (C) 2024 g10 Code GmbH
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Выберите тип ключа:
   (1) RSA и RSA
   (2) DSA и Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
   (9) ECC (подписание и шифрование) *по умолчанию*
  (10) ECC (только для подписи)
  (14) Существующий ключ с карты 
Ваш выбор? gpg --list-secret-keys --keyid-format LONG
Неправильный выбор.
Ваш выбор? 1
длина ключей RSA может быть от 1024 до 4096.
Какой размер ключа Вам необходим? (3072) 14y
размер ключей RSA должен быть в пределах 1024-4096
Какой размер ключа Вам необходим? (3072) 1024
Запрошенный размер ключа - 1024 бит
Выберите срок действия ключа.
         0 = не ограничен
      <n>  = срок действия ключа - n дней
      <n>w = срок действия ключа - n недель
      <n>m = срок действия ключа - n месяцев
      <n>y = срок действия ключа - n лет
Срок действия ключа? (0) 0
Срок действия ключа не ограничен
Все верно? (y/N) y

GnuPG должен составить идентификатор пользователя для идентификации ключа.

Ваше полное имя: Zhenya
Адрес электронной почты: zhenya.bukov.06@mail.ru
Примечание: 123
Вы выбрали следующий идентификатор пользователя:
    "Zhenya (123) <zhenya.bukov.06@mail.ru>"

Сменить (N)Имя, (C)Примечание, (E)Адрес; (O)Принять/(Q)Выход? N
Ваше полное имя: ZhenyaBukov
Вы выбрали следующий идентификатор пользователя:
    "ZhenyaBukov (123) <zhenya.bukov.06@mail.ru>"

Сменить (N)Имя, (C)Примечание, (E)Адрес; (O)Принять/(Q)Выход? o
Необходимо получить много случайных чисел. Желательно, чтобы Вы
в процессе генерации выполняли какие-то другие действия (печать
на клавиатуре, движения мыши, обращения к дискам); это даст генератору
случайных чисел больше возможностей получить достаточное количество энтропии.
Необходимо получить много случайных чисел. Желательно, чтобы Вы
в процессе генерации выполняли какие-то другие действия (печать
на клавиатуре, движения мыши, обращения к дискам); это даст генератору
случайных чисел больше возможностей получить достаточное количество энтропии.
gpg: создан каталог '/home/zhenya/.gnupg/openpgp-revocs.d'
gpg: сертификат отзыва записан в '/home/zhenya/.gnupg/openpgp-revocs.d/8D94D39DE4FEE1BB6A828337305EBF1EE545B369.rev'.
открытый и секретный ключи созданы и подписаны.

pub   rsa1024 2025-05-30 [SC]
      8D94D39DE4FEE1BB6A828337305EBF1EE545B369
uid                      ZhenyaBukov (123) <zhenya.bukov.06@mail.ru>
sub   rsa1024 2025-05-30 [E]

zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ gpg -K ${GITHUB_USERNAME}
gpg: проверка таблицы доверия
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: глубина: 0  достоверных:   1  подписанных:   0  доверие: 0-, 0q, 0n, 0m, 0f, 1u
sec   rsa1024 2025-05-30 [SC]
      8D94D39DE4FEE1BB6A828337305EBF1EE545B369
uid         [  абсолютно ] ZhenyaBukov (123) <zhenya.bukov.06@mail.ru>
ssb   rsa1024 2025-05-30 [E]

zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ GPG_KEY_ID=$(gpg --list-secret-keys --keyid-format LONG | grep ssb | tail -1 | awk '{print $2}' | awk -F'/' '{print $2}')
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ GPG_SEC_KEY_ID=$(gpg --list-secret-keys --keyid-format LONG | grep sec | tail -1 | awk '{print $2}' | awk -F'/' '{print $2}')
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ gpg --armor --export ${GPG_KEY_ID} | pbcopy
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ pbpaste
pbpastezhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/open https://github.com/settings/keysgs/keys
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ Gtk-Message: 17:56:20.397: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.

zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ git config user.signingkey ${GPG_SEC_KEY_ID}
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ git config gpg.program gpg
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ test -r ~/.bash_profile && echo 'export GPG_TTY=$(tty)' >> ~/.bash_profile
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ echo 'export GPG_TTY=$(tty)' >> ~/.profile
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ cmake -H. -B_build -DCPACK_GENERATOR="TGZ"
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
-- Build files have been written to: /home/zhenya/ZhenyaBukov/workspace/projects/lab09/_build
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ cmake --build _build --target package
[ 50%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
In file included from /home/zhenya/ZhenyaBukov/workspace/projects/lab09/sources/print.cpp:2:
/home/zhenya/ZhenyaBukov/workspace/projects/lab09/include/print.hpp:6:6: error: default argument given for parameter 2 of ‘void print(const std::string&, std::ostream&)’ [-fpermissive]
    6 | void print(const std::string& text, std::ostream& out = std::cout);
      |      ^~~~~
In file included from /home/zhenya/ZhenyaBukov/workspace/projects/lab09/sources/print.cpp:1:
/home/zhenya/ZhenyaBukov/workspace/projects/lab09/include/print.hpp:6:6: note: previous specification in ‘void print(const std::string&, std::ostream&)’ here
    6 | void print(const std::string& text, std::ostream& out = std::cout);
      |      ^~~~~
gmake[2]: *** [CMakeFiles/print.dir/build.make:76: CMakeFiles/print.dir/sources/print.cpp.o] Ошибка 1
gmake[1]: *** [CMakeFiles/Makefile2:83: CMakeFiles/print.dir/all] Ошибка 2
gmake: *** [Makefile:156: all] Ошибка 2
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ git tag -s v0.1.0.0
fatal: нет описания метки?
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ git tag -v v0.1.0.0
error: метка  «v0.1.0.0» не найдена.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ git show v0.1.0.0
fatal: неоднозначный аргумент «v0.1.0.0»: неизвестная редакция или не путь в рабочем каталоге.
Используйте «--» для отделения путей от редакций, вот так:
«git <команда> [<редакция>...] -- [<файл>...]»
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ git push origin main --tags
To github.com:ZhenyaBukov/lab09.git
 ! [rejected]        main -> main (fetch first)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab09.git»
подсказка: Updates were rejected because the remote contains work that you do not
подсказка: have locally. This is usually caused by another repository pushing to
подсказка: the same ref. If you want to integrate the remote changes, use
подсказка: 'git pull' before pushing again.
подсказка: See the 'Note about fast-forwards' in 'git push --help' for details.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ git push -f origin main
Перечисление объектов: 2977, готово.
Подсчет объектов: 100% (2977/2977), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2262/2262), готово.
Запись объектов: 100% (2977/2977), 13.48 МиБ | 3.59 МиБ/с, готово.
Всего 2977 (изменений 541), повторно использовано 2977 (изменений 541), повторно использовано пакетов 0
remote: Resolving deltas: 100% (541/541), done.
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
remote:        https://github.com/ZhenyaBukov/lab09/security/secret-scanning/unblock-secret/2xpWCcZHmeOjwc3tRC5DeZZZMeJ
remote:     
remote:     
remote:       —— GitHub Personal Access Token ——————————————————————
remote:        locations:
remote:          - commit: c71fea93dbceb60601f9d9cc6175713b8e8fa5ba
remote:            path: README.md:3
remote:     
remote:        (?) To push, remove secret from commit(s) or follow this URL to allow the secret.
remote:        https://github.com/ZhenyaBukov/lab09/security/secret-scanning/unblock-secret/2xpWCe4BIiaMfxgg9oakqhj1HIN
remote:     
remote: 
remote: 
To github.com:ZhenyaBukov/lab09.git
 ! [remote rejected] main -> main (push declined due to repository rule violations)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab09.git»
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ git push -f origin main
Перечисление объектов: 2977, готово.
Подсчет объектов: 100% (2977/2977), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2262/2262), готово.
Запись объектов: 100% (2977/2977), 13.48 МиБ | 1.74 МиБ/с, готово.
Всего 2977 (изменений 541), повторно использовано 2977 (изменений 541), повторно использовано пакетов 0
remote: Resolving deltas: 100% (541/541), done.
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
remote:        https://github.com/ZhenyaBukov/lab09/security/secret-scanning/unblock-secret/2xpWCcZHmeOjwc3tRC5DeZZZMeJ
remote:     
remote: 
remote: 
To github.com:ZhenyaBukov/lab09.git
 ! [remote rejected] main -> main (push declined due to repository rule violations)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab09.git»
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ git push -f origin main
Перечисление объектов: 2977, готово.
Подсчет объектов: 100% (2977/2977), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2262/2262), готово.
Запись объектов: 100% (2977/2977), 13.48 МиБ | 3.75 МиБ/с, готово.
Всего 2977 (изменений 541), повторно использовано 2977 (изменений 541), повторно использовано пакетов 0
remote: Resolving deltas: 100% (541/541), done.
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
remote:        https://github.com/ZhenyaBukov/lab09/security/secret-scanning/unblock-secret/2xpWCcZHmeOjwc3tRC5DeZZZMeJ
remote:     
remote: 
remote: 
To github.com:ZhenyaBukov/lab09.git
 ! [remote rejected] main -> main (push declined due to repository rule violations)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab09.git»
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ git push origin main
To github.com:ZhenyaBukov/lab09.git
 ! [rejected]        main -> main (fetch first)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab09.git»
подсказка: Updates were rejected because the remote contains work that you do not
подсказка: have locally. This is usually caused by another repository pushing to
подсказка: the same ref. If you want to integrate the remote changes, use
подсказка: 'git pull' before pushing again.
подсказка: See the 'Note about fast-forwards' in 'git push --help' for details.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ git push -f origin main
Перечисление объектов: 2977, готово.
Подсчет объектов: 100% (2977/2977), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2262/2262), готово.
Запись объектов: 100% (2977/2977), 13.48 МиБ | 1.55 МиБ/с, готово.
Всего 2977 (изменений 541), повторно использовано 2977 (изменений 541), повторно использовано пакетов 0
remote: Resolving deltas: 100% (541/541), done.
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
remote:        https://github.com/ZhenyaBukov/lab09/security/secret-scanning/unblock-secret/2xpWCcZHmeOjwc3tRC5DeZZZMeJ
remote:     
remote: 
remote: 
To github.com:ZhenyaBukov/lab09.git
 ! [remote rejected] main -> main (push declined due to repository rule violations)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab09.git»
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ git push origin main
To github.com:ZhenyaBukov/lab09.git
 ! [rejected]        main -> main (fetch first)
error: не удалось отправить некоторые ссылки в «github.com:ZhenyaBukov/lab09.git»
подсказка: Updates were rejected because the remote contains work that you do not
подсказка: have locally. This is usually caused by another repository pushing to
подсказка: the same ref. If you want to integrate the remote changes, use
подсказка: 'git pull' before pushing again.
подсказка: See the 'Note about fast-forwards' in 'git push --help' for details.
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ git push -f origin main
Перечисление объектов: 2977, готово.
Подсчет объектов: 100% (2977/2977), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2262/2262), готово.
Запись объектов: 100% (2977/2977), 13.48 МиБ | 1.70 МиБ/с, готово.
Всего 2977 (изменений 541), повторно использовано 2977 (изменений 541), повторно использовано пакетов 0
remote: Resolving deltas: 100% (541/541), done.
To github.com:ZhenyaBukov/lab09.git
 + cfd77b7...92a2925 main -> main (forced update)
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ github-release --version
github-release: команда не найдена
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ github-release info -u ${GITHUB_USERNAME} -r lab09
github-release: команда не найдена
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ github-release release \
> --user ${GITHUB_USERNAME} \
    --repo lab09 \
    --tag v0.1.0.0 \
    --name "libprint" \
    --description "my first release"
github-release: команда не найдена
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ export PACKAGE_OS=`uname -s` PACKAGE_ARCH=`uname -m` zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ export PACKAGE_FILENAME=print-${PACKAGE_OS}-${PACKAGE_ARCH}.tar.gz
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ github-release upload \
>  --user ${GITHUB_USERNAME} \
    --repo lab09 \
    --tag v0.1.0.0 \
    --name "${PACKAGE_FILENAME}" \
    --file _build/*.tar.gz
github-release: команда не найдена
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ github-release info -u ${GITHUB_USERNAME} -r lab09
github-release: команда не найдена
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ wget https://github.com/${GITHUB_USERNAME}/lab09/releases/download/v0.1.0.0/${PACKAGE_FILENAME}
--2025-05-30 18:03:20--  https://github.com/ZhenyaBukov/lab09/releases/download/v0.1.0.0/print-Linux-x86_64.tar.gz
Распознаётся github.com (github.com)… 140.82.121.4
Подключение к github.com (github.com)|140.82.121.4|:443... соединение установлено.
HTTP-запрос отправлен. Ожидание ответа… 404 Not Found
2025-05-30 18:03:20 ОШИБКА 404: Not Found.

zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ tar -ztf ${PACKAGE_FILENAME}
tar (child): print-Linux-x86_64.tar.gz: Функция open завершилась с ошибкой: Нет такого файла или каталога
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
zhenya@zhenya-VirtualBox:~/ZhenyaBukov/workspace/projects/lab09$ 

