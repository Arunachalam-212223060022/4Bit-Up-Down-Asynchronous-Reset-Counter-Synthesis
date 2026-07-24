# 4Bit-Up-Down-Asynchronous-Reset-Counter-Synthesis

## Aim

Synthesize 4Bit-Up-Down-Asynchronous-Reset-Counter design using Constraints and analyse reports, Timing, area and Power.

---

## Tool Required

### Functional Simulation

* Incisive Simulator (`ncvlog`, `ncelab`, `ncsim`)

### Synthesis

* Genus

---

## Step 1: Getting Started

Synthesis requires three files as follows:

* Liberty Files (`.lib`)
* Verilog/VHDL Files (`.v` or `.vhdl` or `.vhd`)
* SDC (Synopsis Design Constraint) File (`.sdc`)

---

## Step 2: Creating an SDC File

* In your terminal type the following command to create an SDC File if you do not have one:

```bash
gedit input_constraints.sdc
```

* The SDC File must contain the following commands:

```tcl
create_clock -name clk -period 2 -waveform {0 1} [get_ports "clk"]

set_clock_transition -rise 0.1 [get_clocks "clk"]

set_clock_transition -fall 0.1 [get_clocks "clk"]

set_clock_uncertainty 0.01 [get_ports "clk"]

set_input_delay -max 0.8 [get_ports "rst"] -clock [get_clocks "clk"]

set_output_delay -max 0.8 [get_ports "count"] -clock [get_clocks "clk"]
```

### Description of SDC Commands

| Command | Description                                                                            |
| ------- | -------------------------------------------------------------------------------------- |
| i       | Creates a Clock named **"clk"** with Time Period 2 ns and On Time from t = 0 to t = 1. |
| ii, iii | Sets Clock Rise and Fall time to 100 ps.                                               |
| iv      | Sets Clock Uncertainty to 10 ps.                                                       |
| v, vi   | Sets the maximum limit for I/O port delay to 1 ps.                                     |

---

## Step 3: Performing Synthesis

### Library Information

* The Liberty files are present in the library path.
* The Available technology nodes are:

  * 180 nm
  * 90 nm
  * 45 nm

### Initializing the Tool Environment

* In the terminal, initialise the tools with the following commands if a new terminal is being used:

```bash
csh
```

```bash
source /cadence/install/cshrc
```

### Launching Genus

* The tool used for Synthesis is **Genus**.

* Type the following command to open the tool:

```bash
genus -gui
```

### Synthesis Flow

* Genus Script file with `.tcl` file Extension commands are executed one by one to synthesize the netlist.

---

## Generated Outputs

### RTL Schematic

> <img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/4557b9a3-33fd-478e-9b1b-6a699db509e5" />


---

### Area Report

> <img width="1600" height="332" alt="image" src="https://github.com/user-attachments/assets/8cc9f97d-2e70-46bb-9d8b-8b7b9e3c4a98" />


---

### Power Report

> <img width="1600" height="379" alt="image" src="https://github.com/user-attachments/assets/cd5061c1-a11e-4d16-819a-9bad6c2fd9ca" />

---

### Timing Report

> <img width="1600" height="718" alt="image" src="https://github.com/user-attachments/assets/5f65da8e-dcf4-45c3-ace9-c6b47625c225" />


---

## Result

The generic netlist has been created, and area, power, and timing reports have been tabulated and generated using Genus.
