<script>
export default {
    props: ['resourceName', 'field'],

    data: function () {
        return {
            value: JSON.parse(this.field.value || '{}'),
        };
    },

    computed: {
        latitude: function () {
            return this.value.latitude;
        },

        longitude: function () {
            return this.value.longitude;
        },

        hasLatitude: function () {
            return (this.latitude != 0);
        },

        hasLongitude: function () {
            return (this.longitude != 0);
        },

        locationIsSet: function () {
            return this.hasLatitude
                || this.hasLongitude;
        },

        locationIsNotSet: function () {
            return ! this.locationIsSet;
        },
    },
};
</script>

<template>
    <span>
        <span
            v-if="locationIsNotSet"
        >
            &#8212;
        </span>
        <span
            v-if="locationIsSet && hasLatitude"
            class="location"
        >
            <svg aria-hidden="true" width="16" height="16" focusable="false" data-prefix="fas" data-icon="line-height" class="svg-inline--fa fa-line-height fa-w-20" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 512"><path fill="currentColor" d="M626.29 224H269.71c-7.57 0-13.71 7.16-13.71 16v32c0 8.84 6.14 16 13.71 16h356.58c7.57 0 13.71-7.16 13.71-16v-32c0-8.84-6.14-16-13.71-16zm0 160H269.71c-7.57 0-13.71 7.16-13.71 16v32c0 8.84 6.14 16 13.71 16h356.58c7.57 0 13.71-7.16 13.71-16v-32c0-8.84-6.14-16-13.71-16zm0-320H269.71C262.14 64 256 71.16 256 80v32c0 8.84 6.14 16 13.71 16h356.58c7.57 0 13.71-7.16 13.71-16V80c0-8.84-6.14-16-13.71-16zM176 144c14.31 0 21.33-17.31 11.31-27.31l-80-80a16 16 0 0 0-22.62 0l-80 80C-4.64 126 .36 144 16 144h48v224H16c-14.29 0-21.31 17.31-11.29 27.31l80 80a16 16 0 0 0 22.62 0l80-80C196.64 386 191.64 368 176 368h-48V144z"></path></svg>
            {{ latitude }}
        </span>
        <span
            v-if="locationIsSet && hasLongitude"
            class="location"
        >
            <svg aria-hidden="true" width="16" height="16" focusable="false" data-prefix="fas" data-icon="line-height" class="svg-inline--fa fa-line-height fa-w-20 fa-rotate-270" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 512"><path fill="currentColor" d="M626.29 224H269.71c-7.57 0-13.71 7.16-13.71 16v32c0 8.84 6.14 16 13.71 16h356.58c7.57 0 13.71-7.16 13.71-16v-32c0-8.84-6.14-16-13.71-16zm0 160H269.71c-7.57 0-13.71 7.16-13.71 16v32c0 8.84 6.14 16 13.71 16h356.58c7.57 0 13.71-7.16 13.71-16v-32c0-8.84-6.14-16-13.71-16zm0-320H269.71C262.14 64 256 71.16 256 80v32c0 8.84 6.14 16 13.71 16h356.58c7.57 0 13.71-7.16 13.71-16V80c0-8.84-6.14-16-13.71-16zM176 144c14.31 0 21.33-17.31 11.31-27.31l-80-80a16 16 0 0 0-22.62 0l-80 80C-4.64 126 .36 144 16 144h48v224H16c-14.29 0-21.31 17.31-11.29 27.31l80 80a16 16 0 0 0 22.62 0l80-80C196.64 386 191.64 368 176 368h-48V144z"></path></svg>
            {{ longitude }}
        </span>
    </span>
</template>

<style lang="scss" scoped>
    .location {
        white-space: nowrap;
    }
</style>
