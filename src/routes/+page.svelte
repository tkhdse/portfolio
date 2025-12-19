<script>
    import Nav from '../lib/ui/Nav.svelte'
    import profilePic from '$lib/assets/profile.png';
    
    const experiences = [
        {
            type: 'work',
            title: 'Software Engineering Intern',
            organization: 'Salesforce',
            date: 'May 2025 - Aug 2025',
            description: 'Led development of key features and mentored junior developers.',
            skills: ['React', 'Node.js', 'Redis', 'AWS', 'PostgreSQL']
        },
        {
            type: 'work',
            title: 'Co-founder & CTO',
            organization: 'Nightshift',
            date: 'Jan 2025 - present',
            description: 'Built scalable backend services and improved system performance.',
            skills: ['React', 'Python', 'LiveKit', 'Twilio', 'Redis', 'Langchain', 'Docker', 'GCP', 'Firestore']
        },
        {
            type: 'work',
            title: 'Software Engineering Intern',
            organization: 'Yahoo',
            date: 'June 2024 - Aug 2024',
            description: 'Led development of key features and mentored junior developers.',
            skills: ['Nuxt', 'Vue', 'Node.js', 'Python', 'Firestore', 'GCP', 'GKE', 'Terraform']
        },
        {
            type: 'work',
            title: 'Software Developer',
            organization: 'Hack4Impact',
            date: 'Jan 2024 - Jan 2025',
            description: 'Led development of key features and mentored junior developers.',
            skills: ['React', 'PostgreSQL', 'Supabase']
        },
        {
            type: 'work',
            title: 'Machine Learning Research Intern',
            organization: 'UIUC',
            date: 'Oct 2023 - Mar 2024',
            description: 'Led development of key features and mentored junior developers.',
            skills: ['C++', 'CUDA', 'Python', 'PyTorch']
        },
        {
            type: 'project',
            title: 'E-Commerce Platform',
            organization: 'Personal Project',
            date: '2023',
            description: 'Full-stack e-commerce solution with payment integration.',
            skills: ['Svelte', 'Firebase', 'Stripe']
        },
        {
            type: 'project',
            title: 'AI Chat Application',
            organization: 'Hackathon Winner',
            date: '2022',
            description: 'Real-time chat application with AI-powered responses.',
            skills: ['WebSocket', 'OpenAI', 'Redis']
        }
    ];
</script>

<div class="w-full h-full text-white font-mono">
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
            <div class="flex-1 order-2 md:order-1 text-center md:text-left">
                <h1 class="text-2xl sm:text-3xl md:text-4xl font-bold mb-4 sm:mb-6">Hi, I'm Tanish 👋</h1>
                <div class="flex-col space-y-3 sm:space-y-4 text-sm sm:text-md text-gray-300 leading-relaxed">
                    <p>I'm pursuing my BS-MCS degree at UIUC and was previously at Salesforce, Yahoo, and my startup, Nightshift. I'm a passionate engineer focused on building robust, high-performance systems from the metal up through the cloud.</p>
                    <p>I love work involving C++, Go, CUDA, low-level systems, distributed systems, and compilers.</p>
                    <p>If you are looking for an engineer with a strong foundation in systems and a drive for high performance, please feel free to reach out!</p>
                </div>
            </div>
        </div>
        
        <!-- Timeline Container -->
        <div class="relative">
                        
            <!-- Vertical Line -->
            <div class="absolute left-0 top-0 bottom-0 w-[2px] bg-white"></div>
            
            <!-- Timeline Items -->
            <div class="space-y-8 sm:space-y-10 md:space-y-12 ml-6 sm:ml-8">
                {#each experiences as exp, i}
                    <div class="relative">
                        <!-- Timeline Dot -->
                        <div class="absolute -left-[25px] sm:-left-[33px] top-2 w-3 h-3 sm:w-4 sm:h-4 bg-white rounded-full border-2 sm:border-4 border-[#1e1e1e]"></div>
                        
                        <!-- Content Card -->
                        <div>
                            <!-- Type Badge -->
                            <div class="mb-2">
                                <span class="text-xs uppercase tracking-wider px-2 py-1 rounded {exp.type === 'work' ? 'bg-blue-500/20 text-blue-300' : 'bg-green-500/20 text-green-300'}">
                                    {exp.type}
                                </span>
                            </div>
                            
                            <!-- Title and Organization -->
                            <h3 class="text-lg sm:text-xl md:text-2xl font-bold mb-1">{exp.title}</h3>
                            <p class="text-sm sm:text-base text-gray-400 mb-1">{exp.organization}</p>
                            <p class="text-xs sm:text-sm text-gray-500 mb-3">{exp.date}</p>
                            
                            <!-- Description -->
                            <p class="text-sm sm:text-base text-gray-300 mb-4 leading-relaxed">{exp.description}</p>
                            
                            <!-- Skills -->
                            <div class="flex flex-wrap gap-2">
                                {#each exp.skills as skill}
                                    <span class="text-xs px-2 sm:px-3 py-1 bg-white/10 rounded-full border border-white/20 hover:bg-white/20 transition">
                                        {skill}
                                    </span>
                                {/each}
                            </div>
                        </div>
                    </div>
                {/each}
            </div>
        </div>
    </div>
</div>