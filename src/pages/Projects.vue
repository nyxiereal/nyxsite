<template>
    <v-container class="bg-surface">
        <div class="py-8">
            <v-btn to="/" variant="text" prepend-icon="mdi-arrow-left" class="mb-4">
                Back to Home
            </v-btn>

            <h1 class="text-h1 text-md-h1 font-weight-bold mb-3 title-wrap"><span class="climate-font">Projects</span></h1>
            <p class="text-h6 text-medium-emphasis mb-6">List of projects I've built and maintain</p>

            <v-row dense>
                <v-col v-for="project in projects" :key="project.title" cols="12">
                    <v-card color="surface-container-high">
                        <v-card-text class="pa-6">
                            <v-row align="center">
                                <v-col cols="12" md="">
                                    <div class="d-flex align-center mb-2">
                                        <h2 class="text-h4 font-weight-bold title-wrap">{{ project.title }}</h2>
                                    </div>
                                    <p class="text-body-1 text-medium-emphasis mb-2">{{ project.description }}</p>

                                    <div class="d-flex flex-wrap ga-2 mb-2">
                                        <v-chip class="lang-chip" v-for="lang in project.languages" :key="lang.name" :color="lang.color"
                                            variant="elevated" size="small">
                                            <v-icon v-if="!lang.image" start :icon="lang.icon" />
                                            <svg v-else-if="lang.name === 'Dart'" xmlns="http://www.w3.org/2000/svg"
                                                height="15.4333px" viewBox="0 -960 960 960" width="15.4333px"
                                                class="lang-icon-svg">
                                                <path
                                                    d="M236-345 100-480l440-440h271L236-345ZM540-40 303-277l237-237h271L574-277 811-40H540Z" />
                                            </svg>
                                            <img v-else :src="lang.image" :alt="lang.name" class="lang-icon" />
                                            {{ lang.name }}
                                        </v-chip>
                                    </div>

                                    <div v-if="project.badges.length > 0" class="d-flex flex-wrap ga-2">
                                        <img v-for="(badge, index) in project.badges" :key="index" :src="badge"
                                            :alt="'Badge ' + index" />
                                    </div>
                                </v-col>

                                <v-col cols="12" md="auto">
                                    <div class="d-flex flex-column ga-2">
                                        <v-btn v-for="link in project.links" :key="link.text" :href="link.url"
                                            target="_blank" variant="flat" color="secondary-container"
                                            :prepend-icon="link.icon" block>
                                            {{ link.text }}
                                        </v-btn>
                                    </div>
                                </v-col>
                            </v-row>
                        </v-card-text>
                    </v-card>
                </v-col>
            </v-row>
        </div>
    </v-container>
</template>

<script setup lang="ts">
// Material 3 Projects page component

interface ProjectData {
    repo: string
    languages: string
    description: string
    counters?: string
    website?: string
}

interface ProcessedProject {
    title: string
    description: string
    languages: Array<{ name: string; color: string; icon: string; image?: string }>
    badges: string[]
    links: Array<{ text: string; url: string; icon: string }>
}

const projectsData: ProjectData[] = [
    {
        repo: 'MetrolistGroup/Metrolist',
        languages: 'kotlin',
        description: 'A YouTube Music client for Android, following Material 3 guidelines',
        counters: 'stars,downloads',
        website: 'https://metrolist.meowery.eu'
    },
    {
        repo: 'MetrolistGroup/metroserver',
        languages: 'go',
        description: 'A high performance Go WebSocket server for Metrolist\'s Listen Together feature',
        counters: 'stars'
    },
    {
        repo: 'nyxiereal/XToolBox',
        languages: 'dart',
        description: 'A Windows 10/11 optimization utility',
        counters: 'stars,downloads'
    },
    {
        repo: 'nyxiereal/ReVancedPacker',
        languages: 'python',
        description: 'A Windows utility for repacking applications using ReVanced [🪦]',
        counters: 'stars,downloads'
    },
    {
        repo: 'nyxiereal/docs',
        languages: 'typescript',
        description: 'Documentation for all my projects, alongside some other resources and notes',
        website: 'https://docs.meowery.eu'
    },
    {
        repo: 'nyxiereal/userfiles',
        languages: 'javascript,python',
        description: 'A collection of userscripts and userstyles I\'ve made',
        counters: 'stars',
        website: 'https://greasyfork.org/en/users/1444359-nyxiereal'
    },
    {
        repo: 'nyxiereal/AliucordPlugins',
        languages: 'kotlin',
        description: 'A collection of plugins I\'ve made for Aliucord',
        counters: 'stars'
    },
    {
        repo: 'nyxiereal/nFitness',
        languages: 'dart',
        description: 'An alternative application for the eFitness platform',
        counters: 'stars,downloads'
    },
    {
        repo: 'nyxiereal/pekky',
        languages: 'dart',
        description: 'An alternative application for the PEKA system',
        counters: 'stars,downloads'
    },
    {
        repo: 'Basalt',
        languages: 'dart',
        description: 'An alternative application for the eduVulcan system',
        website: 'https://docs.meowery.eu/projects/Basalt/Index.html'
    }
]

const languageConfig: Record<string, { color: string; icon: string; image?: string }> = {
    kotlin: { color: 'primary', icon: 'mdi-language-kotlin' },
    go: { color: 'secondary', icon: 'mdi-language-go' },
    dart: { color: 'tertiary', icon: 'mdi-code-braces', image: '/flutter.svg' },
    python: { color: 'primary', icon: 'mdi-language-python' },
    typescript: { color: 'secondary', icon: 'mdi-language-typescript' },
    javascript: { color: 'tertiary', icon: 'mdi-language-javascript' }
}

function processProjects(data: ProjectData[]): ProcessedProject[] {
    return data.map(project => {
        const hasSlash = project.repo.includes('/')
        const repoName = hasSlash ? project.repo.split('/')[1] : project.repo
        const title = repoName.charAt(0) + repoName.slice(1)

        // Process languages
        const languages = project.languages.split(',').map(lang => {
            const trimmedLang = lang.trim().toLowerCase()
            const config = languageConfig[trimmedLang] || { color: 'primary', icon: 'mdi-code-tags' }
            return {
                name: trimmedLang.charAt(0).toUpperCase() + trimmedLang.slice(1),
                color: config.color,
                icon: config.icon,
                image: config.image
            }
        })

        // Generate badges
        const badges: string[] = []
        if (project.counters) {
            const counters = project.counters.split(',').map(c => c.trim())
            if (hasSlash && counters.includes('stars')) {
                badges.push(`https://img.shields.io/github/stars/${project.repo}?style=flat-square&logo=github`)
            }
            if (hasSlash && counters.includes('downloads')) {
                badges.push(`https://img.shields.io/github/downloads/${project.repo}/total?style=flat-square&logo=github`)
            }
        }

        // Generate links
        const links: Array<{ text: string; url: string; icon: string }> = []
        if (project.website) {
            links.push({
                text: 'Visit Website',
                url: project.website,
                icon: 'mdi-web'
            })
        }
        if (hasSlash) {
            links.push({
                text: 'View on GitHub',
                url: `https://github.com/${project.repo}`,
                icon: 'mdi-github'
            })
        }

        return {
            title,
            description: project.description,
            languages,
            badges,
            links
        }
    })
}

const projects = processProjects(projectsData)
</script>

<style scoped>
/* Material 3 compliant styles */
.lang-icon {
    width: 24px;
    height: 24px;

    .lang-icon-svg {
        width: 24px;
        height: 24px;
        margin-right: 8px;
        fill: currentColor;
    }

    margin-right: 8px;
    object-fit: contain;
}

/* Prevent title overflow on mobile devices */
.title-wrap {
    word-wrap: break-word;
    overflow-wrap: break-word;
    hyphens: auto;
    max-width: 100%;
}
</style>
