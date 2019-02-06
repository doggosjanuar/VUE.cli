<template>
    <div>
        <b-container>
		<p>Masukan nama: {{ nama }}</p>
		<input v-model="nama" placeholder="">

            <p>Skor = {{ score * 1 }}</p>
            <div role="tablist">
                <b-card v-for="(item,index) in items" no-body class="mb-1" :key="item.soal">
                    <b-card-header header-tag="header" class="p-1" role="tab">
                        <b-btn block  type="button" v-b-toggle="'accordion-'+ index" variant="success" v-on:click="setPosition(index)">{{ 'Quis Asal' + (index+1) }}</b-btn>
                    </b-card-header>
                    <b-collapse v-bind:id="'accordion-'+index" visible accordion="my-accordion" role="tabpanel">
                        <b-card-body>
                            <p class="card-text">{{ item.soal }}</p>
                            <div v-if="item.btn_click">
                                <b-form-group>
                                    <b-form-radio-group v-model="item.clicked"
                                                        :options="item.pilihan"
                                                        name="radioInline">
                                    </b-form-radio-group>
                                </b-form-group>
                                <b-button variant="danger" v-on:click="checkingAnswer">Yakin</b-button>
                            </div>
                            <div v-else><p>{{ item.clicked }}</p></div>
                        </b-card-body>
                    </b-collapse>
                </b-card>
            </div>
        </b-container>
		
    </div>
</template>
<script>
    export default {
        name : 'Tugas',
        data : function () {
            return {
                score:0,
                position:0,
                items: [{
                    soal : 'Rapper dari Indonesia ?',
                    btn_click : true,
                    clicked:String,
                    pilihan:[
                        { text:'Eminem',value:'salah'},
                        { text:'2Pac',value:'salah'},
                        { text: 'Biggie',value:'salah'},
						{ text: 'Young Lex',value:'young lex'},
						{ text: 'Big Sean',value:'salah'}],
                    jawaban:'young lex'
                },{
                    soal : 'Hewan berkaki empat ?',
                    btn_click : true,
                    clicked:String,
                    pilihan:[
                        { text:'Angsa',value:'salah'},
                        { text:'Ikan',value:'salah'},
                        { text: 'Kucing',value:'kucing'},
                        { text: 'Ular',value:'salah'},
						{ text: 'Naga',value:'salah'}],
                    jawaban:'kucing'
                },{
                    soal : 'Ninja adalah ?',
                    btn_click : true,
                    clicked:String,
                    pilihan:[
                        { text:'Ninja',value:'Ninjaaa'},
                        { text:'Samurai',value:'salah'},
                        { text: 'Mafia',value:'salah'},
                        { text: 'Yakuja',value:'salah'},
						{ text: 'Gangsta',value:'salah'}],
                    jawaban:'Ninjaaa'
                },{
                    soal : 'Sok Tebak?',
                    btn_click : true,
                    clicked:String,
                    pilihan:[
                        { text:'Pencet',value:'salah'},
                        { text:'Pencet',value:'salah'},
                        { text: 'Pencet',value:'salah'},
						{ text: 'Pencet',value:'salah'},
                        { text: 'Pencet',value:'Bener bre'}],
                    jawaban:'Bener bre'
                },{
                    soal : 'Musuh Batman yang terkuat?',
                    btn_click : true,
                    clicked:String,
                    pilihan:[
                        { text:'Superman',value:'kurang tepat'},
                        { text:'Daredevil',value:'bukan bre'},
                        { text: 'Thanos',value:'beda universe'},
                        { text: 'Dewa19',value:'ini siapa'},
						{ text: 'Hawa Nafsu',value:'Hawa Nafsu'}],
                    jawaban:'Hawa Nafsu'
                }],
            }
        },
        methods:{
            setPosition(i){
               this.position = i;
            },
            checkingAnswer(){
                this.items[this.position].btn_click = false;
                if(this.items[this.position].jawaban === this.items[this.position].clicked){this.score++;}
            },
        }
    }
</script>