<script setup lang="ts">
import { useEditor, EditorContent } from "@tiptap/vue-3";
import StarterKit from "@tiptap/starter-kit";
import Image from "@tiptap/extension-image";
import Underline from "@tiptap/extension-underline";
import TextAlign from "@tiptap/extension-text-align";
import { NCard, NSpace, NButton, NIcon, NDivider, NTooltip } from "naive-ui";
import {
  Bold,
  Italic,
  Underline as UnderlineIcon,
  Strikethrough,
  AlignLeft,
  AlignCenter,
  AlignRight,
  AlignJustify,
} from "@vicons/fa";

const props = defineProps({
  modelValue: String,
});
const editor = useEditor({
  content: props.modelValue,
  extensions: [
    StarterKit,
    Image,
    Underline,
    TextAlign.configure({
      types: ["heading", "paragraph"],
    }),
  ],
  injectCSS: false,
});
</script>

<template>
  <NCard>
    <NSpace>
      <NTooltip>
        <template #trigger>
          <NButton
            secondary
            circle
            @click="editor?.chain().focus().toggleBold().run()"
            :type="editor?.isActive('bold') ? 'primary' : 'default'"
          >
            <template #icon>
              <NIcon>
                <Bold />
              </NIcon>
            </template>
          </NButton>
        </template>
        粗体
      </NTooltip>
      <NTooltip>
        <template #trigger>
          <NButton
            secondary
            circle
            @click="editor?.chain().focus().toggleItalic().run()"
            :type="editor?.isActive('italic') ? 'primary' : 'default'"
          >
            <template #icon>
              <NIcon>
                <Italic />
              </NIcon>
            </template>
          </NButton>
        </template>
        斜体
      </NTooltip>
      <NTooltip>
        <template #trigger>
          <NButton
            secondary
            circle
            @click="editor?.chain().focus().toggleUnderline().run()"
            :type="editor?.isActive('underline') ? 'primary' : 'default'"
          >
            <template #icon>
              <NIcon>
                <UnderlineIcon />
              </NIcon>
            </template>
          </NButton>
        </template>
        下划线
      </NTooltip>
      <NTooltip>
        <template #trigger>
          <NButton
            secondary
            circle
            @click="editor?.chain().focus().toggleStrike().run()"
            :type="editor?.isActive('strike') ? 'primary' : 'default'"
          >
            <template #icon>
              <NIcon>
                <Strikethrough />
              </NIcon>
            </template>
          </NButton>
        </template>
        删除线
      </NTooltip>
      <NTooltip>
        <template #trigger>
          <NButton
            secondary
            circle
            @click="editor?.chain().focus().setTextAlign('left').run()"
            :type="
              editor?.isActive({ textAlign: 'left' }) ? 'primary' : 'default'
            "
          >
            <template #icon>
              <NIcon>
                <AlignLeft />
              </NIcon>
            </template>
          </NButton>
        </template>
        左边对齐
      </NTooltip>
      <NTooltip>
        <template #trigger>
          <NButton
            secondary
            circle
            @click="editor?.chain().focus().setTextAlign('center').run()"
            :type="
              editor?.isActive({ textAlign: 'center' }) ? 'primary' : 'default'
            "
          >
            <template #icon>
              <NIcon>
                <AlignCenter />
              </NIcon>
            </template>
          </NButton>
        </template>
        中间对齐
      </NTooltip>
      <NTooltip>
        <template #trigger>
          <NButton
            secondary
            circle
            @click="editor?.chain().focus().setTextAlign('right').run()"
            :type="
              editor?.isActive({ textAlign: 'right' }) ? 'primary' : 'default'
            "
          >
            <template #icon>
              <NIcon>
                <AlignRight />
              </NIcon>
            </template>
          </NButton>
        </template>
        右边对齐
      </NTooltip>
      <NTooltip>
        <template #trigger>
          <NButton
            secondary
            circle
            @click="editor?.chain().focus().setTextAlign('justify').run()"
            :type="
              editor?.isActive({ textAlign: 'justify' }) ? 'primary' : 'default'
            "
          >
            <template #icon>
              <NIcon>
                <AlignJustify />
              </NIcon>
            </template>
          </NButton>
        </template>
        两边对齐
      </NTooltip>
    </NSpace>
    <NDivider />
    <div style="overflow-y: auto; height: 400px">
      <EditorContent :editor="editor" />
    </div>
  </NCard>
</template>

<style scoped>
:deep(.ProseMirror:focus) {
  outline: none;
}

:deep(.ProseMirror > * + *) {
  margin-top: 0.75em;
}

:deep(.ProseMirror) {
  margin-top: 0.75em;
}
</style>
