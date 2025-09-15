1) A program Z-decays.cc simulating decays of Z bosons at rest either into all possible states or into bbbar. For bbbar, it may optionally treat B mesons (B^+, B^0, Bs, and their antiparticles; may be adjusted) stable. If all particles are unstable, the program writes the file "Z-decays/z-decay-products.txt", with each row representing decay products per event: PDF-identifier p_x-GeV p_y p_z E, x-mm, y, z, r. If B mesons are selected stable, it additionally writes the file "z-decay-products-B.txt".

Compile (replace /home/name/Downloads/pythia-mixing-dev/ with your pythia8 installation directory), should work independently of the folder the programs are stored:
```shell
g++ -O2 -std=c++17 -fopenmp Z-decays.cc -o myprog -I/home/name/Downloads/pythia-mixing-dev/include -L/home/name/Downloads/pythia-mixing-dev/lib -Wl,-rpath,/home/name/Downloads/pythia-mixing-dev/lib -lpythia8 -ldl -lboost_filesystem -lboost_system
```
Launch:
```shell
 ./myprog -n 200 -ifbbar true -ifBstable true
```
where n is the number of events to simulate, ifbbar is whether consider decay Z -> bbbar only (true) or all (false), and ifBstable (needed if the previous argument is true) is whether to treat the B mesons as stable particles (true) or not (false) 

2) A program Z-decays-post.cc simulating the decays of all B mesons from "z-decay-products-B.txt" except one (to be decayed into BSM externally), merging the B decay products with the non-B products from "z-decay-products.txt" + putting them into the file "Z-decays/z-decay-products-merged.txt", and finally storing the remaining B into file "Z-decays/B-data.txt".
Compile:
```shell
g++ -O2 -std=c++17 -fopenmp Z-decays-post.cc -o myprog2 -I/home/name/Downloads/pythia-mixing-dev/include -L/home/name/Downloads/pythia-mixing-dev/lib -Wl,-rpath,/home/name/Downloads/pythia-mixing-dev/lib -lpythia8 -ldl -lboost_filesystem -lboost_system
```
Launch:
```shell
./myprog2
```
3) A program Z-decay-check.cc  (in the folder "Z-decays") testing the 4-momentum conservation in the events.
Compile:
```shell
g++ -O2 -std=c++17 Z-decay-check.cc -o zcheck
```
Launch:
```shell
./zcheck
```
Proper output:
```undefined
[CHECK] Events: 20000
        momentum fails: 0 (|px,py,pz| < 0.001 GeV)
        energy   fails: 0 (|E - 91.1876| < 0.005 GeV)
[OK] All events within tolerances.
```
4) Bonus: a python program distributions.py (in the folder "Z-decays") making the energy histograms of various products: e/mu, pi-charged/K-charged/p, gamma/K_L/n, kept B meson. Produces the plot energy_categories.png.
Launch:
```shell
python3 distributions.py
```