<script>
    import Nav from '../lib/ui/Nav.svelte'
    import profilePic from '$lib/assets/profile.png';
    
    const experiences = [
        {
            type: 'work',
            title: 'Senior Software Engineer',
            organization: 'Tech Company Inc.',
            date: '2023 - Present',
            description: 'Led development of key features and mentored junior developers.',
            skills: ['React', 'Node.js', 'AWS']
        },
        {
            type: 'work',
            title: 'Software Engineer',
            organization: 'Startup XYZ',
            date: '2021 - 2023',
            description: 'Built scalable backend services and improved system performance.',
            skills: ['Python', 'PostgreSQL', 'Docker']
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
    <div class="relative select-none w-[60%] h-full mx-auto pb-24">
        <Nav></Nav>
        
        <!-- Intro Section with Profile Picture -->
        <div class="mt-16 mb-20 flex items-center gap-12">
            <!-- Text Content -->
            <div class="flex-1">
                <h1 class="text-5xl font-bold mb-6">Hi, I'm Tanish 👋</h1>
                <p class="text-xl text-gray-300 leading-relaxed">
                    I'm a software engineer passionate about building elegant solutions to complex problems. 
                    I love working with modern web technologies and creating exceptional user experiences.
                </p>
            </div>
            
            <!-- Profile Picture -->
            <div class="flex-shrink-0">
                <img 
                    src={profilePic} 
                    alt="Tanish Khadse" 
                    class="w-48 h-48 rounded-full object-cover shadow-2xl"
                />
            </div>
        </div>
        
        <!-- Timeline Container -->
        <div class="relative">
            <!-- Section Title -->
            <!-- <h2 class="text-3xl font-bold mb-12">My Journey</h2> -->
            
            <!-- Vertical Line -->
            <div class="absolute left-0 top-0 bottom-0 w-[2px] bg-white"></div>
            
            <!-- Timeline Items -->
            <div class="space-y-12 ml-8">
                {#each experiences as exp, i}
                    <div class="relative">
                        <!-- Timeline Dot -->
                        <div class="absolute -left-[33px] top-2 w-4 h-4 bg-white rounded-full border-4 border-[#1e1e1e]"></div>
                        
                        <!-- Content Card -->
                        <div class="transition-all hover:translate-x-2 duration-300">
                            <!-- Type Badge -->
                            <div class="mb-2">
                                <span class="text-xs uppercase tracking-wider px-2 py-1 rounded {exp.type === 'work' ? 'bg-blue-500/20 text-blue-300' : 'bg-green-500/20 text-green-300'}">
                                    {exp.type}
                                </span>
                            </div>
                            
                            <!-- Title and Organization -->
                            <h3 class="text-2xl font-bold mb-1">{exp.title}</h3>
                            <p class="text-gray-400 mb-1">{exp.organization}</p>
                            <p class="text-sm text-gray-500 mb-3">{exp.date}</p>
                            
                            <!-- Description -->
                            <p class="text-gray-300 mb-4 leading-relaxed">{exp.description}</p>
                            
                            <!-- Skills -->
                            <div class="flex flex-wrap gap-2">
                                {#each exp.skills as skill}
                                    <span class="text-xs px-3 py-1 bg-white/10 rounded-full border border-white/20 hover:bg-white/20 transition">
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