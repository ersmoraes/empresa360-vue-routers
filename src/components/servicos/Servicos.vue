<template>
    <div>
        <h5>Serviços</h5>
        <hr>
        <div class="row">
            <div class="col mb-2" v-for="d in dados" :key="d.id">
                <div class="card" style="width: 11rem;">
                    <img :src="`/img/${d.icone}`" class="card-img-top">
                    <div class="card-body text-center">
                        <router-link :to="{ name: 'servico', params: { id: d.id} }">
                            <p class="card-text">{{d.servico}}</p>
                        </router-link>
                    </div>
                </div>
            </div>
        </div>

        <router-view class="mt-3"/>
        <router-view name="opcoes" />
        <router-view name="indicadores" />
    </div>
    
</template>

<script>
import ApiMixin from '@/mixins/ApiMixin'

export default {
   name: 'ServicosPage',
   mixins: [ApiMixin],
   created() {
       this.getDadosApi('http://localhost:3000/servicos')
   }
}
</script>