<script lang="ts">
  import {FocusEditor} from '$lib/core/commands.js';
  import {getEditor} from '$lib/core/composerContext.js';
  import CloseCircleButton from '../../generic/button/CloseCircleButton.svelte';
  import ModalDialog from '../../generic/dialog/ModalDialog.svelte';
  import ColorPicker from './ColorPicker.svelte';

  let onChange:
    | ((value: string, skipHistoryStack: boolean) => void)
    | undefined;

  const editor = getEditor();

  interface Props {
    color: string;
    title: string;
    showModal?: boolean;
  }

  let {color, title, showModal = $bindable(false)}: Props = $props();
  export function open(
    onChangeCallback: (value: string) => void,
    initialColor?: string,
  ) {
    if (initialColor) {
      color = initialColor;
    }
    onChange = onChangeCallback;
    showModal = true;
  }

  function close() {
    showModal = false;
    FocusEditor(editor);
  }

  function onColorChange(value: string) {
    if (onChange) {
      onChange(value, true);
    }
  }
</script>

<ModalDialog bind:showModal>
  <CloseCircleButton on:click={close} />

  <div class="modal">
    <h2 class="Modal__title">{title}</h2>
    <div class="Modal__content">
      <ColorPicker {color} onChange={onColorChange} />
    </div>
  </div>
</ModalDialog>
