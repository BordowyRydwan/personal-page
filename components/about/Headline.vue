<template>
    <section class="about-me">
        <div class="about-me__container">
            <img src="/img/personal-photo.png" alt="&nbsp;" class="about-me__photo">
            <div class="about-me__content">
                <h2 class="about-me__name">
                    {{ t('headline.name') }}
                </h2>
                <p class="about-me__title">
                    {{ t('headline.title') }}
                </p>
                <span class="spacer"></span>
                <p class="about-me__description">
                    {{ t('headline.description') }}
                </p>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import gsap from 'gsap';

const { t } = useI18n();

onMounted(() => {
    gsap.fromTo(
        `.about-me__container *`,
        {
            x: -20,
            opacity: 0,
        },
        {
            x: 0,
            opacity: 1,
            duration: 0.3,
            stagger: 0.1,
            scrollTrigger: {
                trigger: `.about-me`,
                start: "40% bottom",
            },
        }
    );
});
</script>

<style scoped>
.about-me {
    min-height: 100vh;
    padding: 4rem 1rem;

    display: flex;
    flex-direction: column;
    justify-content: center;
}

.about-me__container {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1.5rem;
}

.about-me__container>* {
    opacity: 0;
}

.about-me__content {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: fit-content;
}

.about-me__description {
    color: var(--text-secondary-color);
    text-align: justify;
    margin-top: 2rem;
    max-width: 300px;
}

.about-me__photo {
    width: 13rem;
    height: auto;
}

.about-me__name {
    font-size: 1.6rem;
    width: fit-content;
}

.about-me__title {
    width: fit-content;
}


@media (min-width: 968px) {
    .about-me {
        min-height: 100vh;
        flex-direction: row;
    }

    .about-me__container {
        flex-direction: row;
        gap: 3rem;
    }

    .about-me__content {
        padding: 0.6rem 0;
        align-items: flex-start;
    }

    .about-me__description {
        max-width: 24rem;
    }

    .about-me__name {
        font-size: 2rem;
    }
}
</style>