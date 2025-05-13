<template>
    <title>sketch</title>
    <div ref="captureArea">
        <NavBar :number="2" class="fixed w-full top-0 z-30 "></NavBar>
        <div ref="canvasContainer" class="w-full h-full  bg-white overflow-x-hidden"></div>
        <div class="TEXT w-full h-full absolute top-0 left-0 p-20">
            <div class="date text-blu text-center">
                COMUNICACIÓN CLARA, CON ESENCIA, PROCESO = RESULTADO, INNOVADOR, COMPROMETIDO Y COLABORATIVO.
            </div>
        </div>
        <div class="dragarround w-full h-full absolute top-0 left-0 p-20">
            <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4 mt-48 ml-32">
                <template v-for="(image, index) in shuffledImages" :key="index">
                    <img v-if="image !== 'empty'" :src="image" alt="Random Image" :class="enableDrag ? 'w-full h-auto object-cover rounded shadow-md draggable'
                        : 'w-full h-auto object-cover rounded shadow-md draggable pointer-events-none'" />
                    <div v-else class="w-full h-48 bg-transparent"></div>
                </template>
            </div>
        </div>
        <div class="controls flex flex-col fixed bottom-20 left-12 gap-6 p-3 rounded-xl border-blu border-2 bg-white">
            <PhNavigationArrow :size="64" color="none" weight="fill" stroke-width="14"
                :class="enableDrag ? 'stroke-black' : 'stroke-blu'"
                @click="enableDrag = !enableDrag; enablePaint = false" />
            <PhPencilSimpleLine :size="64" :color="enablePaint ? '#000000' : '#0C15CF'" weight="fill"
                @click="enablePaint = !enablePaint; enableDrag = false" />
            <PhCube :size="64" color="#0C15CF" weight="fill" />
        </div>
        <div class="flex buttons uppercase gap-10 fixed bottom-20 right-32">
            <Button @click="captureAndDownload">download</Button>
            <Button @click="reloadPage">randomize</Button>
        </div>
    </div>
    <Footer></Footer>
</template>


<script setup>
import { PhNavigationArrow, PhPencilSimpleLine, PhCube } from "@phosphor-icons/vue";
import { ref, onMounted, onBeforeUnmount } from 'vue'
import { gsap } from 'gsap'
import { Draggable } from 'gsap/Draggable'
import { Flip } from 'gsap/Flip'
import { InertiaPlugin } from 'gsap/InertiaPlugin'
import { toPng } from "html-to-image";

const captureArea = ref(null);

gsap.registerPlugin(Draggable, Flip, InertiaPlugin)

const canvasContainer = ref(null)
const winWidth = ref(0)
const winHeight = ref(0)
let sketchInstance = null
let paint = ref(true);
let enablePaint = ref(false);
let enableDrag = ref(false);

const captureAndDownload = async () => {
    if (captureArea.value) {
        try {
            // Usa html-to-image para capturar el área como una imagen PNG
            const image = await toPng(captureArea.value);

            // Crea un enlace para descargar la imagen
            const link = document.createElement("a");
            link.href = image;
            link.download = "captura.png"; // Nombre del archivo a descargar
            link.click();
        } catch (error) {
            console.error("Error al capturar la pantalla:", error);
        }
    } else {
        console.error("El área de captura no está disponible.");
    }
};

const reloadPage = () => {
    window.location.reload();
};

const arrayImages = [
    'projects/32.jpg',
    'projects/33.jpg',
    'projects/31.gif',
    'projects/42.jpg',
    'projects/43.jpg',
    'projects/44.jpg',
    'empty',
    'empty',
    'empty',
    'empty'
]

// Estado reactivo para el array de imágenes barajado
const shuffledImages = ref([])
// Función para barajar el array
function shuffleArray(array) {
    const copy = [...array]
    for (let i = copy.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1))
            ;[copy[i], copy[j]] = [copy[j], copy[i]]
    }
    return copy
}

// Definimos el sketch usando refs para el tamaño
const sketch = (p) => {
    p.setup = () => {
        p.createCanvas(winWidth.value, winHeight.value)
        p.frameRate(260);
        p.smooth();
    }
    p.draw = () => {
        if (paint.value && enablePaint.value) {
            p.stroke(12, 21, 207);
            p.strokeWeight(8);
            p.line(p.pmouseX, p.pmouseY, p.mouseX, p.mouseY);
        }
    }
    p.mousePressed = () => {
        paint.value = true;
    };
    p.mouseReleased = () => {
        paint.value = false;
    };
}

onMounted(async () => {
    // 1) Capturamos tamaño de ventana
    winWidth.value = window.innerWidth
    winHeight.value = window.innerHeight

    // 2) Import dinámico de p5 en entorno cliente
    const p5Module = await import('p5')
    const P5 = p5Module.default || p5Module

    // 3) Creamos instancia del sketch pasándole el canvasContainer
    sketchInstance = new P5(sketch, canvasContainer.value)

    // 4) para las imagenes colocadas aleatoriamente
    shuffledImages.value = shuffleArray(arrayImages)

    // 5) inicializar draggable
    nextTick(() => {
        Draggable.create(".draggable", {
            bounds: ".dragarround",
            inertia: true,
        });
    });
})

onBeforeUnmount(() => {
    if (sketchInstance) {
        sketchInstance.remove()
        sketchInstance = null
    }
})
</script>


<style lang="sass" scoped>

</style>