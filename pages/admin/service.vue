<template>
  <div class="page-container">
    <!-- Header -->
    <div class="header">
      <h3>Services Administration ({{ servicesCount }} services)</h3>
      <div class="actions">
        <IconField>
          <InputIcon class="pi pi-search" />
          <InputText v-model="searchQuery" size="small" placeholder="Search" />
        </IconField>
        <Button
          size="small"
          icon="pi pi-plus"
          iconPos="right"
          label="Create Service"
          @click="addNewService"
        />
        <Button
          size="small"
          icon="pi pi-plus"
          iconPos="right"
          label="Emit event"
          @click="emitServiceCountEvent"
        />
      </div>
    </div>
    <div class="body">
      <AppTable :data="data" />
    </div>
    <Toast />
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
import Button from "primevue/button";
import InputText from "primevue/inputtext";
import IconField from "primevue/iconfield";
import InputIcon from "primevue/inputicon";
import AppTable from "@/components/AppTable.vue";
import { useToast } from "primevue/usetoast";

definePageMeta({
  layout: "base",
});

const data = ref([
  {
    code: "DRE",
    name: "Diabetic Retinal Exam",
    description: "Diabetic Retinal Exam",
    type: "Assessment",
    created: "6/6/2024 by Kurtis Segars",
    lastUpdated: "6/8/2024 by Stephanie Pham",
    status: "Active",
  },
  {
    code: "A1C",
    name: "A1C Blood Test",
    description: "A1C Blood Test",
    type: "Assessment",
    created: "6/6/2024 by Kurtis Segars",
    lastUpdated: "6/7/2024 by Meghan Tooher",
    status: "Active",
  },
  {
    code: "HRA",
    name: "HRA Call",
    description: "HRA Call",
    type: "Outreach",
    created: "6/6/2024 by Kurtis Segars",
    lastUpdated: "6/6/2024 by Kurtis Segars",
    status: "Active",
  },
  {
    code: "WEL",
    name: "Welcome Call",
    description: "Welcome Call",
    type: "Outreach",
    created: "6/6/2024 by Kurtis Segars",
    lastUpdated: "6/7/2024 by Kurtis Segars",
    status: "Active",
  },
  {
    code: "BKR",
    name: "Back Rub",
    description: "Back Rub",
    type: "Service Only",
    created: "6/6/2024 by Kurtis Segars",
    lastUpdated: "6/6/2024 by Kurtis Segars",
    status: "Inactive",
  },
  {
    code: "HAE",
    name: "Health Assessment Evaluation",
    description: "Health Assessment Evaluation",
    type: "Assessment",
    created: "6/6/2024 by Kurtis Segars",
    lastUpdated: "6/6/2024 by Kurtis Segars",
    status: "Active",
  },
  {
    code: "LMP",
    name: "Lorem ipsum",
    description: "Lorem ipsum",
    type: "Service Only",
    created: "Lorem ipsum",
    lastUpdated: "Lorem ipsum",
    status: "Active",
  },
  {
    code: "LMP",
    name: "Lorem ipsum",
    description: "Lorem ipsum",
    type: "Service Only",
    created: "Lorem ipsum",
    lastUpdated: "Lorem ipsum",
    status: "Active",
  },
  {
    code: "LMP",
    name: "Lorem ipsum",
    description: "Lorem ipsum",
    type: "Service Only",
    created: "Lorem ipsum",
    lastUpdated: "Lorem ipsum",
    status: "Active",
  },
  {
    code: "LMP",
    name: "Lorem ipsum",
    description: "Lorem ipsum",
    type: "Service Only",
    created: "Lorem ipsum",
    lastUpdated: "Lorem ipsum",
    status: "Active",
  },
]);

const servicesCount = computed(() => data.value.length);

const searchQuery = ref("");
const toast = useToast();

const addNewService = () => {
  const newService = {
    code: `NEW${data.value.length + 1}`,
    name: "New Service",
    description: "This is a new service",
    type: "Service Only",
    created: new Date().toLocaleDateString(),
    lastUpdated: new Date().toLocaleDateString(),
    status: "Active",
  };
  data.value.push(newService);
};

onMounted(() => {
  console.log("service mounting");
  eventBus.on("shellUserEvent", (payload) => {
    toast.add({
      severity: "success",
      summary: "User Event Received",
      detail: `User Name: ${payload.userName}`,
      life: 3000,
    });
  });
});

const emitServiceCountEvent = () => {
  const payload = {
    message: "Service event emitted!",
    servicesCount: servicesCount.value,
  };
  console.log("Emitting service Event:", payload);
  eventBus.emit("serviceEvent", payload);
};
</script>

<style scoped lang="scss">
.page-container {
  display: flex;
  flex: 1;
  flex-direction: column;

  .header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 5px 10px;

    .actions {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
    }
  }

  .body {
    max-height: 100%;
    overflow: auto;
  }
}
</style>
