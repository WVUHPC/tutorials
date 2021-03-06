---
title: "Introduction"
teaching: 30
exercises: 30
questions:
- "What is High-Performance Computing?"
- "What is a HPC cluster or Supercomputer?"
- "How my computer compares with a HPC cluster?"
- ""
objectives:
- "Learn the components of the HPC"
- "Learn the basic terminology in HPC"
keypoints:
- "Learn about CPUs, cores, and cache, and comparing your own machine with an HPC cluster"
---
## High Performance Computing

<iframe width="560" height="315" src="https://www.youtube.com/embed/R59I_wjBhqA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

High-Performance Computing is about size and speed. A HPC cluster is made of tens, hundreds or even thousands of relatively normal computers specially connected to perform intensive computational operations. In most cases those operations involve large numerical calculations that take too much time to complete and therefore are simply unfeasible to perform on a normal machine.

This is a very pragmatic tutorial: more time on examples and exercises, less time on theoretical stuff. The idea is that after these lessons, you will have learned how to enter into the cluster, compile code, execute using the queue system and transfer data in an out the cluster.

### What are the specifications of my own computer?

Check your computer, gather information about the CPU, number of Cores, Total RAM memory and Hard Drive.

The purpose of this exercise is to compare your machine with our clusters

You can see specs for our clusters [Spruce Knob](https://docs.hpc.wvu.edu/text/82.Spruce.html) and [Thorny Flat](https://docs.hpc.wvu.edu/text/83.ThornyFlat.html)

Try to gather an idea on the Hardware present on your machine and see the hardware we have on Spruce Knob or Thorny Flat

Here are some tricks to get that data from several Operating Systems


<div id="shell">
<div>
  <ul class="nav nav-tabs nav-justified" role="tablist">
    <li role="presentation" class="active"><a data-os="windows" href="#shell-windows" aria-controls="Windows" role="tab" data-toggle="tab">Windows</a></li>
    <li role="presentation"><a data-os="macos" href="#shell-macos" aria-controls="MacOS" role="tab" data-toggle="tab">MacOS</a></li>
    <li role="presentation"><a data-os="linux" href="#shell-linux" aria-controls="Linux" role="tab" data-toggle="tab">Linux</a></li>
  </ul>

  <div class="tab-content">
    <article role="tabpanel" class="tab-pane active" id="shell-windows">
      Open the File Explorer, search for the icon, "This PC" and click with the right mouse button and click properties.

      You should be able to see something like:

      <a href="{{ page.root }}/fig/Windows10.png">
        <img src="{{ page.root }}/fig/Windows10.png" alt="Windows 10" />
      </a>
    </article>
    <article role="tabpanel" class="tab-pane active" id="shell-macos">
    On MacOS click on the top left corner (The Apple Icon), click on "About this Mac" and you will get the basic information.

    <a href="{{ page.root }}/fig/MacOS.png">
    <img src="{{ page.root }}/fig/MacOS.png" alt="MacOS" />
    </a>

    If you want more data click on "System Report..." and you will get:

    <a href="{{ page.root }}/fig/MacOS-SystemReport.png">
      <img src="{{ page.root }}/fig/MacOS-SystemReport.png" alt="MacOS System Report" />
    </a>


    </article>
    <article role="tabpanel" class="tab-pane active" id="shell-linux">
    <p>
    In Linux gathering the data from a GUI depends a lot from more from the exact distribution you are using here some tools that you can try

    <h4> KDE Info Center </h4>

    <a href="{{ page.root }}/fig/KDEInfoCenter.png">
      <img src="{{ page.root }}/fig/KDEInfoCenter.png" alt="KDEInfoCenter" />
    </a>

    <h4> Linux Mint Cinnamon System Info </h4>

    <a href="{{ page.root }}/fig/MintCinnamon.png">
      <img src="{{ page.root }}/fig/MintCinnamon.png" alt="MintCinnamon" />
    </a>

    <h4> Linux Mint Cinnamon System Info </h4>

    <a href="{{ page.root }}/fig/HardInfo.png">
      <img src="{{ page.root }}/fig/HardInfo.png" alt="HardInfo" />
    </a>
    </p>
    </article>
  </div>
</div>
</div>
{% comment %}
    It is probably easier from the command line CLI but this is too early of a stage for that. In case you know how to get access to a terminal here are a few commands to try:

    <code>
    bash-4.2# cat /proc/cpuinfo
    </code>
    {: .source}

    <code>
    processor       : 0
    vendor_id       : GenuineIntel
    cpu family      : 6
    model           : 63
    model name      : Intel(R) Xeon(R) CPU E5-2680 v3 @ 2.50GHz
    stepping        : 2
    microcode       : 0x1
    cpu MHz         : 2494.224
    cache size      : 16384 KB
    physical id     : 0
    siblings        : 1
    core id         : 0
    cpu cores       : 1
    apicid          : 0
    initial apicid  : 0
    fpu             : yes
    fpu_exception   : yes
    cpuid level     : 13
    wp              : yes
    flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon rep_good nopl xtopology eagerfpu pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt arat md_clear spec_ctrl intel_stibp
    bogomips        : 4988.44
    clflush size    : 64
    cache_alignment : 64
    address sizes   : 46 bits physical, 48 bits virtual
    power management:
    </code>
    {: .output}

    <code>
    bash-4.2# free
    </code>
    {: .source}

    <code>
                  total        used        free      shared  buff/cache   available
    Mem:        1882216      174700     1309236       17008      398280     1526060
    Swap:             0           0           0
    </code>
    {: .output}
{% endcomment %}
## Central Processing Units

### CPU Brands and Product lines

There are only two manufacturers that hold most of the market for PC consumer computing: Intel and AMD. There are several others manufacturers of CPUs but those are mostly for Smart Phones, Photo Cameras, Musical Instruments, or very specialized HPC clusters and equipment.

More than a decade ago, the main feature used for marketing purposes on a CPU was the speed. That has changed now as CPUs are not getting much faster
due to faster clock speed. It is hard to market the performance of a new processor with a single number. That is why CPUs are now marketed with "Product Lines" and the "Model numbers" those number bear no direct relation with the actual characteristics of a given processor.

For example, Intel Core i3 processors are marketed for entry level machines more tailored to basic computing tasks like word processing and web browsing. On the other hand, Intel???s Core i7 and i9 processors are for high-end products aimed at the top of the line gaming machines able to run the most recent titles at high FPS and resolutions. Machines for enterprise usage are usually under the Xeon Line.

On AMD???s side, you have the Athlon line aimed at entry-level users, From Ryzen(TM) 3 for basic applications, all the way to the Ryzen(TM) 9 designed mostly for enthusiasts and gamers. AMD also has product lines for enterprises like EPYC Server Processors.

### Cores

Consumer level CPUs up to 2000s only had one core, but Intel and AMD both hit a brick wall with incremental clock speeds improvements. The heat and power consumption scales non-linearly with the CPU speed. That brings us to the current trend and instead of a single core, CPUs now have two, three, four, eight or sixteen cores on a single CPU. That means that each CPU (in marketing terms) is actually several CPUs (in actual component terms).

### Hyperthreading

Hyperthreading is intrinsically linked to cores and is best understood as a proprietary technology that allows the operating system, to recognize the CPU as having double the amount of cores.

In practical terms, a CPU with four physical cores would be recognized by the operating system as having eight virtual cores, or capable of dealing with eight threads of execution. The idea is that by doing that it is expected that the CPU is able to better manage the extra load, by reordering execution and pipelining the workflow to the actual number of physical cores.

In the context of HPC there is still debate if activating Hyperthreading is beneficial for intensive numerical operations and the answer is very dependent on the code. In our clusters Hyperthreading is disabled on all compute nodes and enabled on service nodes.

### CPU Frequency

Back in the 80s and 90s CPU frequency was the most important feature of a CPU or at least that was the way it was marketed.

Other names for CPU frequency are "clock rate", or "clock speed". CPUs work by steps instead of continuous flow of information. The speed of the CPU is today measured in GHz, or how quickly the processor can process instructions in any given second (clock cycles per second). 1 Hz equals one cycle per second, so a 2 GHz frequency can handle 2 billion instructions for every second.

The higher the frequency the more operations can be done. However, today that is not the whole story. Modern CPUs have complex CPU extensions (SSE, AVX, AVX2 and AVX512) that allow the CPU to execute several numerical operations on a single clock step.

From another side, CPUs are now able to change the speed up to certain limits, raising and lowering the value if needed. Sometimes raising the CPU frequency of a multicore CPU means that some cores are disabled as result.

Another technique used often by gamers is overclocking. Overclocking, is when the frequency is altered beyond the manufacturer's official clock rate by user-generated means. In HPC this is often not applied as overclocking increases the chances of instability of the system.

### Cache

Cache is a high-speed momentary memory format assigned to the CPU to facilitate future retrieval of data and instructions before processing. It???s very similar to RAM in the sense that it acts as a temporary holding pen for data. However CPU's access this memory in chunks and the mapping to RAM is different.  

Contrary to RAM that are independent pieces of hardware, cache sits on the CPU itself, so the access times are significantly faster. The cache is an important portion of the production cost of a CPU, to the point where one of the differences between i3s, i5s, and i7s is basically the size of the cache memory.

There are actually several cache memories inside a CPU. They are called cache levels, or hierarchies, a bit like a pyramid: L1, L2, and L3. The lower the level the closer to the core.
{% comment %}
L1 is the fastest cache and the first port of call for a CPU hunting down data. In modern processors, two split compartments make up the L1 cache, one for data and one for instructions, and every core is assigned an exclusive portion of the L1 cache.

L2 is bigger than L1, and consequently slower due to the processor having to trawl through more data. L3, on the other hand, is shared among all the cores and offers more space, but is slower.
{% endcomment %}

From the HPC perspective for intensive numerical operations, the cache size is an important feature. Many CPU cycles are lost if you need to bring data all the time from the RAM or even worst from the Hard Drive. So having large amounts of cache improves the efficiency of HPC codes.


## Learn to read computer specifications

One of the central differences between one computer and another are the CPU, the chip or set of chips that control most of the numerical operations. When reading the specifications of a computer you need to pay attention to the amount of memory, if the drive is SSD or not, the presence of a dedicated GPU card and a number of factors that could or could not be relevant for the purpose of your computer. Have a look at the specifications of the CPU on your machine.

### Intel

If your machine uses Intel Processors, go to <https://ark.intel.com> and enter the model of CPU you have, Intel models are for example: "E5-2680 v3", "E5-2680 v3"

### AMD

If your machine uses AMD processors, go to <https://www.amd.com/en/products/specifications/processors> and check the details for your machine.


{% include links.md %}

