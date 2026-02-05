<script>
    
</script>


<div>
    <div class="text-left mb-4 mt-8 sm:mt-12 md:mt-16 sm:mb-16 md:mb-20">
        <div class="text-2xl sm:text-3xl md:text-4xl font-bold mb-4 sm:mb-6">
            PyTorch JIT Compiler
        </div>

        <div class="space-y-6 sm:space-y-4 text-sm sm:text-md text-gray-300 light-mode:text-[#66615E] leading-relaxed">
            <span class="font-bold">[1/22/26]</span>
            It's been a few weeks of work (and travelling), but I'm here to report my current progress. Frankly, the past few weeks involved a lot of reading and learning on these topics: 
            <ul class="list-disc list-outside ml-5 [&>li::marker]:text-xl [&>li::marker]:text-white light-mode:[&>li::marker]:text-[#2d2a28]">
                <li><a href="https://docs.pytorch.org/assets/pytorch2-2.pdf" class="underline">PyTorch 2 (TorchDynamo/TorchInductor)</a>: this was a useful starting point as the paper discusses the implementation decisions behind TorchDynamo and its Graph Capture mechanism. This essentially helped me narrow down my design to use PyTorch's <a href="https://docs.pytorch.org/docs/stable/fx.html" class="underline">torch.fx</a> toolkit.</li>
                <li>JIT Compilers</li>
                <li><a href="https://www.eecs.harvard.edu/~htk/publication/2019-mapl-tillet-kung-cox.pdf" class="underline">Triton Compiler</a></li>
            </ul>

            A major development includes my Python frontend & Rust setup. This project is actually my 2nd time ever using Rust: for setup purposes, I familiarized myself with Cargo (Rust's package management system), and I'm getting the hang of the memory lifetime model that Rust provides. I also played around with Rust bindings for PyTorch (provided by <a href="https://github.com/PyO3/pyo3" class="underline">PyO3</a>) and 
            Rust bindings for MLIR (via <a href="https://github.com/mlir-rs/melior" class="underline">Melior</a>). What's next? I have to get my hands dirty with MLIR. I have been using the <a href="https://mlir.llvm.org/docs/Tutorials/Toy/" class="underline">Toy example</a> to learn implementation fundamentals for an MLIR-based compiler. 


            <figure class="my-8 text-center max-w-lg mx-auto">
                <img 
                    src="blog/figure1.png" 
                    alt="sopt API usage"
                    class="w-full h-auto rounded-lg shadow-lg"
                />
                <figcaption class="mt-3 text-sm text-gray-400 light-mode:text-gray-600 italic">
                    sopt API usage
                </figcaption>
            </figure>

            Above, I have a very simple 2-layer network defined using PyTorch. Similar to PyTorch, I utilize a compile() decorator under my own sopt library. Taking a step back from the technical side, I also wanted 
            to share how fascinating I found this step; I essentially built my own importable Python library that funnels into the binary for my Rust-based compiler! Many libraries that I use 
            on a daily basis follow some form of what I've just implemented here, which was eye-opening to me. 
            <br/>
            <br/>
            Anyway, during execution, sopt.compile() converts the torch.fx format into a list of related JSON objects that can easily be received by the Rust backend. I set up a class, PyNode, that encapsulates the important data fields from FXNodes. 
            <figure class="my-8 text-center max-w-lg mx-auto">
                <img 
                    src="blog/figure2.png" 
                    alt="sopt API usage"
                    class="w-full h-auto rounded-lg shadow-lg"
                />
                <figcaption class="mt-3 text-sm text-gray-400 light-mode:text-gray-600 italic">
                    sopt compiler receiver endpoint for sopt.compile()
                </figcaption>
            </figure>
            From this point, I am working on setting up my first Dialect/IR on the MLIR skeleton. I call it the "soptfx" dialect. The idea is to lower the PyNodes to operations in MLIR in order to make the data graph; since FX nodes come in 3 main flavors 
            (placeholders, callfunctions, and outputs), I handle this lowering separately for each case. My goal here is to output an accurate .mlir file in order to gauge the correctness of my current logic. 
        </div>

        <br>
        <br>
        <br>
        <br>


        <div class="space-y-6 sm:space-y-4 text-sm sm:text-md text-gray-300 light-mode:text-[#66615E] leading-relaxed">
            <span class="font-bold">[1/4/26]</span>
            So, I've been working on this project for the past few weeks. Up until yesterday, I spent most of my time reading up on basic theory behind 
            ML/DL compilers. I plan to add much more to this blog to help me reinforce whatever I learn and to log my journey into this field (incase it inspires anyone). 
            
            <br>
            <br>

            I'll get started with some preliminaries: my related background up to this point involves GPU programming (CUDA), systems programming, ML systems, and a bit of compiler construction (LLVM). 
            All of these were picked up through courses at my school, <span class="text-blue-700">U</span><span class="text-orange-500">I</span><span class="text-blue-700">U</span><span class="text-orange-500">C</span>.
            Over the past few weeks, I read up on a few more technologies: 
            <ul class="list-disc list-outside ml-5 [&>li::marker]:text-xl [&>li::marker]:text-white light-mode:[&>li::marker]:text-[#2d2a28]">
                <li>MLIR</li>
                <li>TVM</li>
                <li>Triton</li>
                <li>TensorRT</li>
                <li>nvFuser</li>
            </ul>

            Now, I somewhat understand where these technologies fit into a compiler stack.
            MLIR serves as compiler infrastructure, the "skeleton" of the compiler we build; 
            TVM is a fullstack compiler that emphasizes loop-level/tiling optimizations and code generation for heterogenous devices;
            Triton is a language/IR/JIT compiler (used by PyTorch 2.0) that helps write extensible GPU kernels;
            TensorRT is an inference engine that optimizes models for NVIDIA GPUs;
            and nvFuser is a "Fusion Code Generator" that generates code optimized for NVIDIA GPUs.

            <br>
            <br>

            I will revisit these definitions the more I explore :) 

            <br>
            <br>

            Now, I have finalized my design that I want to use for this project. I call it "<a href="https://github.com/tkhdse/soptRT" class="underline font-bold">soptRT</a>" (still need to think of a better name).

            I've broken this project down into 2 phases:
            <ul class="list-disc list-outside ml-5 [&>li::marker]:text-xl [&>li::marker]:text-white light-mode:[&>li::marker]:text-[#2d2a28]">
                <li><span class="font-bold">Phase I</span>: To better learn ML optimizations at a low-level, I want to introduce my own compile() trigger in PyTorch that calls a Rust-based compiler that is built on MLIR. This compiler will trigger optimization passes (Fusion, Quantization, Memory Mapping, etc) and funnel into an existing backend (Triton/TVM).</li>
                <li><span class="font-bold">Phase II</span>: Next, I want to design my own kernel generator. After reading a little, I realized that code generation is a very interesting problem that currently uses several solutions to implement. TVM uses a paradigm called ML for ML, while engineers handcraft kernels for NVIDIA's cuDNN. Details for this part are TBD and will require me to read a bit more. </li>
            </ul>
            
            Great! Now that the plan is out of the way, I will update this page over time with challenges I run into. For now, I am working on creating the "bridge" from my own PyTorch compile() and my Rust backend with MLIR. 
            
            <br>
            <br>

            Stay tuned!            

            <!-- <span class="font-bold">Why am I doing this?</span> I recently took a course in compilers (CS426 at UIUC) and found it to be super interesting!
            The course was taught by one of the inventors of LLVM which opened up lots of perspective in design philosophy. 
            
            Anyway, I've had the opportunity to interview for a few compiler roles before taking this course.
            
            Thankfully, I knew a little bit about programming GPUs/systems (from CS483 at UIUC, another great course) and didn't do horrible, but there was definitely a knowledge gap. 
            
            <br>
            <br>

            Overtime, I became curious on where the tech stacks I learned about in these interviews come into play in the software world.  -->
            

        </div>

        <br/>
        <br/>
        <br/>
        <br/>

        <div class="space-y-6 sm:space-y-4 text-sm sm:text-md text-gray-300 light-mode:text-[#66615E] leading-relaxed">
            <span class="font-bold">Cool links:</span> I'd also like to highlight some cool links I found throughout this project. There are a lot of cool startups and innovations in this field of ML compilers that I want to further explore:

            
            <ul class="list-disc list-outside ml-5 [&>li::marker]:text-xl [&>li::marker]:text-white light-mode:[&>li::marker]:text-[#2d2a28]">
                <li><a href="https://docs.nvidia.com/cuda/tile-ir/latest/index.html#" class="underline">Tile IR</a>: NVIDIA released this somewhat recently. This is a "low-level tile virtual machine" allowing a developer to work in terms of tiles.</li>
                <li><a href="https://xania.org/AoCO2025-archive" class="underline">Compiler Optimization Advent Calendar</a>: I saw this on LinkedIn; as the name suggests, the author goes over some interesting compiler designs.</li>
                <li><a href="https://www.modular.com/" class="underline">Modular</a>: really cool company led by Chris Lattner who I've been following for a while. The language seems very well-designed and I am curious to see how its compiler works.</li>
                <!-- <li><a href="https://xania.org/AoCO2025-archive" class="underline">Compiler Optimization Advent Calendar</a>: I saw this on LinkedIn; as the name suggests, the author goes over some interesting compiler designs</li> -->
            </ul>
        </div>
    </div>

</div>
 <!-- flex flex-col md:flex-row items-center gap-6 sm:gap-8 md:gap-12 -->