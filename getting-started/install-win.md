---
layout: page
title: Installation Instructions for Windows
---

<div class="message">
  <strong>WARNING:</strong>
  The installation process of OSCAR, particularly the precompilation step, requires 
  <strong>at least 6GB of free memory</strong>. For optimal performance with OSCAR, we recommend having <strong>at least 16GB of free memory</strong>.
</div>

The following instructions assume that you are at least somewhat familiar with using a terminal interface.


## Step 1: Install Windows Subsystem for Linux (WSL)

1. Follow the official instructions to install [Ubuntu](https://learn.microsoft.com/en-us/windows/wsl/install) as your [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install).
2. Ensure your WSL subsystem has **at least 6GB of free memory** for the installation process, and ideally **16GB for optimal performance**. The memory available to WSL is **less than the total memory on your system**. To adjust the memory allocation, follow the [official WSL configuration instructions](https://learn.microsoft.com/en-us/windows/wsl/wsl-config#main-wsl-settings). You can view a sample `.wslconfig` file [here](https://learn.microsoft.com/en-us/windows/wsl/wsl-config#example-wslconfig-file).
3. After installing WSL, you should see the *Ubuntu* app in your start menu.


## Step 2: Install Julia

<div class="message">
   <strong>WARNING:</strong> 
   Do <strong>not</strong> install the Windows version of Julia. Instead, install the Linux version of Julia inside <a href="https://learn.microsoft.com/en-us/windows/wsl">WSL</a>, following the steps below.
</div>

1. Open the *Ubuntu* app from your start menu (installed in Step 1).
2. *OSCAR* requires [Julia](https://julialang.org) 1.6.0 or higher. We recommend using the latest stable release of Julia.
3. We suggest installing Julia via [juliaup](https://github.com/JuliaLang/juliaup) for easy updates and version management. *juliaup* will automatically install the latest stable release of Julia and allows you to manage multiple Julia versions if needed.
4. To install Julia via *juliaup*, run the following command in your WSL terminal:
   ```sh
   curl -fsSL https://install.julialang.org | sh
   ```
5. Alternatively, you can [download Julia directly from the official website](https://julialang.org/downloads/) and follow the [installation instructions for Linux Ubuntu]((https://julialang.org/downloads/platform/).


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

Additionally, to view tutorials in the browser, you need a browser installed in WSL. *Ubuntu* installs browsers via Snap, but Snap is disabled in WSL. To install a browser like Firefox, follow the instructions [here](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04).

Finally, if you open a tutorial notebook (stored as a `.ipynb` file) and encounter a "Kernel error" due to an older Julia version, you can resolve this by selecting a different Julia kernel from the notebook's kernel menu.
