
<template>
<div style="overflow: hidden;">
  <editor-content :editor="editor!" />
  <button
    type="button"
    @click="() => editor?.commands.insertTable({ rows: 3, cols: 3, withHeaderRow: true })"
  >
    Add Table
  </button>
</div>
</template>

<script setup lang="ts">
import StarterKit from "@tiptap/starter-kit";
// // eslint-disable-next-line import/no-extraneous-dependencies
// import Document from "@tiptap/extension-document";
// import Gapcursor from "@tiptap/extension-gapcursor";
// import Paragraph from "@tiptap/extension-paragraph";
import Table from "@tiptap/extension-table";
import TableCell from "@tiptap/extension-table-cell";
import TableHeader from "@tiptap/extension-table-header";
import TableRow from "@tiptap/extension-table-row";
// // eslint-disable-next-line import/no-extraneous-dependencies
// import Text from "@tiptap/extension-text";
import { useEditor, EditorContent, Editor } from "@tiptap/vue-3";
import { ShallowRef } from "nuxt/dist/app/compat/vue-demi";
// @ts-ignore
import { Mathematics } from "@exampathfinder/tiptap-katex";



// const editor: ShallowRef<Editor | undefined>;



const editor = useEditor({
  extensions: [
    StarterKit,
    // Document,
    // Paragraph,
    // Text,
    // Gapcursor,
    Table.configure({
      resizable: true,
    }),
    TableRow,
    TableHeader,
    TableCell,
    Mathematics,
  ],
  content: `
        <h1>
          This editor supports $\\LaTeX$ math expressions.
        </h1>
        <p>
          Did you know that $3 * 3 = 9$? Isn't that crazy? Also Pythagoras' theorem is $a^2 + b^2 = c^2$.<br />
          Also the square root of 2 is $\\sqrt{2}$. If you want to know more 
          about $\\LaTeX$ visit <a href="https://katex.org/docs/supported.html" target="_blank">katex.org</a>.
        </p>
        <p>
          Do you want go deeper? Here is a list of all supported functions:
        </p>
        <ul>
          <li>$\\sin(x)$</li>
          <li>$\\cos(x)$</li>
          <li>$\\tan(x)$</li>
      `,
});

</script>

<style>
 .ProseMirror > * + * {
	 margin-top: 0.75em;
}
 .ProseMirror .Tiptap-mathematics-editor {
	 background: #202020;
	 color: #fff;
	 font-family: monospace;
	 padding: 0.2rem 0.5rem;
}
 .ProseMirror .Tiptap-mathematics-render {
	 cursor: pointer;
	 padding: 0 0.25rem;
	 transition: background 0.2s;
}
 .ProseMirror .Tiptap-mathematics-render:hover {
	 background: #eee;
}
 .ProseMirror .Tiptap-mathematics-editor, .ProseMirror .Tiptap-mathematics-render {
	 border-radius: 0.25rem;
	 display: inline-block;
}

.editor {
  border: 1px solid rgba(0, 0, 0, 0.12)
}
.editor__content .ProseMirror {
  min-height: 200px;
}
.ProseMirror{
  margin: 0 0;
  padding: 5px 15px 5px 15px;
  text-align: left;
}

.ProseMirror > * + * {
  margin-top: 0px;
}
.ProseMirror ul, .ProseMirror ol {
  padding: 0 1rem;
  margin-top: 0.75em;
}
.ProseMirror p {
  margin-bottom: 0px;
}

.ProseMirror p img {
  display: initial;
}

/*
  Hack for break and next line
  https://github.com/ueberdosis/tiptap/issues/412#issuecomment-593635371
*/
.ProseMirror p:empty::after{
  content: "\00A0";
}

.ProseMirror h1, .ProseMirror h2, .ProseMirror h3, .ProseMirror h4 {
  line-height: 1.1;
}

.ProseMirror table {
  border-collapse: collapse;
  table-layout: fixed;
  margin: 0;
  overflow: hidden;
}
.ProseMirror table td,
.ProseMirror table th {
  min-width: 1em;
  border: 2px solid #ced4da;
  padding: 3px 5px;
  vertical-align: top;
  box-sizing: border-box;
  position: relative;
}
.ProseMirror table td > *,
.ProseMirror table th > * {
  margin-bottom: 0;
}
.ProseMirror table th {
  font-weight: bold;
  text-align: left;
  background-color: #f1f3f5;
}
.ProseMirror table .selectedCell:after {
  z-index: 2;
  position: absolute;
  content: "";
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  background: rgba(200, 200, 255, 0.4);
  pointer-events: none;
}
.ProseMirror table .column-resize-handle {
  position: absolute;
  right: -2px;
  top: 0;
  bottom: -2px;
  width: 4px;
  background-color: #adf;
  pointer-events: none;
}
.ProseMirror table p {
  margin: 0;
}
.tableWrapper {
  overflow-x: auto;
}
.resize-cursor {
  cursor: ew-resize;
  cursor: col-resize;
}
::v-deep .ProseMirror > * + * {
  margin-top: 0.75em;
}

.ProseMirror ol {
  padding: 0 1rem;
  list-style: decimal !important;
}

.ProseMirror ul {
  padding: 0 1rem;
  list-style: disc !important;
}
h1 {
  font-size: 4rem;
  font-weight: 700;
}

h2 {
  font-size: 1.5rem;
  font-weight: 700;
}

h3 {
  font-size: 1.25rem;
  font-weight: 600;
}

/* For ReviewerQuestionEditor component */
.editor {
  background-color: white;
}

.editor-card {
  cursor: text;
}

.editor-card:hover {
  border: 1px black solid;
}

.text-initial {
  text-align: initial;
}

.ProseMirror .Tiptap-mathematics-editor {
  background: #202020;
  color: #fff;
  font-family: monospace;
  padding: 0.2rem 0.5rem;
}
.ProseMirror .Tiptap-mathematics-render {
  cursor: pointer;
  padding: 0 0.25rem;
  transition: background 0.2s;
}
.ProseMirror .Tiptap-mathematics-render:hover {
  background: #eee;
}
.ProseMirror .Tiptap-mathematics-editor, .ProseMirror .Tiptap-mathematics-render {
  border-radius: 0.25rem;
  display: inline-block;
}
</style>