<script>
export default {
    props: {
        value: Number
    },
    computed: {
        text() {
            switch (this.$props.value) {
                case 1:
                    return 'Too weak!';
                case 2:
                    return 'Weak';
                case 3:
                    return 'Medium';
                case 4:
                    return 'Strong';
                default:
                    return '';
            }
        }
    }
};
</script>

<template>
    <div :class="$style.container">
        <span :class="$style.label">STRENGTH</span>
        <span :class="$style.text">{{ text }}</span>
        <div :class="$style.meter" :data-strength="value">
            <div></div>
            <div></div>
            <div></div>
            <div></div>
        </div>
    </div>
</template>

<style module lang="scss">
.container {
    display: flex;
    align-items: center;
    padding: 1.5rem 2rem;
    background-color: var(--very-dark-grey-clr);

    @media (max-width: 600px) {
        padding: 1rem 1.25rem;
    }
}

.label {
    flex-grow: 1;
    color: var(--grey-clr);
}

.text {
    font-size: var(--heading-medium-fs);
}

.meter {
    display: flex;
    margin-inline-start: 1rem;
    gap: .5rem;

    @media (max-width: 600px) {
        display: flex;
        margin-inline-start: .5rem;
    }

    div {
        width: 10px;
        height: 28px;
        border: 2px solid var(--almost-white-clr);
        transition: border 300ms ease-in-out, background 300ms ease-in-out;
    }

    &[data-strength="1"] {
        div:nth-child(1) {
            border-color: var(--red-clr);
            background-color: var(--red-clr);
        }
    }

    &[data-strength="2"] {
        div:nth-child(1),
        div:nth-child(2) {
            border-color: var(--orange-clr);
            background-color: var(--orange-clr);
        }
    }

    &[data-strength="3"] {
        div:nth-child(1),
        div:nth-child(2),
        div:nth-child(3) {
            border-color: var(--yellow-clr);
            background-color: var(--yellow-clr);
        }
    }

    &[data-strength="4"] {
        div:nth-child(1),
        div:nth-child(2),
        div:nth-child(3),
        div:nth-child(4) {
            border-color: var(--neon-green-clr);
            background-color: var(--neon-green-clr);
        }
    }
}
</style>