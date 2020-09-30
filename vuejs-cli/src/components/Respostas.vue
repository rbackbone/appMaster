<template>
    <div class="container">
        <h1>Avaliação de Pares</h1> 
        <FormRespostas v-on:add-resposta="addResposta"></FormRespostas>
         <div class="list-group">
            <p v-if="respostas.length <= 0">sem respostas</p>
            <div v-else class="list-group-item" v-for="(resp, index) in todasRespostas" :key="resp.id">
                <span class="comment__author">Autor: <strong>{{
                    resp.nome}}
                </strong></span>
                <p>{{ resp.texto}}</p>
                <div>
                    <a href="#" title="Remover" v-on:click.prevent="removeTexto(index)">Remover</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import FormRespostas from './FormRespostas'
    export default {
        components: {
            FormRespostas
        },
        data(){
            return {
                respostas: []
            }
        },
        methods: {
            addResposta (resp){
                this.respostas.push(resp);

            },
             removeTexto(index) {
                console.log(index);
                this.respostas.splice(index,1);

            }
        },
        computed: {
            todasRespostas() {
                return this.respostas.map( resp => ({
                    ...resp,
                    nome: resp.nome.trim() === '' ? 'Anônimo' : resp.nome
                }))
                }
            },
        watch : {
            respostas (valor) {
                console.log(valor);
            }

        }
    }
</script>