<template>
  <div class="animallcell_parent">
    <div class="sidebar_component">
      <div>
        <button class="nav_button">
          <lottie-interactive
            style="cursor: pointer;"
            path="hamburger_menu.json"
            @click="toggle_SideBar"
            interaction="switch"
            speed="4"
          />
        </button>
      </div>
      <div class="sidebar_parent" v-if="toggle">
        <div class="sidebar_container">
          <div class="animalcell_content">
            // Mitosis
            <div class="animal_slots">
              <div class="title-container">
                <p
                  class="title"
                  style="color: '#ffffff; font-family: Bebas; font-size: 45px; margin-bottom: 10px; letter-spacing: 4px;"
                >
                  Mitosis
                </p>
              </div>
              <div class="definition">
                <p>
                  Mitosis is a type of cell division where one cell (the mother)
                  divides into two genetically identical new cells (the
                  daughters). Mitosis is essential for the growth and
                  replacement of cells. The goal of mitosis is to make sure that
                  each daughter cell gets a perfect, full set of chromosomes.
                </p>
                <router-link to="/">
                  <button class="animal_button" style="margin-top: 12px">
                    Explore Animal Cell
                  </button>
                </router-link>
                <router-link to="/plantcell">
                  <button
                    class="animal_button"
                    style="margin-top: 12px; background: #1db954"
                  >
                    Explore Plant Cell
                  </button>
                </router-link>
              </div>
            </div>
            <hr
              style="width: 100%; border: 1px solid #535353; border-radius: 15px; margin-bottom: -2px"
            />
            // Interphase
            <div class="animal_slots">
              <div
                class="title-container"
                @click="this.cell_wall_tab = !this.cell_wall_tab"
              >
                <p class="title" style="color: '#ffffff;">
                  Interphase
                </p>
                <Dropdown_down v-if="this.cell_wall_tab" style="width: 25px;" />
                <Dropdown_up v-else style="width: 25px;" />
              </div>
              <div class="definition" v-show="this.cell_wall_tab">
                <p>
                  Before entering mitosis, the cell spends most of its life
                  cycle in interphase. It is a period of growth and development
                  in preparation before cell division, undergoing the following
                  phases:
                </p>
                <p class="title" style="font-size: 16px; margin-bottom:-5px">
                  1. G1 phase (First gap phase)
                </p>
                <p
                  class="definition"
                  style="font-size: 14px; margin-left: 15px;"
                >
                  During G1 phase, the cell grows physically larger, copies
                  organelles, and makes the molecular building blocks it will
                  need in later steps.
                </p>
                <p class="title" style="font-size: 16px; margin-bottom:-5px">
                  2. S phase
                </p>
                <p
                  class="definition"
                  style="font-size: 14px; margin-bottom: -15px; margin-left: 15px;  overflow: hidden; text-overflow: ellipsis; "
                >
                  In S phase, the cell synthesizes a complete copy of the DNA in
                  its nucleus. It also duplicates the centrosomes, a
                  microtubules-organizing structure.
                </p>
                <p class="title" style="font-size: 16px; margin-bottom:-5px">
                  3. G2 phase (Second gap phase)
                </p>
                <p
                  class="definition"
                  style="font-size: 14px;  margin-left: 15px;  overflow: hidden; text-overflow: ellipsis; "
                >
                  During G2 phase, the cell grows more, makes proteins and
                  organelles, and begins to reorganize its contents in
                  preparation for mitosis.
                </p>
                <button class="slot_button" @click="move_camera">
                  Move Camera
                </button>
              </div>
            </div>
            <hr
              style="width: 100%; border: 1px solid #535353; border-radius: 15px; margin-bottom: -2px"
            />
            // Stages of mitosis
            <div class="animal_slots">
              <div
                class="title-container"
                @click="this.cell_membrane_tab = !this.cell_membrane_tab"
              >
                <p class="title" style="color: '#ffffff;">
                  Stages of mitosis
                </p>
                <Dropdown_down
                  v-if="this.cell_membrane_tab"
                  style="width: 25px;"
                />
                <Dropdown_up v-else style="width: 25px;" />
              </div>
              <div class="definition" v-show="this.cell_membrane_tab">
                <p class="title" style="font-size: 16px; margin-bottom:-5px">
                  1. Early prophase
                </p>
                <p
                  class="definition"
                  style="font-size: 14px; margin-left: 15px;"
                >
                  In early prophase, the chromosomes start to condense, the
                  mitotic spindle begin to form, and the nucleolus disappears.
                </p>
                <p class="title" style="font-size: 16px; margin-bottom:-5px">
                  2. Prometaphase
                </p>
                <p
                  class="definition"
                  style="font-size: 14px; margin-left: 15px;"
                >
                  In prometaphase, chromosomes become very compact, nuclear
                  envelope breaks down and releases the chromosomes, the mitotic
                  spindle grows more, some of the microtubules start to
                  “capture” chromosomes, and the centrioles move toward opposite
                  poles.
                </p>
                <p class="title" style="font-size: 16px; margin-bottom:-5px">
                  3. Metaphase
                </p>
                <p
                  class="definition"
                  style="font-size: 14px; margin-left: 15px;"
                >
                  In metaphase, the centrioles are at the opposite poles of the
                  cell, the mitotic spindle has captured all the chromosomes,
                  and the chromosomes are lined up at the metaphase plate (not a
                  physical structure, just a term for the plane where the
                  chromosomes line up).
                </p>
                <p class="title" style="font-size: 16px; margin-bottom:-5px">
                  4. Anaphase
                </p>
                <p
                  class="definition"
                  style="font-size: 14px; margin-left: 15px;"
                >
                  In anaphase, the mitotic spindle pulls apart the chromosomes
                  towards opposite poles of the cell, splitting the centromere
                  that holds the sister chromatids together. Microtubules not
                  attached to any chromosome elongates and push apart opposite
                  poles making the cell longer.
                </p>
                <p class="title" style="font-size: 16px; margin-bottom:-5px">
                  5. Telophase
                </p>
                <p
                  class="definition"
                  style="font-size: 14px; margin-left: 15px;"
                >
                  In telophase, the chromosomes arrive at the opposite poles and
                  begin to decondense and return to their stringy form. Two new
                  nuclei form. Nuclear envelopes and nucleoli reforms. Mitotic
                  spindle breaks down.
                </p>
                <button class="slot_button" @click="move_camera">
                  Move Camera
                </button>
              </div>
            </div>
            <hr
              style="width: 100%; border: 1px solid #535353; border-radius: 15px; margin-bottom: -2px"
            />
            // Cytokinesis
            <div class="animal_slots">
              <div
                class="title-container"
                @click="this.nucleus_tab = !this.nucleus_tab"
              >
                <p class="title" style="color: '#ffffff;">
                  Cytokinesis
                </p>
                <Dropdown_down v-if="this.nucleus_tab" style="width: 25px;" />
                <Dropdown_up v-else style="width: 25px;" />
              </div>
              <div class="definition" v-show="this.nucleus_tab">
                <p>
                  Cytokinesis if the part of the cell division which divides the
                  cytoplasm to form two new separate daughter cells. Cytokinesis
                  is contractile, pinching the cell membrane in, forming a
                  cleavage furrow (for animal cells) or a cell plate (for plant
                  cells), along the middle of the cell, splitting it into two
                  new daughter cells.
                </p>
                <button class="slot_button" @click="move_camera">
                  Move Camera
                </button>
              </div>
            </div>
            <hr
              style="width: 100%; border: 1px solid #535353; border-radius: 15px; margin-bottom: -2px"
            />
          </div>
        </div>
      </div>
    </div>
    <div class="routing">
      Please Wait
    </div>
    <Renderer
      ref="renderer"
      antialias
      :orbit-ctrl="{
        enableDamping: true,
        enablePan: false,
        dampingFactor: 0.05,
        maxDistance: 15,
        minDistance: 10,
        minPan: 3,
      }"
      resize="window"
      :pointer="{ intersectRecursive: true }"
    >
      <Camera ref="camera" :position="{ x: 10, y: 1, z: 2 }" />
      <Scene>
        <SpotLight
          color="#ffffff"
          :position="{ y: 250, z: 0 }"
          :cast-shadow="true"
          :shadow-map-size="{ width: 1024, height: 1024 }"
        />
        <SpotLight
          color="#ffffff"
          :position="{ y: -150, z: 0 }"
          :cast-shadow="true"
          :shadow-map-size="{ width: 1024, height: 1024 }"
        />
        <GltfModel
          :position="{ x: 0, y: 1, z: 2 }"
          src="humanCell.glb"
          @progress="onProgress"
          @load="onReady"
        />
      </Scene>
      <EffectComposer>
        <RenderPass />
        <UnrealBloomPass :strength="0.8" :radius="1" />
      </EffectComposer>
    </Renderer>
  </div>
</template>

<script>
import gsap from "gsap";
import { LottieInteractive } from "lottie-interactive";
import Dropdown_down from "../components/Dropdown_down.vue";
import Dropdown_up from "../components/Dropdown_up.vue";

import {
  EffectComposer,
  SpotLight,
  Camera,
  GltfModel,
  Renderer,
  Scene,
  UnrealBloomPass,
  RenderPass,
} from "troisjs";
export default {
  data() {
    return {
      loaded: true,
      toggle: false,
      animalCellToggle: true,
      animal_cell_tab: false,
      cell_wall_tab: false,
      cell_membrane_tab: false,
      nucleus_tab: false,
      cytoplasm_tab: false,
      mitochondria_tab: false,
      ribosome_tab: false,
      er_tab: false,
      golgi_tab: false,
      microtubules_tab: false,
      microbodies_tab: false,
      microfilaments_tab: false,
      vacuole_tab: false,
      tonoplast_tab: false,
    };
  },
  components: {
    Dropdown_down,
    Dropdown_up,
    LottieInteractive,
    EffectComposer,
    SpotLight,
    Camera,
    GltfModel,
    Renderer,
    Scene,
    UnrealBloomPass,
    RenderPass,
  },
  mounted() {
    console.log("Hello");
    console.log(this.$refs.camera.camera.position.x);
  },
  methods: {
    move_camera() {
      console.log(this.$refs.camera.camera.position.z);
      console.log(this.$refs.camera.camera.position.y);
      gsap.to(this.$refs.camera.camera.position, {
        x: 1.5,
        y: -0.3383049367400532,
        z: 12,
        duration: 0.5,
        ease: "expo.out",
      });
    },
    onProgress() {
      console.log("Loading Animal Cell");
    },
    onReady() {
      const hello = (this.loaded = !this.loaded);
      console.log("hello loaded" + " " + hello);
    },
    toggle_SideBar() {
      this.toggle = !this.toggle;
      if (this.toggle == true) {
        gsap.to("canvas", { x: "35%", duration: 0.5, ease: "expo.out" });
        gsap.to(".nav_button", {
          left: "38%",
          duration: 0.5,
          ease: "expo.out",
        });
      } else {
        gsap.to("canvas", { x: "0%", duration: 0.5, ease: "expo.out" });
        gsap.to(".nav_button", { left: "3%", duration: 0.5, ease: "expo.out" });
      }
      console.log(this.AnimalCells);
    },
  },
  watch: {
    $route(to, from) {
      this.toggle = false;
      console.log("Route changed from " + from.path + " to " + to.path);
      gsap.to("canvas", { x: "0%", duration: 0.5, ease: "expo.out" });
      gsap.to(".nav_button", { left: "3%", duration: 0.5, ease: "expo.out" });
      // if (to.path == '/plantcell'){
      //   this.animalCellToggle = false
      // } else if (to.path == '/') {
      //   this.animalCellToggle = true
      // }
    },
  },
};
</script>
<style>
.loader_routes {
  z-index: 102;
  background: red;
}
.animal_button {
  padding: 15px;
  border: none;
  border-radius: 10px;
  font-size: 12px;
  font-weight: bold;
  background: #e62117;
  cursor: pointer;
  color: #ffffff;
  width: 100%;
}

.animallcell_parent {
  margin: 0;
  overflow: hidden;
  display: flex;
  justify-content: center;
  background: #030303;
}
.container_all {
  overflow: hidden;
  margin: 0;
  background: #030303;
}
.sidebar_parent {
  width: 35%;
  height: 100vh;
  position: absolute;
  z-index: 40;
  overflow-x: hidden;
  background-color: #030303;
  margin: 0px;
  top: 0;
  left: 0;
}
.sidebar_container {
  padding: 30px;
  display: flex;
  justify-content: space-around;
  display: flex;
  align-items: flex-start;
  flex-direction: column;
}
.sidebar_container > div {
  display: flex;
  justify-content: space-around;
  display: flex;
  align-items: flex-start;
  flex-direction: column;
}
.sidebar_container > div > div > p {
  display: flex;
  justify-content: space-around;
  display: flex;
  align-items: flex-start;
  flex-direction: column;
  text-align: left;
  color: #ffffff;
}
.sidebar_parent a {
  font-weight: bold;
  color: #ffffff;
}
canvas {
  position: fixed;
  z-index: 0;
  background: #030303;
  inset: 0;
}
</style>