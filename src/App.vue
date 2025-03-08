<template>
  <div class="max-w-md mx-auto p-4 bg-white shadow-lg rounded-lg">
    <h2 class="text-xl font-semibold mb-4">Gestion des tâches</h2>

    <!-- Champ de saisie et bouton d'ajout -->
    <div class="flex gap-2 mb-4">
      <input
        type="text"
        v-model="newTask"
        class="flex-1 p-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
        placeholder="Nouvelle tâche..."
      />
      <button
        type="button"
        :disabled="newTask.length === 0"
        @click="addTask"
        class="px-4 py-2 bg-blue-500 text-white rounded-lg disabled:bg-gray-400"
      >
        Ajouter
      </button>
    </div>

    <!-- Affichage des tâches -->
    <p v-if="tasks.length === 0" class="text-gray-500 text-center">
      Aucune tâche enregistrée
    </p>
    <ul v-else class="space-y-2">
      <li
        v-for="task in sortedTasks"
        :key="task.date"
        class="flex items-center gap-2 p-2 border rounded-lg"
      >
        <input
          type="checkbox"
          v-model="task.completed"
          class="form-checkbox h-5 w-5"
        />
        <span :class="{ completed: task.completed }" class="flex-1">{{
          task.title
        }}</span>
      </li>
    </ul>

    <!-- Option pour masquer les tâches complétées -->
    <div class="mt-4 flex items-center gap-2">
      <input
        type="checkbox"
        v-model="hideCompletedTask"
        class="form-checkbox h-5 w-5"
      />
      <label>Masquer les tâches complétées</label>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

const tasks = ref([]); // Liste des tâches
const newTask = ref(""); // Nouvelle tâche en cours de saisie
const hideCompletedTask = ref(false); // État pour masquer ou non les tâches complétées

// Fonction pour ajouter une nouvelle tâche
const addTask = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push({
      title: newTask.value,
      completed: false,
      date: Date.now(),
    });
    newTask.value = ""; // Réinitialiser le champ après l'ajout
  }
};

// Liste triée des tâches, avec possibilité de masquer les tâches complétées
const sortedTasks = computed(() => {
  let sorted = [...tasks.value].sort((a, b) => a.completed - b.completed);
  return hideCompletedTask.value ? sorted.filter((t) => !t.completed) : sorted;
});
</script>

<style>
@import "https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css";

.completed {
  text-decoration: line-through;
  color: gray;
}
</style>
