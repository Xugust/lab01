# labwork01
Лабораторная работа №1 по ТИМПу
1. Скачайте библиотеку boost с помощью утилиты wget. Адрес для скачивания https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
$ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz

Resolving sourceforge.net (sourceforge.net)... 172.64.150.145, 104.18.37.111, 2606:4700:4400::ac40:9691, ...
Connecting to sourceforge.net (sourceforge.net)|172.64.150.145|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/ [following]
--2024-09-12 01:28:48--  https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/
Reusing existing connection to sourceforge.net:443.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/download [following]
--2024-09-12 01:28:48--  https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/download
Reusing existing connection to sourceforge.net:443.
HTTP request sent, awaiting response... 302 Found
Location: https://downloads.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?ts=gAAAAABm4kPQOk8y8pKbnNafR_HvPmWczlHavOwz7G8YPOPEMHqUQAG5a4V5CRbtr2X2XZjqaGi2N0tUVTnmoRw2Oql0l2AdiQ%3D%3D&use_mirror=deac-fra&r= [following]
--2024-09-12 01:28:48--  https://downloads.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?ts=gAAAAABm4kPQOk8y8pKbnNafR_HvPmWczlHavOwz7G8YPOPEMHqUQAG5a4V5CRbtr2X2XZjqaGi2N0tUVTnmoRw2Oql0l2AdiQ%3D%3D&use_mirror=deac-fra&r=
Resolving downloads.sourceforge.net (downloads.sourceforge.net)... 204.68.111.105
Connecting to downloads.sourceforge.net (downloads.sourceforge.net)|204.68.111.105|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://deac-fra.dl.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?viasf=1 [following]
--2024-09-12 01:28:49--  https://deac-fra.dl.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?viasf=1
Resolving deac-fra.dl.sourceforge.net (deac-fra.dl.sourceforge.net)... 37.203.33.33
Connecting to deac-fra.dl.sourceforge.net (deac-fra.dl.sourceforge.net)|37.203.33.33|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 111710205 (107M) [application/x-gzip]
Saving to: ‘boost_1_69_0.tar.gz’

boost_1_69_0.tar. 100%[==========>] 106,53M   340KB/s    in 3m 7s   

2024-09-12 01:31:58 (583 KB/s) - ‘boost_1_69_0.tar.gz’ saved [111710205/111710205]

2. Разархивируйте скаченный файл в директорию ~/boost_1_69_0
$ tar -xf boost_1_69_0.tar.gz -C ~/

3. Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории.
$ find ~/boost_1_69_0 -maxdepth 1 -type f | wc -l
12

4. Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.
$ find ~/boost_1_69_0 -type f | wc -l
61191

5. Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).
$ find ~/boost_1_69_0 -type f -iname "*.hpp" | wc -l
14912
$ find ~/boost_1_69_0 -type f -iname "*.cpp" | wc -l
13774
$ find ~/boost_1_69_0 -type f ! -name "*.hpp" ! -name "*.cpp" | wc -l
32505

6. Найдите полный путь до файла any.hpp внутри библиотеки boost.
$ find ~/boost_1_69_0 -type f -name "any.hpp"

/root/boost_1_69_0/boost/fusion/algorithm/query/any.hpp
/root/boost_1_69_0/boost/fusion/algorithm/query/detail/any.hpp
/root/boost_1_69_0/boost/fusion/include/any.hpp
/root/boost_1_69_0/boost/any.hpp
/root/boost_1_69_0/boost/type_erasure/any.hpp
/root/boost_1_69_0/boost/proto/detail/any.hpp
/root/boost_1_69_0/boost/xpressive/detail/utility/any.hpp
/root/boost_1_69_0/boost/spirit/home/support/algorithm/any.hpp
/root/boost_1_69_0/boost/hana/any.hpp
/root/boost_1_69_0/boost/hana/fwd/any.hpp

7. Выведите в консоль все файлы, где упоминается последовательность boost::asio.
grep -r "boost::asio" ~/boost_1_69_0 > ~/boost_1_69_0_files_with_boost_asio.txt
[boost_1_69_0_files_with_boost_asio.txt](https://github.com/user-attachments/files/16986898/boost_1_69_0_files_with_boost_asio.txt)

8. Скомпилирутйе boost.
$ ./bootstrap.sh --prefix=boost_output

Building Boost.Build engine with toolset gcc... tools/build/src/engine/bin.linuxarm/b2
Unicode/ICU support for Boost.Regex?... not found.
Generating Boost.Build configuration in project-config.jam...

Bootstrapping is done. To build, run:

    ./b2
    
To adjust configuration, edit 'project-config.jam'.
Further information:

   - Command line help:
     ./b2 --help
     
   - Getting started guide: 
     http://www.boost.org/more/getting_started/unix-variants.html
     
   - Boost.Build documentation:
     http://www.boost.org/build/doc/html/index.html

$ ./bootstrap.sh --prefix=boost_output --with-icu=

Building Boost.Build engine with toolset gcc... tools/build/src/engine/bin.linuxarm/b2
Unicode/ICU support for Boost.Regex?... not found.
Backing up existing Boost.Build configuration in project-config.jam.1
Generating Boost.Build configuration in project-config.jam...

Bootstrapping is done. To build, run:

    ./b2
    
To adjust configuration, edit 'project-config.jam'.
Further information:

   - Command line help:
     ./b2 --help
     
   - Getting started guide: 
     http://www.boost.org/more/getting_started/unix-variants.html
     
   - Boost.Build documentation:
     http://www.boost.org/build/doc/html/index.html

$ ./b2 install >> logs.txt
[logs.txt](https://github.com/user-attachments/files/16986775/logs.txt)

9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.
$ mv boost_output/lib/*.a ~/boost-libs

10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
$ du -sh ~/boost-libs/*

4,0K	/root/boost-libs/libboost_atomic.a
276K	/root/boost-libs/libboost_chrono.a
148K	/root/boost-libs/libboost_container.a
24K	/root/boost-libs/libboost_context.a
384K	/root/boost-libs/libboost_contract.a
168K	/root/boost-libs/libboost_date_time.a
4,0K	/root/boost-libs/libboost_exception.a
252K	/root/boost-libs/libboost_fiber.a
456K	/root/boost-libs/libboost_filesystem.a
928K	/root/boost-libs/libboost_graph.a
184K	/root/boost-libs/libboost_iostreams.a
2,2M	/root/boost-libs/libboost_locale.a
840K	/root/boost-libs/libboost_math_c99.a
576K	/root/boost-libs/libboost_math_c99f.a
772K	/root/boost-libs/libboost_math_c99l.a
3,8M	/root/boost-libs/libboost_math_tr1.a
3,0M	/root/boost-libs/libboost_math_tr1f.a
3,5M	/root/boost-libs/libboost_math_tr1l.a
236K	/root/boost-libs/libboost_prg_exec_monitor.a
1,7M	/root/boost-libs/libboost_program_options.a
96K	/root/boost-libs/libboost_random.a
2,8M	/root/boost-libs/libboost_regex.a
1,3M	/root/boost-libs/libboost_serialization.a
24K	/root/boost-libs/libboost_stacktrace_addr2line.a
24K	/root/boost-libs/libboost_stacktrace_backtrace.a
16K	/root/boost-libs/libboost_stacktrace_basic.a
4,0K	/root/boost-libs/libboost_stacktrace_noop.a
4,0K	/root/boost-libs/libboost_system.a
2,5M	/root/boost-libs/libboost_test_exec_monitor.a
60K	/root/boost-libs/libboost_timer.a
2,4M	/root/boost-libs/libboost_unit_test_framework.a
4,8M	/root/boost-libs/libboost_wave.a
844K	/root/boost-libs/libboost_wserialization.a

11. Найдите топ10 самых "тяжёлых".
$ find ~/boost-libs/ -type f -exec du -Sh {} + | sort -rh |head -n 10

4,8M	/root/boost-libs/libboost_wave.a
3,8M	/root/boost-libs/libboost_math_tr1.a
3,5M	/root/boost-libs/libboost_math_tr1l.a
3,0M	/root/boost-libs/libboost_math_tr1f.a
2,8M	/root/boost-libs/libboost_regex.a
2,5M	/root/boost-libs/libboost_test_exec_monitor.a
2,4M	/root/boost-libs/libboost_unit_test_framework.a
2,2M	/root/boost-libs/libboost_locale.a
1,7M	/root/boost-libs/libboost_program_options.a
1,3M	/root/boost-libs/libboost_serialization.a
