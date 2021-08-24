<template>
    <form action="#">
        <h1>Создать клиента</h1>
        <div class="form-group">
                <div class="input-form">
                    <label for="name-field">Фамилия:</label>
                    <input type="text" name="" id="name-field">
                </div>
                <div class="input-form">
                    <label for="lastname-field">Имя:</label>
                    <input type="text" name="" id="lastname-field">
                </div>
                <div class="input-form">
                    <label for="patronymic-field">Отчество:</label>
                        <input type="text" name="" id="patronymic-field">
                </div>
            <div class="input-form date">
                <label for="dateBirth">Дата рождения:</label>
                <input name="date" type="text" onfocus="(this.type='date')" onblur="if(!this.value)this.type='text'">
            </div>
            <div class="input-form gender"> 
                <label><input type="radio" name="gender">Женский</label>
                <label><input type="radio" name="gender">Мужской</label>
            </div>
            <div class="input-form">
                <select name="" id="">
                    <option selected value="doctor">Лечащий врач</option>
                    <option value="">Иванов</option>
                    <option value="">Захаров</option>
                    <option value="">Чернышева</option>
                </select>
            </div>
            <div class="input-form">
                <Multiselect
                v-model="filter.selectedClients"
                :multiple="true"
                :options="clients"
                :custom-label="option => option.text"
                />
                <!-- <ul>
                    <li v-for="client in selectedClients" :key="client">{{client.type}}</li>
                </ul> -->
            </div>
        </div>
    </form>
</template>

<script>
import  {email, required}  from '@vuelidate/validators'
import  useVuelidate  from '@vuelidate/core'
import Multiselect from 'vue-multiselect'

export default {
    name: 'ClientForm',
    components: {
        // Multiselect: window.VueMultiselect.default
        Multiselect
    },
    data(){
        return{
            clients: [
                {
                    text: 'VIP',
                    value: 'VIP'
                },
                {
                    text: 'Проблемные',
                    value: 'Проблемные'
                },
                {
                    text: 'ОМС',
                    value: 'ОМС'
                }
            ],
            filter: {
                selectedClients: []
            }
        }
    },
    setup: () => ({ v$: useVuelidate() }),
        validations () {
            return {
            form: {
                name: { required },
                email: { required, email }
            }
        }
    }
}
</script>

<style lang="sass">
    @import './Form'                
</style>
