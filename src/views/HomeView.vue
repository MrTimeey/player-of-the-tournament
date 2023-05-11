<script setup lang="ts">
import InputField from '@/components/InputField.vue';
import { computed, ref } from 'vue';
import DropdownField from '@/components/DropdownField.vue';

const name = ref('');
const team = ref('');
const year = ref('U6');
const player = ref('');
const keeper = ref('');
const items = ['U6', 'U7', 'U8', 'U9', 'U10', 'U11'];

const requiredFields = computed(() => name.value !== '' && team.value !== '' && player.value !== '' && keeper.value !== '');

const sendMail = () => {
    if (!requiredFields.value) return;
    const subject = `Rewe Cup 2023 - Wahl Spieler des Turniers - ${year.value}`;
    let formattedBody = `Hi,\n\nmein Name ist ${name.value} und ich bin Trainer*in von ${team.value} (${year.value}).`;
    formattedBody += `\n\nMeine Wahl Spieler*in des Truniers: ${player.value} \n`;
    formattedBody += `Meine Wahl Torhüter*in des Turniers: ${keeper.value} \n\n`;
    formattedBody += 'Gesendet über rewecup.mrtimeey.de\n';
    console.log(formattedBody);
    location.href = `mailto:stuff@tim-kruse.com?subject=${subject}&body=${encodeURIComponent(formattedBody)}`;
};
</script>

<template>
    <div class="p-4 flex flex-col text-gray-200">
        <p class="text-3xl mt-5 font-extrabold">Rewe Cup 2023</p>
        <p class="mb-12 text-l font-bold text-gray-400">02.06. - 03.06.2024</p>
        <input-field class="mb-4" label="Wie heißt du?" placeholder="Name" v-model="name" />
        <input-field class="mb-4" label="Von welcher Mannschaft bist du Trainer*in?" placeholder="Mannschaft" v-model="team" />
        <dropdown-field class="mb-4" label="An welchem Turnier nimmst du teil?" placeholder="Jahrgang" :items="items" v-model="year" />
        <input-field class="mb-4" label="Wer ist für dich Spieler*in des Turniers?" placeholder="Spieler*in des Turniers" v-model="player" />
        <input-field class="mb-4" label="Wer ist für dich Torwart*in des Turniers?" placeholder="Torwart*in des Turniers" v-model="keeper" />
        <div class="card-actions justify-end mt-8">
            <button class="btn bg-red-600 hover:bg-red-400 disabled:bg-red-300" :disabled="!requiredFields" @click="sendMail">Abschicken</button>
        </div>
    </div>
</template>

<style scoped></style>
