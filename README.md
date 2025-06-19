Following are commands of each Question:

Q1
run hello world
./build/X86/gem5.opt configs/example/se.py \
-c tests/test-progs/hello/bin/x86/linux/hello \
--cpu-type=TimingSimpleCPU --caches --l2cache --l3cache --mem-type=NVMainMemory \
--nvmain-config=../NVmain/Config/PCM_ISSCC_2012_4GB.config

Q2

compile:
scons EXTRAS=../NVmain build/X86/gem5.opt

execute:
./build/X86/gem5.opt configs/example/se.py -c tests/test-progs/hello/bin/x86/linux/hello --cpu-type=TimingSimpleCPU --caches --l2cache --l3cache --mem-type=NVMainMemory --nvmain-config=../NVmain/Config/PCM_ISSCC_2012_4GB.config


Q3

gcc --static quicksort.c -o quicksort

./build/X86/gem5.opt configs/example/se.py \
-c ./quicksort --cpu-type=TimingSimpleCPU \
--caches --l1i_size=32kB --l1d_size=32kB --l2cache --l2_size=128kB \
--l3cache --l3_size=1MB --l3_assoc=16384 --mem-type=NVMainMemory \
--nvmain-config=../NVmain/Config/PCM_ISSCC_2012_4GB.config > cmdlog_full-way.txt

./build/X86/gem5.opt configs/example/se.py \
-c ./quicksort --cpu-type=TimingSimpleCPU \
--caches --l1i_size=32kB --l1d_size=32kB --l2cache --l2_size=128kB \
--l3cache --l3_size=1MB --l3_assoc=2 --mem-type=NVMainMemory \
--nvmain-config=../NVmain/Config/PCM_ISSCC_2012_4GB.config > cmdlog_2-way.txt

Q4

compile:
scons EXTRAS=../NVmain build/X86/gem5.opt

executes:
./build/X86/gem5.opt configs/example/se.py \
-c ./quicksort --cpu-type=TimingSimpleCPU \
--caches --l1i_size=32kB --l1d_size=32kB --l2cache --l2_size=128kB \
--l3cache --l3_size=1MB --l3_assoc=2 --mem-type=NVMainMemory \
--nvmain-config=../NVmain/Config/PCM_ISSCC_2012_4GB.config > cmdlog_FB.txt

./build/X86/gem5.opt configs/example/se.py \
-c ./quicksort --cpu-type=TimingSimpleCPU \
--caches --l1i_size=32kB --l1d_size=32kB --l2cache --l2_size=128kB \
--l3cache --l3_size=1MB --l3_assoc=2 --mem-type=NVMainMemory \
--nvmain-config=../NVmain/Config/PCM_ISSCC_2012_4GB.config > cmdlog_LRU.txt

Q5

編譯multiply
gcc --static multiply.c -o multiply

執行writeback
./build/X86/gem5.opt configs/example/se.py \
-c ./multiply --cpu-type=TimingSimpleCPU \
--caches --l1i_size=32kB --l1d_size=32kB --l2cache --l2_size=128kB \
--l3cache --l3_size=1MB --l3_assoc=4 --mem-type=NVMainMemory \
--nvmain-config=../NVmain/Config/PCM_ISSCC_2012_4GB.config > cmdlog_WriteBack.txt

執行writethrough
./build/X86/gem5.opt configs/example/se.py \
-c ./multiply --cpu-type=TimingSimpleCPU \
--caches --l1i_size=32kB --l1d_size=32kB --l2cache --l2_size=128kB \
--l3cache --l3_size=1MB --l3_assoc=4 --mem-type=NVMainMemory \
--nvmain-config=../NVmain/Config/PCM_ISSCC_2012_4GB.config > cmdlog_WriteThrough.txt
