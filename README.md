# Profiling-in-cpp
cmake -DCMAKE_CXX_FLAGS=-pg -DCMAKE_EXE_LINKER_FLAGS=-pg -DCMAKE_SHARED_LINKER_FLAGS=-pg <source-dir>
./<executable>
gprof <executable> gmon.out > output.txt
pip install gprof2dot
gprof2dot -o output.dot output.txt --node-label=self-time
dot -Tpng -o output.png output.dot
