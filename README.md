# HTML To DraftJS

A library for converting plain HTML to DraftJS Editor content.

## Installation

```
npm install html-to-draftjs --save
```

## Usage

```
import { EditorState, ContentState } from 'draft-js';
import htmlToDraft from 'html-to-draftjs';

const blocksFromHtml = htmlToDraft(this.props.content);
const { contentBlocks, entityMap } = blocksFromHtml;
const contentState = ContentState.createFromBlockArray(contentBlocks, entityMap);
const editorState = EditorState.createWithContent(contentState);
```

### (optional) customChunkRenderer
Use to define additional html nodes. Only supports atomic blocks.

* _nodeName: string_ - the name of the node, in lowercase
* _node: HTMLElement_ - the parsed node itself

This renderer function is executed before any other html to draft conversion.
Return nothing (or something falsy) to continue with the normal translation.

Example:

```
htmlToDraft('<hr/>', (nodeName, node) => {
  if (nodeName === 'hr') {
    return {
      type: 'HORIZONTAL_RULE',
      mutability: 'MUTABLE',
      data: {}
    };
  }
})
```

### (optional) customStyleMap
Use to define custom style map.

**[mapping dtaftjs styles](https://draftjs.org/docs/advanced-topics-inline-styles/#mapping-a-style-string-to-css)**

Example:

```
htmlToDraft('<span style="font-weight: 700">text</span>', undefined, {
    customBold: {
        fontWeight: 700,
    }
})
```
