<script lang="ts">
    /**
     * Set the height, default is h-96,
     * you can customize according to
     * https://tailwindcss.com/docs/height
     */
    export let height: string = "h-96";
    export let src: string = "";
    export let alt: string = "This is an image";
</script>

<div class="flex w-full  justify-center items-center">
    <img class="{ height } mx-auto" src="{ src }" alt="{ alt }" />
</div>