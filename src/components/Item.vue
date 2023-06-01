<template>
    <div>
        <li class="videoGalleryItem">
            {{ video.tags }}
            <video class="videoItem" controls>
                <source :src="video.videos.tiny.url" type="video/mp4">
                Your browser does not support the video tag.
            </video>
            {{ video.likes }}
        </li>
    </div>
</template>

<script>
export default {
    name: "Item",
    props: {
        video: {
            type: Object,
            required: true
        }
    }
};
</script>

<style>
    .videoGalleryItem{
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .videoItem {
        min-width: 30%;
        max-width: 45%;
        height: auto;
    }
</style>
