<template>
    <div class="form-todo form-group">
        <p>
            <input placeholder="Nome" type="text" name="author" class="form-control" v-model="nome" />
        </p>
        <p>
            <textarea placeholder="Descrição" name="message" class="form-control" v-model="texto" id="" cols="30" rows="10"></textarea>
        </p>
        <button v-on:click.prevent="addComment" type="submit" class="btn btn-primary">Confirmar</button>
    </div>
</template>

<script>
    export default {


    data() {
        return {
            nome: '',
            texto: ''
                
            }
       },
        methods: {
            addComment () {

                console.log("chegou");
                console.log(this.nome);
                console.log(this.texto);
           
                this.$emit('add-resposta', {
                    nome: this.nome,
                    texto: this.texto,

                });

                this.nome = '';
                this.texto = '';
            },
        }
    }



</script>