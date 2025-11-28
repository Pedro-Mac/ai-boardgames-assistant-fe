<template>
    <div>
        <form @submit="" @submit.prevent>
            <input type="file" @change="onFileChange" accept="application/pdf,.pdf" />
            <div v-if="selectedFileRef">
                <p>File Name: {{ fileNameRef }}</p>
                <p>File Size: {{ fileSizeRef }} bytes</p>
            </div>
        </form>

    </div>
</template>

<script setup lang="ts">

const selectedFileRef = ref<File | null>(null)
const fileNameRef = ref("")
const fileSizeRef = ref(0)

const onFileChange = (event: Event) => {
    const target = event.target as HTMLInputElement
    if (target.files && target.files.length > 0) {
        selectedFileRef.value = target.files[0] || null
        fileNameRef.value = target.files[0]?.name || ""
        fileSizeRef.value = target.files[0]?.size || 0
    }
}

const handleFormSubmission = () => {

}
</script>