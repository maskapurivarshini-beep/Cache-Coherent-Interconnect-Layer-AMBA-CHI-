# Cache-Coherent Interconnect Layer Verification (AMBA CHI)

An advanced verification project focused on testing multi-master cache-coherency logic across processing nodes utilizing the industry-standard **AMBA CHI (Coherent Hub Interface)** protocol framework.

## 🚀 Key Features & Architectural Highlights
* **Assertion-Driven Design:** Developed and deployed over **120+ SystemVerilog Assertions (SVA)** explicitly targeted at capturing illegal protocol cache transitions.
* **Coherency Verification:** Verified complex ReadShared, WriteBack, and Snoop protocol transitions across multiple local caches.
* **Coverage Tracking:** Created exhaustive covergroups tracking Snoop transaction state combinations, driving functional metrics past a strict **99.8% verification sign-off limit**.
* **Scalable Testing:** Built modular UVM components designed to allow quick modification of the total cluster node count (2 to 8 nodes).

## 📂 Repository Structure
```text
├── docs/               # Protocol state-transition tracking notes
├── rtl/                # Cache Coherent Interconnect fabric
└── tb/                 # UVM Testbench Environment 
    ├── chi_mon/        # AMBA CHI Interface Protocol Monitors
    ├── sva_bind/       # SVA assertion binding declarations
    ├── covergroups/    # Functional Coverage Definition blocks
    └── chi_tb_top.sv   # Interconnect System Harness
```

## 🛠️ Tools & Prerequisites
* **EDA Simulators:** Siemens QuestaSim (highly recommended for coverage viewing) or Synopsys VCS
* **Methodology:** Universal Verification Methodology (UVM 1.2)

## 💻 How to Run Simulations
Execute multi-node coherent transaction scenarios:
```bash
vsim -c -do "run -all; coverage save -onexit metrics.ucdb; quit" tb_top +UVM_TESTNAME=chi_multi_node_stress_test
```
To view the functional coverage matrix matching the 99.8% sign-off criteria:
```bash
vsim -viewcov metrics.ucdb
```
