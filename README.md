# Profiling-in-cpp  
cmake -DCMAKE_CXX_FLAGS=-pg -DCMAKE_EXE_LINKER_FLAGS=-pg -DCMAKE_SHARED_LINKER_FLAGS=-pg &lt;source-dir&gt;   
./&lt;executable&gt;    
gprof &lt;executable&gt; gmon.out &gt; output.txt    
pip install gprof2dot    
gprof2dot -o output.dot output.txt --node-label=self-time    
dot -Tpng -o output.png output.dot   


The png files are output of profile  for the same codes, for different dataset (data & simulation) . The data was taking more time to run the same number of events. When profiled, it shows all the events in the data are triggered, but in simulation its not. It was easy to find from the png file after profiling. It shows how much times each one is called and called and how much "time"  it took for each.
