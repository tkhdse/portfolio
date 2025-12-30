<script>
    import Nav from '../lib/ui/Nav.svelte'
    import profilePic from '$lib/assets/profile.png';
</script>

<div class="w-full h-full text-white dark:text-white light-mode:text-[#1e1e1e] font-mono transition-colors duration-300">
    <!-- Responsive container: full width with padding on mobile, 60% width on desktop -->
    <div class="relative select-none w-full px-6 sm:px-8 md:w-[80%] lg:w-[70%] xl:w-[60%] h-full mx-auto pb-16 sm:pb-24">
        <Nav></Nav>
        
        <!-- Intro Section with Profile Picture -->
        <!-- Stack vertically on mobile, horizontal on md+ screens -->
        <div class="mt-8 sm:mt-12 md:mt-16 mb-12 sm:mb-16 md:mb-20 flex flex-col md:flex-row items-center gap-6 sm:gap-8 md:gap-12">
            <!-- Profile Picture - appears first on mobile -->
            <div class="shrink-0 order-1 md:order-2">
                <img 
                    src={profilePic} 
                    alt="Tanish Khadse" 
                    class="w-32 h-32 sm:w-40 sm:h-40 md:w-48 md:h-48 rounded-full object-cover shadow-2xl"
                />
            </div>
            
        <!-- Text Content -->
        <div class="flex-1 order-2 md:order-1 text-left">
            <h1 class="text-2xl sm:text-3xl md:text-4xl font-bold mb-4 sm:mb-6">Hi, I'm Tanish 👋</h1>
            <div class="space-y-6 sm:space-y-4 text-sm sm:text-md text-gray-300 light-mode:text-[#66615E] leading-relaxed">
                <p>I love challenges in distributed systems and low-level programming. Also have a drive for impact.</p>
                <ul class="list-disc list-outside ml-5 [&>li::marker]:text-xl [&>li::marker]:text-white light-mode:[&>li::marker]:text-[#2d2a28]">
                    <li>BS-MCS degree at UIUC.</li>
                    <li>Got into GPU programming.</li>
                    <li>Going pro in ping pong one day.</li>
                    <li>Happy to chat :) </li>
                    <ul class="list-[circle] list-outside ml-6 mt-2 text-[0.75rem] text-gray-300 light-mode:text-[#5a5654]">
                        <li>tkhadse2 [at] illinois [dot] edu</li>
                    </ul>
                </ul>
            </div>
        </div>
            
        </div>
        <!-- Divider -->
        <div class="w-full h-px bg-white light-mode:bg-[#5a5654] mb-12 sm:mb-16"></div>

<!-- Work Experience -->
<div class="mb-12 sm:mb-16">
    <h2 class="text-2xl sm:text-3xl font-bold mb-6 sm:mb-8">Work Experience</h2>
    <ul class="list-disc list-outside ml-5 space-y-4 text-sm sm:text-base text-gray-300 light-mode:text-[#5a5654]">
        <li>
            <div class="flex flex-col sm:flex-row sm:justify-between sm:items-baseline gap-1 sm:gap-4">
                <span class="font-semibold text-white light-mode:text-[#2d2a28] text-lg sm:text-xl">Salesforce | <span class="text-gray-300 light-mode:text-[#5a5654] font-light text-sm">Software Engineering Intern</span></span>
                <span class="text-gray-400 light-mode:text-[#5a5654] text-xs sm:text-sm whitespace-nowrap">May 2025 - Aug 2025</span>
            </div>
            <ul class="list-[circle] list-outside ml-6 mt-2 text-sm text-gray-300 light-mode:text-[#5a5654]">
                <li>high availablility & real-time translation</li>
            </ul>
        </li>
        <li>
            <div class="flex flex-col sm:flex-row sm:justify-between sm:items-baseline gap-1 sm:gap-4">
                <span class="font-semibold text-white light-mode:text-[#2d2a28] text-lg sm:text-xl">Nightshift | <span class="text-gray-300 light-mode:text-[#5a5654] font-light text-sm">Co-founder/CTO</span></span>
                <span class="text-gray-400 light-mode:text-[#5a5654] text-xs sm:text-sm whitespace-nowrap">Jan 2025 - present</span>
            </div>
            <ul class="list-[circle] list-outside ml-6 mt-2 text-sm text-gray-300 light-mode:text-[#5a5654]">
                <li>voice AI agents for hotel automation</li>
            </ul>
        </li>
        <li>
            <div class="flex flex-col sm:flex-row sm:justify-between sm:items-baseline gap-1 sm:gap-4">
                <span class="font-semibold text-white light-mode:text-[#2d2a28] text-lg sm:text-xl">Yahoo | <span class="text-gray-300 light-mode:text-[#5a5654] font-light text-sm">Software Engineering Intern</span></span>
                <span class="text-gray-400 light-mode:text-[#5a5654] text-xs sm:text-sm whitespace-nowrap">Jun 2024 - Aug 2024</span>
            </div>
            <ul class="list-[circle] list-outside ml-6 mt-2 text-sm text-gray-300 light-mode:text-[#5a5654]">
                <li>data pipeline observability</li>
            </ul>
        </li>
        <li>
            <div class="flex flex-col sm:flex-row sm:justify-between sm:items-baseline gap-1 sm:gap-4">
                <span class="font-semibold text-white light-mode:text-[#2d2a28] text-lg sm:text-xl">ML Research @ UIUC</span>
                <span class="text-gray-400 light-mode:text-[#5a5654] text-xs sm:text-sm whitespace-nowrap">Oct 2023 - March 2024</span>
            </div>
            <ul class="list-[circle] list-outside ml-6 mt-2 text-sm text-gray-300 light-mode:text-[#5a5654]">
                <li>model speedup with CUDA & long-sequence inference</li>
            </ul>
        </li>
    </ul>
</div>


<!-- Projects -->
<div class="mb-12 sm:mb-16">
    <h2 class="text-2xl sm:text-3xl font-bold mb-6 sm:mb-8">Projects</h2>
    <ul class="list-disc list-outside ml-5 space-y-4 text-sm sm:text-base text-gray-300 light-mode:text-[#5a5654]">
        <li>
            <div class="flex justify-between items-baseline gap-4">
                <div class="flex items-baseline gap-3 flex-wrap">
                    <span class="text-white light-mode:text-[#2d2a28] text-lg">LLVM-based Compiler with Optimizations</span>
                    <span class="flex gap-2 text-xs">
                        <a href="#" class="text-gray-400 light-mode:text-[#5a5654] hover:text-white light-mode:hover:text-[#2d2a28] transition border-b border-gray-400 light-mode:border-[#5a5654] hover:border-white light-mode:hover:border-[#2d2a28]">[blog]</a>
                        <!-- <a href="#" class="text-gray-400 hover:text-white transition border-b border-gray-400 hover:border-white">[github]</a> -->
                    </span>
                </div>
                <span class="text-gray-400 light-mode:text-[#5a5654] whitespace-nowrap text-sm">Fall 2025 - present</span>
            </div>
        </li>
        <li>
            <div class="flex justify-between items-baseline gap-4">
                <div class="flex items-baseline gap-3 flex-wrap">
                    <span class="text-white light-mode:text-[#2d2a28] text-lg">Hierarchical HLM (HiLM) </span>
                    <span class="flex gap-2 text-xs">
                        <!-- <a href="#" class="text-gray-400 hover:text-white transition border-b border-gray-400 hover:border-white">[blog]</a> -->
                        <a href="https://github.com/gohinv/HiLM" class="text-gray-400 light-mode:text-[#5a5654] hover:text-white light-mode:hover:text-[#2d2a28] transition border-b border-gray-400 light-mode:border-[#5a5654] hover:border-white light-mode:hover:border-[#2d2a28]">[github]</a>
                    </span>
                </div>
                <span class="text-gray-400 light-mode:text-[#5a5654] whitespace-nowrap text-sm">Fall 2025 - present</span>
            </div>
        </li>
        <li>
            <div class="flex justify-between items-baseline gap-4">
                <div class="flex items-baseline gap-3 flex-wrap">
                    <span class="text-white light-mode:text-[#2d2a28] text-lg">Query Reorder Buffer (QRB) for Efficient RAG </span>
                    <span class="flex gap-2 text-xs">
                        <a href="https://github.com/tkhdse/QRB" class="text-gray-400 light-mode:text-[#5a5654] hover:text-white light-mode:hover:text-[#2d2a28] transition border-b border-gray-400 light-mode:border-[#5a5654] hover:border-white light-mode:hover:border-[#2d2a28]">[github]</a>
                    </span>
                </div>
                <span class="text-gray-400 light-mode:text-[#5a5654] whitespace-nowrap text-sm">Fall 2025</span>
            </div>
        </li>
        <li>
            <div class="flex justify-between items-baseline gap-4">
                <div class="flex items-baseline gap-3 flex-wrap">
                    <span class="text-white light-mode:text-[#2d2a28] text-lg">Transport Protocol</span>
                    <span class="flex gap-2 text-xs">
                        <!-- <a href="#" class="text-gray-400 hover:text-white transition border-b border-gray-400 hover:border-white">[github]</a> -->
                    </span>
                </div>
                <span class="text-gray-400 light-mode:text-[#5a5654] whitespace-nowrap text-sm">Fall 2024</span>
            </div>
        </li>
        <li>
            <div class="flex justify-between items-baseline gap-4">
                <div class="flex items-baseline gap-3 flex-wrap">
                    <span class="text-white light-mode:text-[#2d2a28] text-lg">Linux Kernel Modules</span>
                    <span class="flex gap-2 text-xs">
                        <!-- <a href="#" class="text-gray-400 hover:text-white transition border-b border-gray-400 hover:border-white">[github]</a> -->
                    </span>
                </div>
                <span class="text-gray-400 light-mode:text-[#5a5654] whitespace-nowrap text-sm">Fall 2024</span>
            </div>
        </li>
        <li>
            <div class="flex justify-between items-baseline gap-4">
                <div class="flex items-baseline gap-3 flex-wrap">
                    <span class="text-white light-mode:text-[#2d2a28] text-lg">Autonomous F1-Tenth Vehicle</span>
                    <span class="flex gap-2 text-xs">
                        <a href="https://github.com/gohinv/f1tenth-project" class="text-gray-400 light-mode:text-[#5a5654] hover:text-white light-mode:hover:text-[#2d2a28] transition border-b border-gray-400 light-mode:border-[#5a5654] hover:border-white light-mode:hover:border-[#2d2a28]">[github]</a>
                    </span>
                </div>
                <span class="text-gray-400 light-mode:text-[#5a5654] whitespace-nowrap text-sm">Fall 2024</span>
            </div>
        </li>
        <li>
            <div class="flex justify-between items-baseline gap-4">
                <div class="flex items-baseline gap-3 flex-wrap">
                    <span class="text-white light-mode:text-[#2d2a28] text-lg">Raft</span>
                    <span class="flex gap-2 text-xs">
                        <!-- <a href="#" class="text-gray-400 hover:text-white transition border-b border-gray-400 hover:border-white">[github]</a> -->
                    </span>
                </div>
                <span class="text-gray-400 light-mode:text-[#5a5654] whitespace-nowrap text-sm">Spring 2024</span>
            </div>
        </li>
        <li>
            <div class="flex justify-between items-baseline gap-4">
                <div class="flex items-baseline gap-3 flex-wrap">
                    <span class="text-white light-mode:text-[#2d2a28] text-lg">CUDA-Accelerated Convolutional Neural Network</span>
                    <span class="flex gap-2 text-xs">
                        <!-- <a href="#" class="text-gray-400 hover:text-white transition border-b border-gray-400 hover:border-white">github</a> -->
                    </span>
                </div>
                <span class="text-gray-400 light-mode:text-[#5a5654] whitespace-nowrap text-sm">Fall 2023</span>
            </div>
        </li>
    </ul>
</div>
    </div>
</div>