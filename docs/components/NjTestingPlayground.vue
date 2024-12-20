<template>
  <div>
    <div v-if="!multiple">
      Value: <treeselect-value :value="value" />
    </div>
    <div>
      <treeselect
        v-model="value"
        :multiple="multiple"
        :disable-top-level-branch-nodes="disableTopLevelBranchNodes"
        :flat="flat"
        :ignore-flat-mode-fixing="ignoreFlatModeFixing"
        :auto-select-descendants="autoSelectDescendants"
        :limit="3"
        :options="options"
        :max-height="200"
        />
    </div>
    <p style="display: flex; flex-direction: column; gap: 10px; margin-top: 30px;">
      <button :style="{ color: !multiple ? 'blue' : 'gray' }" @click="setTest1">Test 1</button>
      <button :style="{ color: !multiple ? 'gray' : 'blue' }" @click="setTest2">Test 2</button>
    </p>
    <p v-html="hint" />
    <div v-if="multiple">
      Extra Test Options:
      <label><input type="checkbox" v-model="disableTopLevelBranchNodes"> Disable Top Level Nodes</label>
    </div>
  </div>
</template>
<script>
  import { generateOptions } from './utils'

  export default {
    data: () => ({
      multiple: false,
      disableTopLevelBranchNodes: true,
      flat: false,
      ignoreFlatModeFixing: false,
      autoSelectDescendants: false,
      value: null,
      options: generateOptions(3, 2),
      hint: '',
      hint1: 'You can select branch nodes: <b>AA, AB, BA,</b> and <b>BB</b>. You cannot select top level branch nodes: <b>A, B</b>. The value below will change when you select a branch node and not a top level node',
      hint2: 'Selecting a branch node will auto select its descendants, but de-selecting will not auto deselect anything. Thereby keeping the branch nodes selected when desired.',
    }),
    beforeMount() {
      this.hint = this.hint1
    },
    methods: {
      setTest1() {
        this.disableTopLevelBranchNodes = true
        this.multiple = false
        this.ignoreFlatModeFixing = false
        this.autoSelectDescendants = false
        this.hint = this.hint1
        this.value = null
        this.flat = false
      },
      setTest2() {
        this.disableTopLevelBranchNodes = false
        this.multiple = true
        this.flat = true
        this.ignoreFlatModeFixing = true
        this.autoSelectDescendants = true
        this.hint = this.hint2
        this.value = []
      },
    },
  }
  </script>
