<template>
    <form @submit.prevent="onsubmit" class="screen">
        <div class="container">
            <div class="row"><h1 class="title">Now, about your project...</h1></div>
            <div class="row">
                <div class="col-7">
                    <div class="section">
                        <p>We like being on a first-name basis, but it also helps us get in touch with you.</p>
                        <div class="form-group">
                            <div class="form-item col">
                                <label for="name">What is your full name?</label>
                                <input id="name" type="text" placeholder="John Smith" v-model="fullName" />
                                <p class="error-text"></p>
                                <p class="success-text"></p>
                            </div>
                            <div class="form-item col">
                                <label for="email">What is your email address?</label>
                                <input id="email" type="email" placeholder="skyalbert.960@gmail.com" v-model="email" />
                            </div>
                        </div>
                    </div>
                    <div class="section options">
                        <p>What sort of creative work do you need help with? You can read about our services</p>
                        <div class="row">
                            <div class="col-4" v-for="item in lstPosition" :key="item.id">
                                <div class="block">
                                    <label class="option">
                                        <span>{{ item.name }}</span>
                                        <input type="radio" :value="item.id" v-model="position" />
                                        <span class="checkmark"></span>
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-4">
                    <div class="section right">
                        <p>Tell us what you need help with, the purpose of this project and problems wr’re solving.</p>
                        <div class="form-item">
                            <label for="about">What is your project all about?</label>
                            <textarea
                                id="about"
                                placeholder="Hey RHP Team, I’d love  to talk to you about  branding this Something AI  project we’re working..."
                                v-model="about"
                            ></textarea>
                        </div>
                        <div class="form-item">
                            <ul class="items">
                                <li class="item">
                                    <div class="file">
                                        <div class="file-icon">
                                            <img src="../assets/images/file.png" alt="File Icon" />
                                        </div>
                                        <div class="file-name">website-information-architecture.pdf</div>
                                        <div class="file-icon">
                                            <img src="../assets/images/close.png" alt="Close Icon" />
                                        </div>
                                    </div>
                                </li>
                                <li class="item">
                                    <div class="file">
                                        <div class="file-icon">
                                            <img src="../assets/images/file.png" alt="File Icon" />
                                        </div>
                                        <div class="file-name">logo-animation.mov</div>
                                        <div class="file-icon">
                                            <img src="../assets/images/close.png" alt="Close Icon" />
                                        </div>
                                    </div>
                                </li>
                                <li class="item">
                                    <div class="file">
                                        <div class="file-icon">
                                            <img src="../assets/images/upload.png" alt="Upload Icon" />
                                        </div>
                                        <div class="file-name">Attach files</div>
                                    </div>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="action">
            <div class="container">
                <div class="remaining">1/6 questions remaining</div>
                <div class="progress">
                    <div class="progress-inner">
                        <div class="progress-mask"></div>
                    </div>
                </div>
                <button type="submit" class="btn btn-submit">Submit</button>
            </div>
        </div>
    </form>
</template>

<script lang="ts">
import { defineComponent, ref, toRefs, onMounted, type Ref, type PropType } from 'vue';

export default defineComponent({
    setup(props, ctx) {
        const fullName: Ref<string> = ref('');
        const email: Ref<string> = ref('');
        const about: Ref<string> = ref('');
        const lstPosition = ref([
            { name: 'Intern', id: 1 },
            { name: 'Senior', id: 2 },
            { name: 'PM', id: 3 },
            { name: 'TL', id: 4 },
        ]);

        const position = ref<number | null>(null);

        const onsubmit = () => {
            const payload = {
                fullName: fullName.value,
                email: email.value,
                about: about.value,
                position: position.value,
            };
            console.log(payload);
        };

        return {
            fullName,
            email,
            about,
            lstPosition,
            position,
            onsubmit,
        };
    },
});
</script>
