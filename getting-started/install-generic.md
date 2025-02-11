---
layout: page
---

<div class="platform-tabs">
  <input type="radio" id="mac" name="platform">
  <label for="mac" onclick="window.location.href='{{site.baseurl}}/getting-started/install-mac/'">Mac</label>

  <input type="radio" id="windows" name="platform">
  <label for="windows" onclick="window.location.href='{{site.baseurl}}/getting-started/install-win/'">Windows</label>

  <input type="radio" id="linux" name="platform">
  <label for="linux" onclick="window.location.href='{{site.baseurl}}/getting-started/install-linux/'">Linux</label>

  <input type="radio" id="other" name="platform" checked>
  <label for="other" onclick="window.location.href='{{site.baseurl}}/getting-started/install-generic/'">Other</label>
</div>


## Generic Installation Instructions


We do not provided support for operating systems other than Windows, macOS, and Linux (Debian, Ubuntu, Fedora).

If you wish to try anyway, you will need to install at least GNU make, and a fairly recent C++ compiler supporting the C++17 standard.
Suitable compilers include:
* GNU C/C++ compiler (gcc) version 7 or newer,
* Clang C/C++ compiler version 5 or newer,
* Intel C/C++ Compiler (icc) version 19.0 or newer.

<div class="message">
  <strong>WARNING:</strong>
  The installation process of OSCAR, particularly the precompilation step, requires <strong>at least 6GB of free memory</strong>. For optimal performance with OSCAR, we recommend having <strong>at least 16GB of free memory</strong>.
</div>


## Advanced Installation Instructions

It is possible to install OSCAR and its cornerstones only once on your system,
and to let several people use this installation. For that, the following `bash` scripts can be used.

<div class="clickdesc">

<details>
<summary>
Install OSCAR system-wide,
or update the system-wide installation of OSCAR when a new version is available.
</summary>
Enter the following commands into a file (for example <code>oscar_systemwide_install</code>),
adjust the paths for the variables <code>julia_for_oscar</code> and <code>central_depot</code>,
and then run the script in a terminal (with administrator rights).
{% highlight bash %}
#!/bin/bash

# Specify the intended version of Julia.
julia_for_oscar=/users/oscar/julia-1.8.5/bin/julia

# Specify the intended location of the central Oscar installation.
central_depot=/users/oscar/JULIA_DEPOT

# We will store the necessary artifacts in the
# "architecture dependent location" in Julia's default DEPOT_PATH.
# First determine this path and create the directory if necessary.
# (Here we asume that `DEPOT_PATH[2]` is the architecture-specific
# shared system directory, as documented for the default value of
# `DEPOT_PATH`.)
system_depot=$(${julia_for_oscar} --startup-file=no -e 'println(DEPOT_PATH[2])')
mkdir -p "${system_depot}/artifacts"

# Set the Julia variables that control the location of packages.
# (Do not admit the current user's own depot path.)
export JULIA_DEPOT_PATH=${central_depot}:${system_depot}

# Clean the environment, such that the already centrally installed packages
# get replaced by newer versions if necessary.
# (This is safer than calling `Pkg.update()` in Julia.)
# Then let Julia install and precompile the packages.
${julia_for_oscar} --project=@v#.#-oscar -e 'using Pkg, Artifacts; \
rm("'${central_depot}'/environments/v" * join(split(string(VERSION), ".")[1:2], ".") * "/Project.toml", force=true)
Artifacts.with_artifacts_directory("'${system_depot}'/artifacts") do; \
Pkg.add("Oscar"); \
Pkg.add("GAP"); \
Pkg.add("Nemo"); \
Pkg.add("Hecke"); \
Pkg.add("Singular"); \
Pkg.add("Polymake"); \
Pkg.add("AbstractAlgebra"); \
Pkg.instantiate(); \
end; \
exit();'
{% endhighlight %}
</details>

<details>
<summary>
Call Julia such that the system-wide installation of Oscar gets loaded
when the user enters <code>using Oscar</code> in the Julia session.
</summary>
Enter the following commands into a file (for example <code>julia_with_oscar</code>),
adjust the paths for the variables <code>julia_for_oscar</code> and <code>central_depot</code>,
and then run the script in a terminal (not with administrator rights).
{% highlight bash %}
#!/bin/bash

# Specify the intended version of Julia.
julia_for_oscar=/users/oscar/julia-1.8.5/bin/julia

# Specify the intended location of the central Oscar installation.
central_depot=/users/oscar/JULIA_DEPOT

# Admit the path with the central installation.
export JULIA_DEPOT_PATH=:${central_depot}
export JULIA_LOAD_PATH=":@v#.#-oscar"

# Call Julia.
${julia_for_oscar} $*
{% endhighlight %}
</details>

</div>

<div class="message">
  <strong>WARNING:</strong>
  Users of such a system-wide installation may run into Julia errors if they have already installed some dependencies of OSCAR in their <code>~/.julia/packages</code>, or if they <C>add</C> them later on.
</div>

