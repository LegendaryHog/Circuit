# Electical Circuits problem
My solution of electical circuits problem.

# How to clone?
```
git clone https://github.com/LegendaryHog/ElcCir.git
```

# How to build?
```
cmake -B build/ -DCMAKE_CXX_COMPILER=[your c++ compiler] -DCMAKE_BUILD_TYPE=Release -DEND_TO_END_TESTING=[True/False]

cmake --build build/ --target Circuit       # building Circuit library 
cmake --build build/ --target unit_tests    # building all unit tests
cmake --build build/ --target currents      # building problem solution
cmake --build build/ --target whole_project # building the unit_tests and currents
```

# How to run google tests?
```
ctest --test-dir build/
```

# Requirements for testing
If you want to use my scripts you need `numpy`, `math` and `termcolor` libraries, you can install these libraries by these commands:
```
pip install numpy
pip install math
pip install termcolor
```

# How to generate end to end tests?
In directory `end_to_end/`:
```
chmod "+x" test_gen.py
./test_gen.py number_of_nodes filename [--ans]
```
Script will generate test in `filename`. If you add flag `--ans` script will generate answer in `filename.ans`

# How to run end to end tests?
If you **don't** want to run end to end tests, you need run cmake configuration with `-DEND_TO_END_TESTING=False`
Else you need run withou that flag, or set it `True`. It will install my python lib for end to end tests from my github.

```
chmod "+x" test_cmp.py
./test_cmp.py build_dir test1 [test2, test3, ...]
```
Script compares output of program and answer. Scripit searches answet in `test{i}.ans`.

# Example of end to end testing from build to result.

```
cmake -B build/ -DCMAKE_CXX_COMPILER=clang++ -DCMAKE_BUILD_TYPE=Release

cmake --build build/ --target currents

cd end_to_end/

for i in $(seq 1 1 20); ./test_gen.py 20 test${i}.dat --ans

./test_cmp.py ../build/ *.dat
```
Result:

![image](.readme_src/runnernormal.png)

If error occurred:

![image](.readme_src/runnererr.png)

# How to run programm?
```
./build/task/currents
```
