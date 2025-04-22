<script setup>
import { ref } from 'vue'

const slike = {
        "Jabuka": "https://www.svgrepo.com/show/530203/apple.svg",
        "Mrkva": "https://www.svgrepo.com/show/530216/carrot.svg",
        "Sir": "https://www.svgrepo.com/show/530219/cake.svg",
        "Kruh": "https://www.svgrepo.com/show/530223/bread.svg",
    }

const proizvodi = [
        { naziv: "Jabuka", cijena: 0.25 },
        { naziv: "Mrkva", cijena: 0.12 },
        { naziv: "Kruh", cijena: 2.00 },
        { naziv: "Sir", cijena: 4.48 }
    ]

const korisnik = {
    jeAdmin: true,
    osobni_podaci: {
        ime: "Marko",
        prezime: "Krivić",
        adresa: {
            grad: "Pula",
            ulica: "Veruda",
            broj: 32
        },
        broj_telefona: "+091-123-456"
    },
    kosarica: [
        { naziv: "Jabuka", količina: 4 },
        { naziv: "Mrkva", količina: 12 },
        { naziv: "Sir", količina: 1 },
        { naziv: "Kruh", količina: 3 },
    ]
}

function dohvatiCijenu(naziv) {
    const proizvod = proizvodi.find(p => p.naziv === naziv)
    return proizvod.cijena
}

function sveukupnaCijena() {
    return korisnik.kosarica.reduce((suma, artikl) => {
    return suma + (dohvatiCijenu(artikl.naziv) * artikl.količina)}, 0)

}


function najskupljaStavka() {
    let najskuplji = korisnik.kosarica[0]
    let max = dohvatiCijenu(najskuplji.naziv) * najskuplji.količina
    korisnik.kosarica.forEach(artikl => {
    const ukupno = dohvatiCijenu(artikl.naziv) * artikl.količina
    if (ukupno > max) {
        najskuplji = artikl
        max = ukupno
    }
  })
  return najskuplji.naziv
}


</script>

<template>
<div class="bg-gray-900">
    <div class="flex justify-center items-center ">
        <div :class="korisnik.jeAdmin ? 'text-blue-600' : 'text-black'" class="border p-4 border-gray-300 rounded-lg mb-6 bg-blue-50 max-w-md mt-[24px] ml-[24px] ">
            
            <h1 class="text-2xl mb-[7px]"><b>Korisnički podaci</b></h1>

            <hr class="border-gray-300">
        
            <div class="mt-[7px]">
            <b>Ime:</b> {{ korisnik.osobni_podaci.ime }} {{ korisnik.osobni_podaci.prezime }} <br>
            <b>Adresa:</b> {{ korisnik.osobni_podaci.adresa.ulica }} {{ korisnik.osobni_podaci.adresa.broj }}, {{ korisnik.osobni_podaci.adresa.ulica }}<br>
            <b>Telefon:</b> {{ korisnik.osobni_podaci.broj_telefona }} <br>
            </div>
        </div>
    </div>
    <div class="flex justify-center items-center">
        <div class="border p-4 border-gray-300 rounded-lg mb-6 bg-gray-100 max-w-md mt-[24px] ml-[24px] ">
            
            <h1 class="text-2xl mb-[7px] flex items-center gap-2"><b>Košarica</b></h1>
        
            <div :class="korisnik.kosarica[0].naziv === najskupljaStavka() ? 'border-red-400 bg-red-50' : 'border-gray-300'" class="mt-[7px] border p-4 border-gray-300 rounded-lg flex items-center space-x-4 mb-2">
                <img :src="slike[korisnik.kosarica[0].naziv]" class="w-24 h-24" /> 
                <div>
                    <b>{{ korisnik.kosarica[0].naziv }}</b><br>
                    <b>Cijena:</b> {{ dohvatiCijenu(korisnik.kosarica[0].naziv).toFixed(2)}} € | <b>Kolicina: {{ korisnik.kosarica[0].količina }}</b><br>
                    <b>Ukupno:</b> {{ (dohvatiCijenu(korisnik.kosarica[0].naziv) * korisnik.kosarica[0].količina).toFixed(2) }} € <br>
                </div>
            </div>

            <div :class="korisnik.kosarica[1].naziv === najskupljaStavka() ? 'border-red-400 bg-red-50' : 'border-gray-300'" class="mt-[7px] border p-4 border-gray-300 rounded-lg flex items-center space-x-4 mb-2">
                <img :src="slike[korisnik.kosarica[1].naziv]" class="w-24 h-24" /> 
                <div>
                    <b>{{ korisnik.kosarica[1].naziv }}</b><br>
                    <b>Cijena:</b> {{ dohvatiCijenu(korisnik.kosarica[1].naziv).toFixed(2)}} € | <b>Kolicina: {{ korisnik.kosarica[1].količina }}</b><br>
                    <b>Ukupno:</b> {{ (dohvatiCijenu(korisnik.kosarica[1].naziv) * korisnik.kosarica[1].količina).toFixed(2) }} € <br>
                </div>
            </div>

            <div :class="korisnik.kosarica[2].naziv === najskupljaStavka() ? 'border-red-400 bg-red-50' : 'border-gray-300'" class="mt-[7px] border p-4 border-gray-300 rounded-lg flex items-center space-x-4 mb-2">
                <img :src="slike[korisnik.kosarica[2].naziv]" class="w-24 h-24" /> 
                <div>
                    <b>{{ korisnik.kosarica[2].naziv }}</b><br>
                    <b>Cijena:</b> {{ dohvatiCijenu(korisnik.kosarica[2].naziv).toFixed(2)}} € | <b>Kolicina: {{ korisnik.kosarica[2].količina }}</b><br>
                    <b>Ukupno:</b> {{ (dohvatiCijenu(korisnik.kosarica[2].naziv) * korisnik.kosarica[2].količina).toFixed(2) }} € <br>
                </div>
            </div>

            <div :class="korisnik.kosarica[3].naziv === najskupljaStavka() ? 'border-red-400 bg-red-50' : 'border-gray-300'" class="mt-[7px] border p-4 border-gray-300 rounded-lg flex items-center space-x-4 mb-2">
                <img :src="slike[korisnik.kosarica[3].naziv]" class="w-24 h-24" /> 
                <div>
                    <b>{{ korisnik.kosarica[3].naziv }}</b><br>
                    <b>Cijena:</b> {{ dohvatiCijenu(korisnik.kosarica[3].naziv).toFixed(2)}} € | <b>Kolicina: {{ korisnik.kosarica[3].količina }}</b><br>
                    <b>Ukupno:</b> {{ (dohvatiCijenu(korisnik.kosarica[3].naziv) * korisnik.kosarica[3].količina).toFixed(2) }} € <br>
                </div>
            </div>

            <div>
                <h1><b>Ukupna cijena: </b> {{  sveukupnaCijena() }} €</h1>
            </div>
        


        </div>
    </div>
</div>
</template>


