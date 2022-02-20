# Payload SEO Plugin

[![NPM](https://img.shields.io/npm/v/payload-plugin-seo)](https://www.npmjs.com/package/payload-plugin-seo)

A plugin for [Payload CMS](https://github.com/payloadcms/payload) to auto-generate custom meta data based on the content of your documents.

Core features:
  - Adds a `meta` field to every seo-enabled collection that:
    - Includes title, description, and image subfields
    - Auto-generates meta data from your document's content
    - Displays hints and indicators to help content editors
    - Renders a snippet of what a search engine might display
    - Soon: variable injection

## Installation

```bash
  yarn add payload-plugin-seo
  # OR
  npm i payload-plugin-seo
```

## Basic Usage

In the `plugins` array of your [Payload config](https://payloadcms.com/docs/configuration/overview), call the plugin with [options](#options):

```js
import { buildConfig } from 'payload/config';
import seo from 'payload-seo';

const config = buildConfig({
  collections: [
    {
      slug: 'pages',
      fields: []
    },
    {
      slug: 'media',
      upload: {
        staticDir: // path to your static directory,
      },
      fields: []
    }
  ],
  plugins: [
    seo({
      collections: [
        'pages',
      ],
      uploadsCollection: 'media',
      generateTitle: ({ doc }) => `Website.com — ${doc.title}`,
      generateDescription: ({ doc }) => doc.excerpt
    })
  ]
});

export default config;
```

### Options

- `collections`

    An array of collections slugs to enable SEO. Enabled collections receive a `meta` field which is an object of title, description, and image subfields.


- `uploadsCollection`

    An upload-enabled collection slug, for the meta image to access.

- `generateTitle`

    Lorem

    ```js
    seo({
      ...
      generateTitle: ({ doc }) => `Website.com — ${doc.title}`,
    })
    ```

  - `generateDescription`

    Lorem

    ```js
    seo({
      ...
      generateDescription: ({ doc }) => doc.excerpt
    })

  ## TypeScript

  All types can be directly imported:

  ```js
  import {
    SEOConfig,
    GenerateTitle,
    GenerateDescription
   } from 'payload-plugin-seo/dist/types';
  ```

  ## Screenshots

  <!-- ![screenshot 1](https://github.com/trouble/payload-plugin-seo/blob/main/images/screenshot-1.jpg?raw=true) -->