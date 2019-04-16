<template>
  <svg xmlns="http://www.w3.org/2000/svg"
    xmlns:xlink="http://www.w3.org/1999/xlink"
    x="0px" y="0px" viewBox="0 0 24 24"
    style="enable-background:new 0 0 30 30;"
    xml:space="preserve"
    :class="disabled ? 'disabled' : 'enabled'">
    <g stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
      <g transform="translate(-1279.000000, -390.000000)" :fill="color" fill-rule="nonzero">
        <g id="pencil-tool" transform="translate(1279.000000, 390.000000)">
          <path d="M2.293,17.988 L2.146,18.134 C2.098,18.182 2.06,18.239 2.036,18.302 L0.036,23.302 C-0.038,23.488 0.005,23.699 0.146,23.841 C0.242,23.937 0.37,23.987 0.5,23.987 C0.562,23.987 0.626,23.975 0.686,23.951 L5.686,21.951 C5.794,21.908 5.883,21.828 5.938,21.728 C5.949,21.714 5.965,21.696 5.983,21.676 L2.293,17.988 Z" id="Shape"></path>
          <path d="M23.227,0.752 C22.241,-0.234 20.522,-0.234 19.536,0.752 L17.003,3.284 L20.687,6.968 C21.489,6.174 22.335,5.338 23.225,4.459 C23.723,3.968 23.998,3.313 24,2.614 C24.002,1.914 23.73,1.255 23.227,0.752 Z" id="Shape"></path>
          <path d="M16.296,3.991 L3,17.281 L6.67,20.951 C7.998,19.582 11.464,16.097 19.977,7.672 L16.296,3.991 Z" id="Shape"></path>
        </g>
      </g>
    </g>
  </svg>
</template>

<script>
export default {
  name: 'PencilIcon',
  props: {
    color: { type: String, default: '#6d6d6d' },
    disabled: { type: Boolean, default: false }
  }
}
</script>

<style lang="scss" scoped>
.enabled {
  opacity: 1;
  cursor: pointer;
}
.disabled {
  opacity: 0.4;
  cursor: default;
}
</style>
