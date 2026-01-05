<script>
    
</script>


<div>
    <div class="text-left mb-4 mt-8 sm:mt-12 md:mt-16 sm:mb-16 md:mb-20">
        <div class="text-2xl sm:text-3xl md:text-4xl font-bold mb-4 sm:mb-6">
            PyTorch JIT Compiler
        </div>

        <div class="space-y-6 sm:space-y-4 text-sm sm:text-md text-gray-300 light-mode:text-[#66615E] leading-relaxed">
            <span class="font-bold">[1/4/26]</span>
            So, I've been working on this project for the past few weeks. Up until yesterday, I spent most of my time reading up on basic theory behind 
            ML/DL compilers. I plan to add much more to this blog to help me reinforce whatever I learn and to log my journey into this field (incase it inspires anyone). 
            
            <br>
            <br>

            I'll get started with some preliminaries: my related background up to this point involves GPU programming (CUDA), systems programming, ML systems, and a bit of compiler construction (LLVM). 
            All of these were picked up through courses at my school, <span class="text-blue-700">U</span><span class="text-orange-500">I</span><span class="text-blue-700">U</span><span class="text-orange-500">C</span>.
            Over the past few weeks, I researched a few more technologies: 
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
    </div>

</div>
 <!-- flex flex-col md:flex-row items-center gap-6 sm:gap-8 md:gap-12 -->