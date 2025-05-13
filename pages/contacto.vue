<template>
    <title>contacto</title>
    <NavBar :number="3" class="fixed w-full top-0"></NavBar>
    <div class="flex flex-col mt-60 p-12 gap-20 w-[900px]">
        <p class="bodysmall">
            Alexia Moreno es una diseñadora gráfica con base en Madrid, actualmente está finalizando sus estudios en la
            Escuela Superior de Diseño. Le interesa especialmente la dirección de arte y el desarrollo de lenguajes
            visuales
            que conecten emoción, concepto e identidad. Su trabajo abarca el diseño editorial, de branding y packaging,
            explorando la mezcla entre herramientas digitales y técnicas artesanales.
            En 2024 realizó prácticas en Prodigioso Volcán, donde participó en la creación de piezas estáticas y de
            motion
            para clientes como Sabadell, AXA y la Feria del Libro de Madrid, adquiriendo experiencia en procesos
            creativos
            reales y entornos colaborativos.
        </p>
        <div class="flex justify-between gap-20">
            <img src="../public/ilustration.png" alt="">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <!-- Columna izquierda -->
                <div class="grid gap-6">
                    <div class="grid grid-cols-2 gap-4">
                        <div class="bodylarge">EXPERIENCIA</div>
                        
                    </div>
                    <div class="bodysmall">
                        Prodigioso Volcán 2024-25. <br />Creación de contenido RRSS.
                    </div>
                    <div class="bodylarge">CLIENTES</div>
                    <div class="bodysmall">
                        AXA, Banco Sabadell, Levanta la Cabeza, <br />Novartis, Feria del Libro...
                    </div>
                </div>

                <!-- Columna derecha -->
                <div class="grid gap-6">
                    <div class="bodylarge">EDUCACIÓN</div>
                    <div class="bodysmall">
                        Escuela Superior de Diseño Madrid <br />
                        Grado en Diseño Gráfico <br />
                        2025
                    </div>
                    <div class="bodylarge">HUELLA DIGITAL</div>
                    <div class="bodysmall">
                        INSTAGRAM <br />
                        BEHANCE <br />
                        LINKEDIN
                    </div>
                </div>
            </div>
        </div>
    </div>
    <Footer></Footer>


</template>


<script setup>

</script>


<style lang="sass" scoped>

</style>