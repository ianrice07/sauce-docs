---
id: vscode
title: saucectl with Visual Studio Code
sidebar_label: Visual Studio Code
---

import useBaseUrl from '@docusaurus/useBaseUrl';
import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

Visual Studio Code can help you edit the `saucectl` configuration files by providing helpful suggestions, autocompletion and docs; all without having to leave the IDE.

## What You'll Need

- [Visual Studio Code](https://code.visualstudio.com/)
- [Visual Studio Code YAML Extension](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml)

## JSON Schema Validation

Our JSON schema is published to the [JSON Schema Store](https://www.schemastore.org/json/), which is made available to Visual Studio Code.

:::caution Default Limitations
By default, JSON Schema validation _only_ works with JSON files, not YAML. So make sure to have the YAML extension installed or this will not work.
:::

Ensure that the YAML Extension downloads schemas automatically from the Schema Store by
checking the Visual Studio Code settings to confirm that `yaml.schemaStore.enable` is set to `true`. If this entry does not exist, add it.

If your `saucectl` config YAML is stored in a `.sauce/` folder, Visual Studio Code will automatically apply the schema to all YAML files contained in that folder and no further action is required.

You should now be able to see the docs for various attributes:<br/><img src={useBaseUrl('img/stt/vscode-yaml-docs.png')} alt="Visual Studio Code YAML Attribute Description" width="300"/>

and have autocompletion ready at your fingertips!<br/><img src={useBaseUrl('img/stt/vscode-yaml-autocomplete.png')} alt="Visual Studio Code YAML Attribute Autocompletion" width="400"/>

Alternatively, it's also possible to associate schema files with files they are supposed to validate by adding the mapping into your Visual Studio Code settings:

```json
"yaml.schemas": {
    "https://raw.githubusercontent.com/saucelabs/saucectl/main/api/v1alpha/generated/saucectl.schema.json": "path/to/config.yml"
}
```

For more information, see the Visual Studio Code YAML extension page [mentioned above](#what-youll-need).
