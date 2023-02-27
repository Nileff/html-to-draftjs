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
