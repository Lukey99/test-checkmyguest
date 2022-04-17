<template src="./main.html"></template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class Main extends Vue {
  //input
  montant = 100000;
  apportPc = 0;
  duree = 0;
  taux = 0;

  //display
  apport = 0;

  mensualite = 0;
  interet = 0;
  donutPc = 0;

  mounted(){
      const donut = document.getElementById("donut-segment");
      donut!.style.strokeDasharray = "100 0";
  }

  public calcul() {
    this.mensualite = Math.round(
      (this.montant - this.apport) / (this.duree * 12)
    );
    this.interet = Math.round(
      (this.montant - this.apport) * (this.taux / 100) * (1 / 12)
    );
    this.apport = Math.round(this.montant * (this.apportPc / 100));

    const element = document.getElementById("progress-bar_1");
    if (this.apportPc < 40)
      element!.style.width = (this.apportPc * 4).toString() + "px";
    else element!.style.width = (this.apportPc * 3.3).toString() + "px";

    const element2 = document.getElementById("progress-bar_2");
    if (this.duree < 7)
      element2!.style.width = (this.duree * 14.6).toString() + "px";
    else element2!.style.width = (this.duree * 11.2).toString() + "px";
    const element3 = document.getElementById("progress-bar_3");
    if (this.taux < 0.6)
      element3!.style.width = (this.taux * 150).toString() + "px";
    else element3!.style.width = (this.taux * 110).toString() + "px";

    //donut
    const donut = document.getElementById("donut-segment");
    this.donutPc = Math.round((this.mensualite*100)/(this.mensualite + this.interet));
    const remain = 100 - this.donutPc;
    donut!.style.strokeDasharray = this.donutPc.toString()+" "+remain.toString();
  }

  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss" src="./main.scss"></style>
