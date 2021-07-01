Advanced Physical Design - OpenLANE Workshop
<details>
<summary>Contents</summary>

+ #### [Day 1 - Inception of Opensource EDA](https://github.com/Anitha-Juliette/Openlane#Day1-Inception_of_Opensource_EDA)
    +  ##### [Talk with Computers](https://github.com/Anitha-Juliette/Openlane#Talk_with_Computers)
    +  ##### [](https://github.com/Anitha-Juliette/Openlane#Invoking_Openlane)

</details>

### Day 1 - Inception of Opensource EDA
#### I. TALK WITH COMPUTERS
**_1. Chip Overview_**
* Chip on a board with its Peripherals
![](images/1.png)
* Package and Chip inside Package
![](images/2.png)
* Deep inside the Chip
![](images/3.png)
**_2. RISC_V Architecture_**
* C program -->converted to RISC-V assembly language program --> converted to machine language(binary) code --> run on RISC architecture(layout)
* Inbetween the RISC-V architecture specifications and Layout, RTL is sandwiched
* RTL implements the RISC-V architecture specifications and generates Layout
![](images/4.png)
**_3. Software Applications to Hardware_**
* Typical flow from software app to hardware
![](images/5.png)
* Flow illustrated with *Clock Timer* app
![](images/6.png)
* Abstract interface
![](images/7.png)
* Detailed flow
![](images/8.png)
#### II. SoC DESIGN AND OPENLANE
**_1. Components of Open Source digital ASIC design_**
* Components
   - RTL IP's
   - EDA Tools
   - PDK's(Process Design Kits)
![](images/9.png)
* In *Age of Gods*, design industry and Technology(Manufacturing) were closely related. 
* Lynn Convay and Carver Mead emphasized seperation of both design and technology industries; proposed *structured* design methodology based on Lambda rules; emerging of *Pure Play* and *efabless* companies
* Collection of files to model a fabrication process for EDA tools to design an IC
   - Process Design rules : DRC, LVS, PEX
   - Device Models
   - Digital Standard Libraries
   - I/O libraries



