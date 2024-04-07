<template>
    <q-card class="q-mb-md"
        style="max-width: 500px; min-width: 990px; margin-bottom: 0px; margin-top: 70px; margin-left: 15px;">
        <q-card-section>
            <div class="flex items-center">
                <q-btn flat icon="arrow_back" size="11px" class="back-button" @click="goBack" />
                <span class="page-title"><span class="add-store">Store Name</span></span>
                <div style="margin-left: 420px;">
                    <q-btn unelevated rounded color="primary" label="Show Location"
                        style="width: 130px; padding: 8px 20px; font-size: 11px;" />
                    <q-btn unelevated rounded color="primary" label="Edit"
                        style="margin-right: 10px; margin-left: 10px; width: 120px; padding: 8px 16px; font-size: 11px;" />
                    <q-btn unelevated rounded color="primary" label="Delete"
                        style="width: 120px; padding: 8px 16px; font-size: 11px;" />

                </div>
            </div>

            <q-card-main>
                <div class="fit row wrap justify-start items-start content-start">
                    <div>
                        <div class="title">Contact</div>
                        <hr class="section-divider-left" />

                        <div class="form-group">
                            <label class="label" for="storeName">Store Name</label>
                            <span class="value">{{ storedData.storeName || '-' }}</span>
                        </div>
                        <div class="form-group">
                            <label class="label" for="email">Email Address</label>
                            <span class="value">{{ storedData.email || '-' }}</span>
                        </div>
                        <div class="form-group">
                            <label class="label" for="phoneNumber">Phone Number</label>
                            <span class="value">{{ storedData.phoneNumber || '-' }}</span>
                        </div>

                        <div class="title">Address</div>
                        <hr class="section-divider-left" />

                        <div class="form-group">
                            <label class="label" for="province">Province</label>
                            <span class="value">{{ storedData.province || '-' }}</span>
                        </div>
                        <div class="form-group">
                            <label class="label" for="city">City/Municipality</label>
                            <span class="value">{{ storedData.city || '-' }}</span>
                        </div>
                        <div class="form-group">
                            <label class="label" for="barangay">Barangay</label>
                            <span class="value">{{ storedData.barangay || '-' }}</span>
                        </div>
                        <div class="form-group">
                            <label class="label" for="streetBuilding">Street/Building</label>
                            <span class="value">{{ storedData.streetBuilding || '-' }}</span>
                        </div>
                        <div class="form-group">
                            <label class="label" for="postalCode">Postal Code</label>
                            <span class="value">{{ storedData.postalCode || '-' }}</span>
                        </div>
                    </div>
                    <div class="offset-4">
                        <div class="fit column wrap justify-start items-start content-start" style="margin-top: 40px;">
                            <label for="storeImage" style="font-weight: bold;">Store Image</label>
                            <q-img :src="storedData.storeImage" class="store-image" />
                        </div>
                    </div>
                </div>
            </q-card-main>
        </q-card-section>
    </q-card>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const storedData = ref({
    storeName: '',
    email: '',
    phoneNumber: '',
    storeImage: '',
    province: '',
    city: '',
    barangay: '',
    streetBuilding: '',
    postalCode: '',
});

onMounted(() => {
    const storedDataJSON = localStorage.getItem('storeData');
    if (storedDataJSON) {
        storedData.value = JSON.parse(storedDataJSON);
    }
});

function goBack() {
    window.location.reload();
}
</script>

<style scoped>
.title {
    color: #9d7204;
    font-weight: 400;
    font-size: 18px;
    margin-top: 40px;
    margin-left: 10px;
}

.page-title {
    color: #999;
    /* Gray out the text */
    font-weight: bold;
    font-size: 18px;
}

.add-store {
    color: #9d7204;
    /* Dark orange color */
}

.back-button {
    margin-left: -5px;
    margin-right: -5px;
}

.section-divider-left {
    margin-top: 5px;
    border: none;
    border-top: 1px solid #000000;
    /* Define the color and style of the divider */
    width: calc(100% + 200px);
    margin-left: 10px;
    /* Set a specific width for the divider */
    /* Subtract 10px from 100% to cut a bit from the right side */
}

.store-image-section {
    text-align: right;
    /* Align the store image to the right */
}

.store-image {
    width: 200px;
    height: auto;
    margin-top: 20px;
}

.form-group {
    display: flex;
    align-items: center;
}

.label {
    flex: 0 0 150px;
    /* Set a fixed width for the labels */
    margin-bottom: 20px;
    margin-left: 10px;
}

.value {
    flex: 1;
    /* Allow the values to fill the remaining space */
    margin-left: 20px;
    margin-bottom: 20px;
    white-space: nowrap;
}

</style>