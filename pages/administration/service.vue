<template>
  <div class="page-container">
    <div class="header">
      <h3>Services Administration</h3>
      <div class="actions">
        <IconField>
          <InputIcon class="pi pi-search" />
          <InputText size="small" placeholder="Search" />
        </IconField>
        <Button
          size="small"
          icon="pi pi-plus"
          iconPos="right"
          label="Create Service"
          @click="showModal = true"
        />
      </div>
    </div>
    <div class="body">
      <!-- Table to show services -->
      <AppTable :services="services" />
    </div>

    <!-- Modal -->
    <Dialog
      v-model:visible="showModal"
      modal
      header="Create Service"
      :style="{ width: '50vw' }"
    >
      <form @submit.prevent="saveService">
        <div class="form-field">
          <label for="code">Code</label>
          <InputText v-model="newService.code" required />
        </div>
        <div class="form-field">
          <label for="name">Name</label>
          <InputText v-model="newService.name" required />
        </div>
        <div class="form-field">
          <label for="description">Description</label>
          <InputText v-model="newService.description" required />
        </div>
        <div class="form-field">
          <label for="type">Type</label>
          <InputText v-model="newService.type" required />
        </div>
        <div class="form-field">
          <label for="status">Status</label>
          <InputText v-model="newService.status" required />
        </div>

        <div class="actions">
          <Button
            type="button"
            label="Cancel"
            icon="pi pi-times"
            class="p-button-secondary"
            @click="showModal = false"
          />
          <Button
            type="submit"
            label="Save"
            icon="pi pi-check"
            class="p-button-primary"
          />
        </div>
      </form>
    </Dialog>
  </div>
</template>

<script setup>
import { ref, reactive } from "vue";
import Button from "primevue/button";
import InputText from "primevue/inputtext";
import Dialog from "primevue/dialog";
import IconField from "primevue/iconfield";
import InputIcon from "primevue/inputicon";
import AppTable from "@/components/AppTable.vue";

const showModal = ref < boolean > false;

const services = reactive([
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

const newService = reactive({
  code: "",
  name: "",
  description: "",
  type: "",
  created: new Date().toLocaleDateString(),
  lastUpdated: new Date().toLocaleDateString(),
  status: "Active",
});

const saveService = () => {
  services.push({ ...newService });
  resetNewService();
  showModal.value = false;
};

const resetNewService = () => {
  Object.assign(newService, {
    code: "",
    name: "",
    description: "",
    type: "",
    created: new Date().toLocaleDateString(),
    lastUpdated: new Date().toLocaleDateString(),
    status: "Active",
  });
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
      gap: 10px;
    }
  }

  .form-field {
    margin-bottom: 15px;

    label {
      display: block;
      margin-bottom: 5px;
    }
  }

  .actions {
    display: flex;
    justify-content: flex-end;
    gap: 10px;
  }
}
</style>
