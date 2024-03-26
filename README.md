# Profiling-in-cpp  

**Prerequisites** CMake "gprof" "gprof2dot" "graphviz(for dot command)"  

1)**Compile with profiling flags "pg"**  
cmake -DCMAKE_CXX_FLAGS=-pg -DCMAKE_EXE_LINKER_FLAGS=-pg -DCMAKE_SHARED_LINKER_FLAGS=-pg &lt;source-dir&gt;   
2)**Run the executable like normal**  
./&lt;executable&gt;    
3)**Generate Profile Data using GNU gprof**   
gprof &lt;executable&gt; gmon.out &gt; output.txt    
4)**Install gprof2dot with pip**    
pip install gprof2dot    
5)**Convert to dot file**  
gprof2dot -o output.dot output.txt --node-label=self-time    
6)**Convert to png file**  
dot -Tpng -o output.png output.dot   


The png files are output of profile  for the same codes, for different dataset (data & simulation) . The data was taking more time to run the same number of events. When profiled, it shows all the events in the data are triggered, but in simulation its not. It was easy to find from the png file after profiling. It shows how much times each one is called and called and how much "time"  it took for each.
