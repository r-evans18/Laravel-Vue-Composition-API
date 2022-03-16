<template>
    <div class="overflow-hidden overflow-x-auto min-w-full align-middle sm:rounded-md">
        <div class="flex place-content-end mb-4">
            <div class="px-4 py-2 text-white bg-blue-600 hover:bg-blue-700 cursor-pointer mr-2">
                <router-link :to="{ name: 'companies.index' }" class="text-sm font-medium">Back</router-link>
            </div>
            <div class="px-4 py-2 text-white bg-blue-600 hover:bg-blue-700 cursor-pointer">
                <router-link :to="{ name: 'companies.edit', params: { id: company.id } }" class="text-sm font-medium">Update</router-link>
            </div>
        </div>


        <label>Name: </label> {{ company.name }} <br>
        <label>Email: </label>{{ company.email }} <br>
        <label>Address: </label>{{ company.address }} <br>
        <label>Website: </label>{{ company.website }} <br>
    </div>
</template>

<script>
import useCompanies from "../../composables/companies";
import {onMounted} from "vue";

export default {
    props: {
        id: {
            required: true,
            type: String
        }
    },

    setup(props) {
        const { errors, company, getCompany } = useCompanies()

        onMounted(getCompany(props.id))

        return {
            errors,
            company
        }
    }
}
</script>
