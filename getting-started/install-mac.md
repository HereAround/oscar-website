---
layout: page
title: Installation Instructions for MacOS
---

<div class="message">
  <strong>WARNING:</strong>
  The installation process of OSCAR, particularly the precompilation step, requires 
  <strong>at least 6GB of free memory</strong>. For optimal performance with OSCAR, we recommend having <strong>at least 16GB of free memory</strong>.
</div>

The following instructions assume that you are at least somewhat familiar with using a terminal interface.


## Step 1: Install prerequisites

If you are using macOS 10.12 or newer, you need to install the Xcode command line tools, as explained in the following instructions.

1. Launch a Terminal and copy and paste the command <code>xcode-select --install</code>, then press enter.
2. A window will appear asking you: <q>The xcode-select command requires the command line developer tools. Would you like to install the tools now?</q>. Confirm this by clicking <q>Install</q>.
3. Wait for this to complete; it needs to download about 130 MB of data.
4. You can verify that everything worked by verifying that the folder <code>/Library/Developer/CommandLineTools/usr/bin/</code> exists and contains executables such as <code>clang</code> and <code>clang++</code>, the C and C++ compiler.


## Step 2: Install Julia

<div class="message">
   <strong>WARNING:</strong>
   macOS users should generally <strong>not</strong> install the Julia version
   provided by their package manager (e.g., `apt`, `pac`, `dnf`, `homebrew`, ...), as in many cases,
   these Julia version are either outdated, or crippled, or both.
</div>

1. *OSCAR* requires [Julia](https://julialang.org) 1.6.0 or higher. We recommend using the latest stable release of Julia.
2. We suggest installing Julia via [juliaup](https://github.com/JuliaLang/juliaup) for easy updates and version management. *juliaup* will automatically install the latest stable release of Julia and allows you to manage multiple Julia versions if needed.
3. To install Julia via *juliaup*, run the following command in your WSL terminal:
   ```sh
   curl -fsSL https://install.julialang.org | sh
   ```
4. Alternatively, you can [download Julia directly from the official website](https://julialang.org/downloads/) and follow the [installation instructions for macOS]((https://julialang.org/downloads/platform/).


## Step 3: Install OSCAR

1. Open the Julia REPL in your WSL terminal.
2. Install OSCAR by running the following commands:
   ```julia
   using Pkg
   Pkg.add("Oscar")
   ```
   This process will take a few minutes to complete, as it will install OSCAR and its dependencies. Internet access is required.


## Step 4: Start OSCAR

After the installation is complete, you can start using OSCAR by running `using Oscar` in the Julia REPL:
```console?lang=julia
julia> using Oscar
  ___   ____   ____    _    ____
 / _ \ / ___| / ___|  / \  |  _ \   |  Combining ANTIC, GAP, Polymake, Singular
| | | |\___ \| |     / _ \ | |_) |  |  Type "?Oscar" for more information
| |_| | ___) | |___ / ___ \|  _ <   |  Manual: https://docs.oscar-system.org
 \___/ |____/ \____/_/   \_\_| \_\  |  Version 1.0.0
```


## Step 5: Running Tutorials Locally with IJulia

To run tutorials locally, you will need to install the *IJulia* package:

1. Install *IJulia* (and jupyter) by issuing the following command in your Julia REPL:
```julia
using Pkg; Pkg.add("IJulia")
```
For more information, visit the [installation guide](https://julialang.github.io/IJulia.jl/stable/manual/installation/).
2. In some cases, you may need to explicitly build *IJulia*; for troubleshooting, refer to the [IJulia troubleshooting page](https://julialang.github.io/IJulia.jl/stable/manual/troubleshooting/).

If you open a tutorial notebook (stored as a `.ipynb` file) and encounter a "Kernel error" due to an older Julia version, you can resolve this by selecting a different Julia kernel from the notebook's kernel menu.
