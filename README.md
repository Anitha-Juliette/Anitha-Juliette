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
* First ever Open Source PDK 
![](images/10.png)
* Collection of files to model a fabrication process for EDA tools to design an IC
   - Process Design rules : DRC, LVS, PEX
   - Device Models
   - Digital Standard Libraries
   - I/O libraries
 **_3. ASIC Flow Objective : RTL to GDSII (Automated PnR and/or Physical Implementation)_**
 * Simplified RTL2GDSII design flow
 ![](images/11.png)
 * Step 1 : Synthesis
 ![](images/12.png)
 * Step2 : Floor and Power planning
    - Foor Planning
      - Chip Floor planning
      - Macro Floor planning
 ![](images/13.png)
     - Power planning : Uses upper metal layers rather than lower metal layers
 ![](images/14.png)
 * Step 3 : Placement - Macros will place cells(gate level netlist) onto virtual rows. The cells should be placed close so as to ensure proer routing
 ![](images/15.png)
   - Global placements : 
   - Detailed placements :
 ![](images/16.png)
* Step 4 : Clock Tree Synthesis
![](images/17.png)
* Step 5 : Routing
![](images/18.png)
  - Metal Tracks form Routing grid that is large
  - Divide and Conquer approach
    - Global routing : generates routing guides(Fine grain grids)
    - Deatiled routing : uses the routing guides to implement the actual wiring(Coarse grain Grids)
 * Step 6 : Sign off/Layout
 ![](images/19.png)
 **_4. Open Source ASIC Flow with Openlane and Strive Chipsets_**
 * Openlane : Open Source Flow for a *True* open source Tapeout experiment
 * efabless has a family of Soc's calles as Strive( Open PDK, Open EDA, Open RTL); SoC family
 *![](images/20.png)
 * Main goal of Openlane ASIC is *Clean* GDSII with no human interventions; No LVS or DRC or Timing violations
 * Openlane is tuned for Skywater 130nm PDK
 * Openlane Operation
   - Autonomous : Push button approach
   - Interactive : allows to execute commands and experiment
 * Openlane Design Space exploration : Finds the best set of flow configurations
 * Openlane Design examples : 43 design examples with best configurations
 **_5. Openlane detailed ASIC Flow_**
  *![](images/21.png)
  * Integrated tools of OpenLane 
    - OpenRoad
    - magic VLSI layout Tool
    - K Layout
    - Fault
    - Yosys
    - Qflow
    - ABC
  * RTL Synthesis : RTL is fed to *Yosys* with design constraints
     - Synthesis exploartion
     - Design exploartion : sweep across various configurations and obtain the best one; Openlane regression testing run on 70 designs and obtained the best
  * DFT : Uses *Fault* for Testing ; Optional
  * Physical Implementation/ Automated PnR(Place and Route) : use *OpenRoad* tool
  * LEC(Logic Equivalence Check): Compares *netlist obtained after optimization during Physical implementation* with *Gate level netlist* obtained after RTL synthesis : Uses         *Yosys* tool
  * Dealing with Antenna Rules violation :
    - Fabricated metal wire segment(long) can act as antenna -> collects charges and damages transistor gates during fabrication
  ![](images/22.png) 
    - Solutions :
      - Bridging
      - Add antenna diode cell to leak away charges
   ![](images/23.png)  
   ![](images/24.png) 
  * RC Extraction :  DEF2SPEF
  * Static Timing analysis
      * Open STA using OpenRoad; Output of this stage is a set of Timing parameters that can specify violations if any
  * Physiscal Signoff 
  * DRC & LVS
  * DRC and Spice extraction from Layout : Magic 
  * LVS : Magic and Netgen
**_6. Openlane Directory structure in detail**
* Empty Linux terminal -> own directory
* Basic Linux commands
  - cd work/tools/ --> Change directory
  - ls -ltr --> List files
  - ls -- help --> will list the linux commands
  - clear --> clear page
 * Exploring Openlane Working Directory
   - From *Desktop/work/tools$ ls -ltr*, list the files
     - All tool directories such as openlane working dir, magic, skywater etc.. will be listed
   - From *Desktop/work/tools/openlane_working_dir$ ls -ltr*, list the files
     - openlane
     - pdks
  * Exploring *pdks*
   - From *Desktop/work/tools/openlane_working_dir/pdks$ ls -ltr*, list the files
     - skywater-pdk : foundry files used for commercialized tools; not for open source tools
     - open_pdks : scripts that converts foundry pdks to be compatible with open source tools
     - sky130A : pdk that is made compatible with open source environment
   - From *Desktop/work/tools/openlane_working_dir/pdks/sky130A$ ls -ltr*, list the files
     - libs.ref : contains technology process specific files
     - libs.tech : contains files specific tools
  - From *Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech$ ls -ltr*, list the files
  - From *Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.ref*, list the files
  ![](images/25.png)
  - From *Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.ref/sky130_fd_sc_hd$ ls -lrt*, list the files; fd--> foundry sc--> standard cell hd --> variant of pdk *high density*
    - techlef : technolgy layer information
    - lib : timing information(PVT corners)
    - much more..
  ![](images/26.png)
  * Exploring *openlane*
    - From *Desktop/work/tools/openlane_working_dir/openlane$docker*, run docker and then list files
    - bash-4.25 *ls  -ltr*
    - bash-4.25 *./flow.tcl -interactive*
    - % *package require openlane 0.9* 
      ![](images/27.png)
       - Exploring designs : From *Desktop/work/tools/openlane_working_dir/openlane/designs$ ls -ltr*, list the files
       - Among the various *designs* in openlane we choose *picorv32a*
       - From *Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a$ ls -ltr*, list the files
         - src : contains the verilog file of the RTL design chosen
         - config.tcl : bypasses the prviously set configurations in the openlane flow
         ![](images/28.png)
       - *Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a$ less config.tcl*
         ![](images/29.png)
 * Design preparation step
   - *% prep -design picorv32a* : design preparation stage : merges LEF's
   ![](images/30.png) 
   - AFter the design prepartion stage, execute *Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a$ less config.tcl* ; *runs* directory is created
    - *anitha@openlane-workshop-03:~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs$ ls -ltr* creates 4 folders.
    - */Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/02-07_10-07$ ls -ltr* Open the folder that contains date. This creates the directories required for the openlane
       - cmds.logs
       - tmp
       - results
       - logs
       - reports
       - config.tcl
       -
  ![](images/31.png)
  ![](images/32.png)
  
  * Review files after design preparation step and run synthesis
   - *run_synthesis* : Obtain Static timing analysis and Chip area 
 ![](images/33.png) 
**_7. Steps to characterize synthesis results**
**_8. Openlane Github link**
* efabless openlane github : detailed study in this link

