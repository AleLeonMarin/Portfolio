<template>
    <!-- About me -->
    <section class="about" id="about">
        <div class="container">
            <SectionHeader title="About me" />

            <div class="features-grid">
                <FeatureItem v-for="(f, i) in features" :key="i" :title="f.title" :description="f.description" />
            </div>

            <div class="bottom-grid">
                <div>
                    <SectionHeader title="Skills" />
                    <SkillChips :skills="skills" />
                </div>
                <div>
                    <SectionHeader title="Experience" />
                    <ExperienceBlock :text="experienceText" />
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import SectionHeader from './SectionHeader.vue'
import FeatureItem from './FeatureItem.vue'
import SkillChips from './SkillChips.vue'
import ExperienceBlock from './ExperienceBlock.vue'

const features = [
    {
        title: 'Design',
        description:
            'I craft intuitive and beautiful interfaces, focused on user experience',
    },
    {
        title: 'Development',
        description:
            'I build fast, responsive websites using the latest technologies',
    },
    {
        title: 'Innovation',
        description:
            'Always looking for new ways to solve design challenges',
    },
]

const skills = ['HTML', 'CSS', 'JavaScript', 'TypeScript', 'Java', 'React', 'Vue', 'Node.js', 'Git', 'Next.js', 'Tailwind CSS', 'Oracle DBMS', 'PostgreSQL', 'Firebase', 'REST APIs', 'Soap APIs', 'Docker', 'Java', 'Kotlin', 'LaTeX', 'Linux', 'VSCode', 'Postman']

const experienceText =
    'Freelance Software Engineer — 1 year delivering client apps; 4 years at Universidad Nacional de Costa Rica building diverse academic and personal projects. Passionate about crafting user-focused, performant solutions with modern tools and languages.'
</script>

<style scoped>
/* Hero */
.hero {
    width: 100%;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #0a0a0a;
    padding: 0;
    margin: 0;
}

.hero-content {
    text-align: center;
    max-width: 900px;
}

.hero-title {
    font-size: 3.5rem;
    font-weight: 700;
    color: white;
    margin-bottom: 1.5rem;
    line-height: 1.2;
}

.name {
    color: #00d4aa;
}

.hero-subtitle {
    font-size: 1.25rem;
    color: #9ca3af;
    margin-bottom: 3rem;
    line-height: 1.6;
    font-weight: 400;
}

.hero-buttons {
    display: flex;
    gap: 1.5rem;
    justify-content: center;
    align-items: center;
}

.btn {
    padding: 1rem 2rem;
    font-size: 1rem;
    font-weight: 500;
    border-radius: 8px;
    cursor: pointer;
    transition: all 0.3s ease;
    border: 2px solid transparent;
}

.btn-primary {
    background-color: #00d4aa;
    color: #0a0a0a;
    border-color: #00d4aa;
}

.btn-primary:hover {
    background-color: #00b894;
    border-color: #00b894;
    transform: translateY(-2px);
}

.btn-secondary {
    background-color: transparent;
    color: white;
    border-color: #333;
}

.btn-secondary:hover {
    border-color: #00d4aa;
    color: #00d4aa;
    transform: translateY(-2px);
}

/* Sobre mí */
.about {
    background-color: #0a0a0a;
    /* Center vertically accounting for fixed header (~80px) */
    min-height: calc(100vh - 80px);
    display: flex;
    align-items: center;
    padding: 3rem 0;
    scroll-margin-top: 80px;
    /* anchor offset under fixed header */
}

/* Center inner pieces horizontally */
.about :deep(.section-header) {
    align-items: center;
    text-align: center;
}

/* Use global .container from assets/main.css for centering */

.features-grid {
    display: grid;
    grid-template-columns: repeat(1, minmax(0, 1fr));
    gap: 2rem;
    margin: 3rem 0 4rem;
    justify-items: center;
    text-align: center;
}

.bottom-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 3rem;
    justify-items: center;
    text-align: center;
}

/* Center content inside child components */
.about :deep(.feature-title),
.about :deep(.feature-text),
.about :deep(.experience-title),
.about :deep(.experience-text) {
    text-align: center;
}

.about :deep(.chips) {
    justify-content: center;
}

@media (min-width: 900px) {
    .features-grid {
        grid-template-columns: repeat(3, minmax(0, 1fr));
        gap: 3rem;
    }

    .bottom-grid {
        grid-template-columns: 1.5fr 1fr;
        gap: 4rem;
    }
}
</style>
