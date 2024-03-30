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


**Memory usage check with valgrind**  
1)**Run the program with valgrind**  
valgrind --tool=massif ./&lt;executable&gt;   
The program will execute (slowly). Upon completion, no summary statistics are printed to Valgrind's commentary; all of Massif's profiling data is written to a file. By default, this file is called massif.out.<pid>, where <pid> is the process ID, although this filename can be changed with the --massif-out-file option.  
2)**Print the output file**  
ms_print massif.out.12345  
3)**Use massif-visualizer to see where is the issue** 
sudo add-apt-repository ppa:kubuntu-ppa/backports    
sudo apt-get update
sudo apt-get install massif-visualizer    
4)**Expand the snapshots and it will show which function and the line number it takes more memorey**   
Attached pics from massif-visualizer   

Here we found the TH3F histogram of dimension (500 X 500 X 500) taking 500MB. And we had three histograms.  
Due to this we converted all the TH3F histos to THnSparseD histos.    






