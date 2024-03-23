# Profiling-in-cpp  
cmake -DCMAKE_CXX_FLAGS=-pg -DCMAKE_EXE_LINKER_FLAGS=-pg -DCMAKE_SHARED_LINKER_FLAGS=-pg &lt;source-dir&gt;   
#./&lt;executable&gt;    
gprof &lt;executable&gt; gmon.out &gt; output.txt    
pip install gprof2dot    
gprof2dot -o output.dot output.txt --node-label=self-time    
dot -Tpng -o output.png output.dot   
