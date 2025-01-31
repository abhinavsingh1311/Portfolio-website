<script setup>
defineEmits(['close']);
</script>

<template>
    <div class="modal-overlay">
        <div class="resume-modal">
            <div class="modal-header">
                <h2>My Resume</h2>
                <button @click="$emit('close')" class="close-btn">×</button>
            </div>
            <div class="modal-content">
                <section>
                    <h3>Experience</h3>
                    <p>Full Stack Developer | 2022-Present</p>
                    <h3>Education</h3>
                    <p>NAIT - Digital Media & IT Diploma (4.0 GPA)</p>
                    <h3>Skills</h3>
                    <ul>
                        <li>React/Next.js</li>
                        <li>Three.js</li>
                        <li>ASP.NET Core</li>
                    </ul>
                </section>
            </div>
        </div>
    </div>
</template>

<style scoped>
.modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
}

.resume-modal {
    background: white;
    padding: 2rem;
    border-radius: 8px;
    width: 80%;
    max-width: 600px;
    max-height: 80vh;
    overflow-y: auto;
}

.close-btn {
    background: none;
    border: none;
    font-size: 1.5rem;
    cursor: pointer;
    position: absolute;
    right: 1rem;
    top: 1rem;
}
</style>