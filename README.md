# mdast-util-to-vnode

mdast utility to get the vue vnode

## What is this?

This package is a custom fork of [mdast-util-to-vnode](https://github.com/litingyes/mdast-util-to-vnode) with breaking changes in these areas:

- **Table rendering**: Tables now render headers and bodies in separate HTML tags (`<thead>` and `<tbody>`)

- **Function slots**: To address Vue 3 warnings, all non-function slots have been converted to functional slots

## API

This package exports the identifier `toVNode`. There is no default export.

`toVNode(mdast[, options])`

### Options

This package allows passing custom Vue components to override default mdast node rendering.

```ts
export type ComponentReturn = Component | [Component, Record<string, any> | undefined]

export interface ToVNodeOptions {
  components?: Partial<Record<Nodes['type'], ComponentReturn |
  ((node: Node) => ComponentReturn)>>
}
```

### Example Usage

```ts
const vNode = toVNode(tree, {
  components: {
    // Custom components for different node types
    heading: MyHeadingComponent,
    code: MyCodeComponent,
    // ...other component overrides
  }
})
```

---

Last Update: 2025-04-15
