---
layout: post
title:  "Installing Open Source Silicon Design Tools"
date:   2020-07-25 12:00:00
author: Soumil Heble
comments: true
categories: silicon tools
---

<div class="three-img-bar">
	<ul>
		<li><img src="/media/posts/2020-07-25-installing-open-source-silicon-design-tools/verilator_logo.png" alt="Verilator Logo"></li>
        <li><img src="/media/posts/2020-07-25-installing-open-source-silicon-design-tools/gtkwave_logo.png" alt="GTKWave Logo"></li>
		<li><img src="/media/posts/2020-07-25-installing-open-source-silicon-design-tools/wavedrom_logo.png" alt="Wavedrom Logo"></li>
	</ul>
</div>

> I use the terms Silicon Design/Silicon Development to describe the design and development of ASICs, CPUs, GPUs, SOCs, and FPGAs.

> This is in no way a comprehensive list of Open Source Silicon Design tools out there. This is just a list of tools I use, and I'll keep updating this list if I start using new tools.

## The Excitement of Open Source Silicon Design Tools
A decade ago if you were thinking of dipping your toes in the world of silicon design and development you'd need access to tools from the `Big 3 EDA vendors` - `Mentor Graphics`, `Synopsys`, or `Cadence Design Systems`. The only way to get access to these tools is to purchase a license from the vendor, and it's not cheap. So you have to either be a student at a University that has purchased a license, work at a semiconductor company, or have deep pockets to buy one (I'm not sure whether the vendors supply license to individuals).

## OS and Install Location(s)
{% include image.html name="kubuntu_focal_banner.png" alt="Kubuntu Focal Fossa 20.04 LTS Banner" width="740px" class="center" %}

> All the following steps of compiling and installing the software have been done on a <a href="https://kubuntu.org/" target="_blank">Kubuntu Focal Fossa 20.04 LTS</a> based system.

I like `Ubuntu` because of the simplicity, wide adoption by the general public, abundant documentation, and a lot of developer effort spent on the distro. However, I also like customization. The `GNOME` desktop environment, though polished, does not provide a lot of customizations like the `K` desktop environment (`KDE`) does. Kubuntu marries together the Ubuntu distribution with a `KDE` desktop environment which is exactly what I need.

#### Install Location

| Directory Path | Reason |
|:-:|:-:|
| /opt | Software that has been pre-compiled and is ready to be used after the download/extracting from the compressed file |
| /usr/local | Software that has been compiled on the system from the source code |

## The Tools
We are going to compile and install these tools from the source if possible because the `package manager (apt)/snap` versions of these tools might be old and may not have features that are implemented in the latest stable release.

### GTKWave - Waveform Viewer
> <a href="http://gtkwave.sourceforge.net/" target="_blank">GTKWave</a> is an analysis tool used to perform debugging on Verilog or VHDL simulation models.  With the exception of interactive VCD viewing, it is not intended to be run interactively with simulation, but instead relies on a post-mortem approach through the use of dumpfiles. - <a href="http://gtkwave.sourceforge.net/gtkwave.pdf" target="_blank">GTKWave Manual</a>

**My Use Case:** To view the waveform dumped by tests run on Icarus Verilog or Verilator.

{% include image.html name="gtkwave.png" alt="GTKWave Window" width="740px" class="center" %}

#### Prerequsite Packages
{% highlight shell %}sudo apt install zlib1g bzip2 gperf
sudo apt install tcl-dev tk-dev liblzma-dev autoconf
sudo apt install libgtk2.0-dev flex
sudo apt install libcanberra-gtk-module	#Ubuntu
sudo apt install gnome-themes-standard	#Kubuntu{% endhighlight %}

* Download the latest version of source code from <a href="https://sourceforge.net/projects/gtkwave/files/" target="_blank">GTKWave SourceForge Site</a>. 
* Uncompress source code and run the following commands inside the directory.

{% highlight shell %}./configure
make #Use make -j$(nproc) is nproc is installed
sudo make install{% endhighlight %}

* Make sure that you have `/usr/local/bin` in your shell's PATH variable.
* Check the installation by running `gtkwave -V` and it should print out the version information.

### Wavedrom - Timing Diagram and Waveform Documentation
> WaveDrom draws your Timing Diagram or Waveform from simple textual description. It comes with description language, rendering engine and the editor. WaveDrom editor works in the browser or can be installed on your system. Rendering engine can be embeded into any webpage. - <a href="https://wavedrom.com/" target="_blank">WaveDrom</a>

**My Use Case:** To document timing diagrams of protocols or designs and register definitions.

{% include image.html name="wavedrom.png" alt="WaveDrom Generated Timing Diagram" width="740px" class="center" %}

* Download the pre-compiled release of WaveDrom for `linux-x64` from <a href="https://github.com/wavedrom/wavedrom.github.io/releases" target="_blank">WaveDrom GitHub Releases</a>.
* Uncompress the download and `sudo` move the directory to `/opt/`
* Make sure that you have `/opt/<wavedrom_directory_name>/` in your shell's PATH variable `OR`
* I add the following line to my Shell's `rc` file which opens wavedrom in background and redirects stdout and stderr to `/dev/null`.
{% highlight shell %}alias wavedrom='/opt/wavedrom-editor-v2.4.2-linux-x64/wavedrom-editor > /dev/null 2>&1 &'{% endhighlight %}
* KDE also allows you to add a custom menu item that triggers a command. You can use the above alias to do so and add the WaveDrom logo as the application's icon. KDE is pretty neat huh!

### Icarus Verilog - Verilog Simulation Tool
> Icarus Verilog is a Verilog simulation and synthesis tool. It operates as a compiler, compiling source code written in Verilog (IEEE-1364) into some target format. - <a href="http://iverilog.icarus.com/" target="_blank">Icarus Verilog</a>

**My Use Case:** Write Verilog testbenches, simulate designs, and use along with SymbiYosys to do formal verification.

{% include image.html name="icarus_verilog_logo.png" alt="Icarus Verilog Logo" width="512px" class="center" %}

#### Prerequsite Packages
{% highlight shell %}sudo apt install bison{% endhighlight %}

* Download the latest source code release from <a href="ftp://icarus.com/pub/eda/verilog/v10" target="_blank">Icarus Verilog's FTP Server</a>.
* Uncompress the source code and run the following commands inside the directory.

{% highlight shell %}./configure
make #Use make -j$(nproc) is nproc is installed
sudo make install{% endhighlight %}

* Make sure that you have `/usr/local/bin` in your shell's PATH variable.
* Check the installation by running `iverilog -v` and it should print out the version information.

### Yosys - Design Synthesis
> Yosys is a framework for Verilog RTL synthesis. It currently has extensive Verilog-2005 support and provides a basic set of synthesis algorithms for various application domains. - <a href="http://www.clifford.at/yosys/" target="_blank">Yosys</a>

**My Use Case:** Use along with SymbiYosys to do formal verification and synthesize Verilog for <a href="http://www.latticesemi.com/iCE40" target="_blank">Lattice iCE40</a> FPGA.

{% include image.html name="yosys.png" alt="Yosys Design Element Diagram" width="512px" class="center" %}

#### Prerequsite Packages
{% highlight shell %}sudo apt install build-essential clang bison flex \
	libreadline-dev gawk tcl-dev libffi-dev git \
	graphviz xdot pkg-config python3 libboost-system-dev \
	libboost-python-dev libboost-filesystem-dev zlib1g-dev{% endhighlight %}

* Download the latest source code release from <a href="https://github.com/YosysHQ/yosys/releases" target="_blank">Yosys GitHub Releases</a>.
* Uncompress the source code and run the following commands inside the directory.

{% highlight shell %}make config-gcc
echo "PREFIX := /usr/local" >> Makefile.conf
make #Use make -j$(nproc) is nproc is installed
sudo make install{% endhighlight %}

* Check the installation by running `yosys -V` and it should print out the version information.

### SystemC Libraries - Event Driven Simulation Library
> SystemC is a set of C++ classes and macros which provide an event-driven simulation interface (see also discrete event simulation). These facilities enable a designer to simulate concurrent processes, each described using plain C++ syntax. - <a href="https://en.wikipedia.org/wiki/SystemC" target="_blank">Wikipedia</a>

**My Use Case:** Modelling functionality of designs and connecting them to SystemC testbenches along with open-source RISC-V cores.

{% include image.html name="systemc_logo.jpg" alt="SystemC Logo" width="300px" class="center" %}

* `SystemC` is an <a href="https://en.wikipedia.org/wiki/Accellera" target="_blank">Accelera</a> standard and the libraries are maintained <a href="https://www.accellera.org/downloads/standards/systemc" target="_blank">here</a>.
* Download the latest source code release from <a href="https://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.3.tar.gz" target="_blank">Accelera's Download Page</a>.
* Uncompress the source code and run the following commands inside the directory.

{% highlight shell %}mkdir objdir
cd objdir
../configure --prefix=/usr/local/systemc-2.3.3 --enable-debug
make #Use make -j$(nproc) is nproc is installed
make check
sudo make install{% endhighlight %}

### Verilator - Verilog to C++ Behavioural Model
> Verilator is a free and open-source software tool which converts Verilog (a hardware description language) to a cycle-accurate behavioral model in C++ or SystemC. It is restricted to modeling the synthesizable subset of Verilog and the generated models are cycle-accurate, 2-state, with synthesis (zero delay) semantics. - <a href="https://en.wikipedia.org/wiki/Verilator" target="_blank">Wikipedia</a>

**My Use Case:** This my go to software for running tests on the designs that I develop. Its fast, easy to use and C++ based. Recently I used it with the `lowRISC ibex` RISC-V core to run a few simple assembly tests.

{% include image.html name="verilator_logo.png" alt="Verilator Logo" width="256px" class="left-float" %}

Verilator can convert Verilog to C++ or SystemC based executables. We are going to compile Verilator with SystemC libraries but we can select during Verilog compilation whether we want the executable to be C++ or SystemC based. Having SystemC support comes in handy when you want to integrate your design with other SystemC based designs.

#### Prerequsite Packages
{% highlight shell %}sudo apt install perl python3 make
sudo apt install g++ ccache libgoogle-perftools-dev numactl
sudo apt install libfl2 libfl-dev zlibc zlib1g zlib1g-dev
sudo apt install git autoconf flex bison{% endhighlight %}

* Run the following commands:

{% highlight shell %}git clone https://github.com/verilator/verilator
cd verilator
git pull
git tag
git checkout stable
autoconf
export SYSTEMC_INCLUDE=/usr/local/systemc-2.3.3/include
export SYSTEMC_LIBDIR=/usr/local/systemc-2.3.3/lib-linux64
unset VERILATOR_ROOT
./configure --prefix /usr/local
make #Use make -j$(nproc) is nproc is installed
make test
sudo make install{% endhighlight %}

* Check the installation by running `verilator -V` and it should print out the version information.

**Additional Tasks:** You will need to add the path of SystemC libraries to the GNU linker environment variable `LD_LIBRARY_PATH` so that Verilator can pick it up if need be during Verilog compilation. Add the following lines to your Shell's configuration file.

{% highlight shell %}export SYSTEMC_LIBDIR='/usr/local/systemc-2.3.3/lib-linux64'
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:$SYSTEMC_LIBDIR"{% endhighlight %}

### IceStorm - Lattice iCE40 FPGA Development Tools
> Project IceStorm aims at documenting the bitstream format of Lattice iCE40 FPGAs and providing simple tools for analyzing and creating bitstream files. The IceStorm flow (Yosys, Arachne-pnr, and IceStorm) is a fully open source Verilog-to-Bitstream flow for iCE40 FPGAs. - <a href="http://www.clifford.at/icestorm/" target="_blank">Project IceStorm</a>

**My Use Case:** Program my <a href="https://www.latticesemi.com/icestick" target="_blank">iCEstick Evaluation Board</a> based on the Lattice iCE40 HX1K FPGA.

#### Prerequsite Packages
{% highlight shell %}sudo apt install build-essential clang bison flex libreadline-dev \
        gawk tcl-dev libffi-dev git mercurial graphviz   \
        xdot pkg-config python python3 libftdi-dev \
        qt5-default python3-dev libboost-all-dev cmake libeigen3-dev{% endhighlight %}

* Run the following commands:
{% highlight shell %}git clone https://github.com/cliffordwolf/icestorm.git icestorm
cd icestorm
make #Use make -j$(nproc) is nproc is installed
sudo make install{% endhighlight %}

### NextPnR - FPGA Place and Route Tool
> nextpnr aims to be a vendor neutral, timing driven, FOSS FPGA place and route tool. - <a href="https://github.com/YosysHQ/nextpnr" target="_blank">NextPnR GitHub</a>

**My Use Case:** Place and Route Yosys synthesized design for my <a href="https://www.latticesemi.com/icestick" target="_blank">iCEstick Evaluation Board</a>.

{% include image.html name="nextpnr.png" alt="NextPnR GUI" width="740px" class="center" %}

* Run the following commands:
{% highlight shell %}git clone https://github.com/YosysHQ/nextpnr nextpnr
cd nextpnr
cmake -DARCH=ice40 -DCMAKE_INSTALL_PREFIX=/usr/local .
make #Use make -j$(nproc) is nproc is installed
sudo make install{% endhighlight %}

* Check the installation by running `nextpnr-ice40 -V` and it should print out the version information.

### <a href="https://symbiyosys.readthedocs.io" target="_blank">SymbiYosys</a> - Formal Verification Tool
> SymbiYosys (sby) is a front-end driver program for Yosys-based formal hardware verification flows. - <a href="https://github.com/YosysHQ/SymbiYosys" target="_blank">SymbiYosys GitHub</a>

**My Use Case:** Formal verification of my Verilog RTL designs.

* Run the following commands:
{% highlight shell %}git clone https://github.com/YosysHQ/SymbiYosys.git SymbiYosys
cd SymbiYosys
sudo make install{% endhighlight %}

### Yices 2, Z3 & Bootlector - <a href="https://en.wikipedia.org/wiki/Satisfiability_modulo_theories" target="_blank">SMT</a> Solvers 

**My Use Case:** SMT solvers for SmbiYosys formal verification flow

#### Yices2
* Run the following commands:
{% highlight shell %}git clone https://github.com/SRI-CSL/yices2.git yices2
cd yices2
autoconf
./configure
make #Use make -j$(nproc) is nproc is installed
sudo make install{% endhighlight %}

* Check the installation by running `yices -V` and it should print out the version information.

#### Z3
* Run the following commands:
{% highlight shell %}git clone https://github.com/Z3Prover/z3.git z3
cd z3
python scripts/mk_make.py
cd build
make #Use make -j$(nproc) is nproc is installed
sudo make install{% endhighlight %}

#### Boolector
* Run the following commands:
{% highlight shell %}git clone https://github.com/boolector/boolector
cd boolector
./contrib/setup-btor2tools.sh
./contrib/setup-lingeling.sh
./configure.sh
make -C build #Use make -C build -j$(nproc) is nproc is installed
sudo cp build/bin/{boolector,btor*} /usr/local/bin/
sudo cp deps/btor2tools/bin/btorsim /usr/local/bin/{% endhighlight %}

* Check the installation by running `boolector -V` and it should print out the version information.



{% include image.html name="fin.jpg" alt="PC from the 2000's" width="740px" class="center" caption="<a href=\"https://www.flickr.com/photos/christophebecker/39643834842\" target=\"_blank\">That's all Folks!</a> by <a href=\"https://www.flickr.com/photos/christophebecker/\" target=\"_blank\">Christophe Becker</a> is licensed under <a href=\"https://creativecommons.org/licenses/by-nd/2.0/\" target=\"_blank\">CC BY-ND 2.0</a>" %}