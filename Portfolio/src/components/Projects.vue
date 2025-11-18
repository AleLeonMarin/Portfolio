<template>
    <section id="projects" class="projects">
        <div class="container">
            <SectionHeader title="Featured projects" />

            <!-- Category filters -->
            <div class="filters" role="tablist" aria-label="Project categories">
                <button
                    v-for="cat in ['all', ...categories]"
                    :key="cat"
                    :class="['filter', { active: selectedCategory === cat }]"
                    @click="selectedCategory = cat"
                    role="tab"
                    :aria-selected="selectedCategory === cat"
                >
                    {{ formatLabel(cat) }}
                </button>
            </div>

            <div class="grid">
                <ProjectCard
                  v-for="(p, i) in filtered"
                  :key="i"
                  :title="p.title"
                  :description="p.description"
                  :url="p.url"
                  :image="p.image"
                  :tags="p.tags"
                  :category="p.category"
                  :previewScale="0.5"
                />
            </div>
        </div>
    </section>
</template>

<script setup>
import { computed, ref } from 'vue'
import SectionHeader from './SectionHeader.vue'
import ProjectCard from './ProjectCard.vue'

// Helper to resolve public assets with base path
const getImageUrl = (path) => path ? `${import.meta.env.BASE_URL}${path.replace(/^\//, '')}` : ''

// Edit this array to manage your projects
const projects = [
    {
        title: 'VP Planillas',
        description: 'Modern web app nominee management system for Cafeteria y Vivero Verde Pradera',
        url: '',
        image: getImageUrl('/VP.png'),
        tags: ['React', 'Next.js', 'Typescript', 'Tailwind', 'Express.js', 'PostgreSQL'],
        category: 'web',
    },
    {
        title: 'Pequeños Exploradores de Costa Rica',
        description: 'A virtual Museum for Kids to explore Costa Rica\'s history',
        url: 'https://exploradorescr.vercel.app/',
        image: '',
        tags: ['Next.js', 'Tailwind'],
        category: 'web',
    },
    {
        title: 'Park Xpress System',
        description: 'A modern web app for managing parking lots with AI integration',
        url: 'https://parkxpress.vercel.app/',
        image: '',
        tags: ['Next.js', 'PostgreSQL', 'Prisma', 'Tailwind', 'AI', 'Python', 'Docker', 'FastAPI'],
        category: 'web',
    },
    {
        title: 'Parqueo Parroquial San Marcos de Tarrazú',
        description: 'An app for managing the parking lot of San Marcos Church in Tarrazú, Costa Rica',
        url: '',
        image: getImageUrl('/San-Marcos.jpg'),
        tags: ['Java', 'CSS', 'Oracle DBMS'],
        category: 'desktop',
    },
    {
        title: 'Sigece-UNA',
        description: 'A comprehensive academic enterprise management system for Universidad Nacional de Costa Rica',
        url: '',
        image: getImageUrl('/Sigece.png'),
        tags: ['Java', 'REST API', 'CSS', 'Oracle DBMS'],
        category: 'desktop',
    },
    {
        title: 'UNA-KIDS',
        description: 'An educational platform for kids to learn about saving money through a imaginary bank',
        url: '',
        image: getImageUrl('/UNA-KIDS.png'),
        tags: ['Java', 'CSS'],
        category: 'desktop',
    },
    {
        title: 'Git Documentation',
        description: 'A complete guide to using Git version control system, written in English',
        url: '',
        image: getImageUrl('/git.png'),
        tags: ['LaTeX', 'Git'],
        category: 'documentation',
    },
    {
        title: 'Docker Documentation',
        description: 'A comprehensive guide to Docker containerization platform, written in English',
        url: '',
        image: getImageUrl('/docker.png'),
        tags: ['LaTeX', 'Docker'],
        category: 'documentation',
    },
    {
        title: 'JPA Documentation',
        description: 'A JPA documentation used for comprehending Java Persistence API concepts and usage',
        url: '',
        image: getImageUrl('/jpa.svg'),
        tags: ['LaTeX', 'Java', 'Oracle DBMS'],
        category: 'documentation',
    }
]

const categories = computed(() => [
    ...new Set(projects.map((p) => p.category).filter(Boolean)),
])

const selectedCategory = ref('all')

const filtered = computed(() =>
    selectedCategory.value === 'all'
        ? projects
        : projects.filter((p) => p.category === selectedCategory.value)
)

const formatLabel = (v) =>
    v === 'all' ? 'All' : v.replace(/-/g, ' ').replace(/\b\w/g, (c) => c.toUpperCase())
</script>

<style scoped>
.projects {
    background: #0a0a0a;
    padding: 6rem 0;
}

.filters {
    display: flex;
    flex-wrap: wrap;
    gap: 0.6rem;
    margin: 1rem 0 1.5rem;
}

.filter {
    border: 1px solid #0f2c2a;
    background: #071a19;
    color: #00d4aa;
    padding: 0.45rem 0.8rem;
    border-radius: 999px;
    font-size: 0.9rem;
    cursor: pointer;
    transition: all 0.2s ease;
}

.filter.active {
    background: #00d4aa;
    color: #0a0a0a;
    font-weight: 600;
}

.filter:hover {
    border-color: #00d4aa;
    transform: translateY(-1px);
}

.grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 2rem;
    margin-top: 2rem;
}

@media (min-width: 900px) {
    .grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
        gap: 2.25rem;
    }
}
</style>
