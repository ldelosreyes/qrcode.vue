<template>
  <div class="container-fluid">
    <div class="page-header">
      <h1>qrcode.vue:</h1>
      <div class='row'>
        <div class='col-xs-4'>
          <a
            class="github-button"
            href="https://github.com/scopewu/qrcode.vue"
            data-show-count="true"
            aria-label="Star qrcode.vue on GitHub"
          >Star</a>
        </div>
        <div class='col-xs-8 text-right'>
          <a href='https://github.com/scopewu/qrcode.vue'>Fork me on GitHub</a>
        </div>
      </div>
    </div>
    <form class="form-horizontal">
      <div class="form-group">
        <label class="col-sm-2 control-label">Value:</label>
        <div class="col-sm-10">
          <textarea v-model="value" class="form-control" rows="3"></textarea>
        </div>
      </div>
      <div class="form-group">
        <label class="col-sm-2 control-label">Size:</label>
        <div class="col-sm-10">
          <div class='col-xs-8'>
            <input type="range" v-model="size" min="100" max="800" step="20" class="form-control">
          </div>
          <div class='col-xs-4 form-control-static'>{{size}}</div>
        </div>
      </div>
      <div class="form-group">
        <label class="col-sm-2 control-label">Margin:</label>
        <div class="col-sm-10">
          <div class='col-xs-8'>
            <input type="range" v-model="margin" min="0" max="10" step='1' class="form-control">
          </div>
          <div class='col-xs-4 form-control-static'>{{margin}}</div>
        </div>
      </div>
      <div class="form-group">
        <label class="col-sm-2 control-label">Level:</label>
        <div class="col-sm-10">
          <select v-model="level" class="form-control">
            <option value="L">L</option>
            <option value="Q">Q</option>
            <option value="M">M</option>
            <option value="H">H</option>
          </select>
        </div>
      </div>
      <div class="form-group">
        <label class="col-sm-2 control-label">renderAs:</label>
        <div class="col-sm-10">
          <select v-model="renderAs" class="form-control">
            <option value="svg">svg</option>
            <option value="canvas">canvas</option>
          </select>
        </div>
      </div>
      <div class="form-group">
        <label class="col-sm-2 control-label">Background:</label>
        <div class="col-sm-10">
          <div class="form-control-static">
            <input type="color" v-model="background">
          </div>
        </div>
      </div>
      <div class="form-group">
        <label class="col-sm-2 control-label">Foreground:</label>
        <div class="col-sm-10">
          <div class="form-control-static">
            <input type="color" v-model="foreground">
          </div>
        </div>
      </div>
      <div class="form-group">
        <label class="col-sm-2 control-label">QR_CODE:</label>
        <div class="col-sm-10">
          <div class="form-control-static">
            <qrcode-vue
              class="qrcode"
              :value="value"
              :margin='margin >>> 0'
              :renderAs="renderAs"
              :size="size >>> 0"
              :level="level"
              :background="background"
              :foreground='foreground'
            />
          </div>
        </div>
      </div>
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import QrcodeVue from '../src'

export default defineComponent({
  name: 'App',
  components: { QrcodeVue },
  data() {
    return {
      value: 'https://example.com',
      size: 100,
      level: 'L',
      background: '#ffffff',
      foreground: '#000000',
      renderAs: 'svg',
      margin: 0,
    }
  },
})
</script>
