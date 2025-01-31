---
layout: page
title: Software used in the OSCAR project

used_software:
    - name: GAP
      website: https://www.gap-system.org

    - name: Nemo
      website: https://github.com/Nemocas/Nemo.jl/

    - name: Hecke
      website: https://github.com/thofma/Hecke.jl/

    - name: Polymake
      website: https://www.polymake.org/

    - name: Singular
      website: https://www.singular.uni-kl.de/

    - name: GMP
      website: https://gmplib.org/

    - name: MPFR
      website: https://www.mpfr.org/

    - name: Arb
      website: http://arblib.org/

    - name: NTL
      website: https://www.shoup.net/ntl

    - name: Flint
      website: http://www.flintlib.org

    - name: Antic
      website: https://github.com/wbhart/antic

    - name: gfanlib
      website: https://users-math.au.dk/~jensen/software/gfan/gfan.html

    - name: Factory
      website: https://www.singular.uni-kl.de/ftp/pub/Math/Singular/Factory/README

    - name: cdd
      website: https://www.inf.ethz.ch/personal/fukudak/cdd_home/

    - name: AbstractAlgebra
      website: https://github.com/Nemocas/AbstractAlgebra.jl
      
    - name: msolve
      website: https://msolve.lip6.fr/

used_software_technical:
    - name: CxxWrap.jl
      website: https://github.com/JuliaInterop/CxxWrap.jl

    - name: Julia
      website: https://www.julialang.org
---

### Mathematical software

The OSCAR project is based on the following mathematical software:

{% assign entries = page.used_software | sort_natural:"name" %}
<ul class="software_credits_list">
{% for p in entries %}
  <li>
    <a href="{{ p.website }}">
    <strong>{{ p.name }}</strong>
    </a>
  </li>
{% endfor %}
</ul>

### Technical software

The following software is used as technical components in the OSCAR project:

{% assign entries = page.used_software_technical | sort_natural:"name" %}
<ul>
{% for p in entries %}
  <li>
    <a href="{{ p.website }}">
    <strong>{{ p.name }}</strong>
    </a>
  </li>
{% endfor %}
</ul>


### MaRDI

The [Mathematical Research Data Initiative](https://www.mardi4nfdi.de/about/mission) (MaRDI), is a German consortium dedicated to setting guidelines and developing software for findability, accessibility, interoperability, and reuse of mathematical research data. OSCAR's serialization employs the **mrdi** file format, the specifications of which can be found on [zenodo](https://zenodo.org/records/12723387). More details are available in [this article](https://link.springer.com/chapter/10.1007/978-3-031-64529-7_25) and the [OSCAR documentation](https://docs.oscar-system.org/stable/General/serialization/).
