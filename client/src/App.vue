<template>
    <div class="app-container h-100">
        <!-- <Micro v-if="this.analysis" class="left-pane" :analysis="this.analysis"/> -->
        <NewMicro v-if="this.analysis" class="left-pane" :analysis="this.analysis"/>
        <FileForm v-else="this.analysis" class="left-pane" url="/analyze" @received-analysis="setAnalysis" />
        <span class="line"></span>
        <OldMacro v-if="this.analysis" :analysis="this.analysis"/>
    </div>
</template>

<script>
    import FileForm from "./components/FileForm"
    import Macro from "./components/Macro"
    import OldMacro from "./components/OldMacro"
    import NewMicro from "./components/NewMicro"

    export default {
        name: "App",
        components: {
            FileForm,
            Macro,
            OldMacro,
            NewMicro
        },

        data() {
            return {
                analysis: null
            }
        },

        methods: {
            setAnalysis(analysis) {
                this.analysis = analysis;
            }
        }
    }
</script>

<style>
  body {
      height: 100vh;
  }

  .app {
      height: 100%;
  }

  .app-container {
      background-color: #262626;
      display: grid;
      grid-template-columns: 50% auto 50%;
  }
  .line {
    background:linear-gradient(#FFF,#FFF) center/2px 100% no-repeat;
    height: 100vh;
    width: 1px;
  }
</style>
