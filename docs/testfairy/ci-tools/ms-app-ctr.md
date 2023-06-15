---
id: ms-app-ctr
title: Microsoft App Center
sidebar_label: MS App Center
---

import useBaseUrl from '@docusaurus/useBaseUrl';
import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

To upload apps from Microsoft App Center to TestFairy, do the following:

### 1. Create an Upload Script

Create a new file, call it `appcenter-post-build.sh`, and add it next to the project file in your repository.

```sh
#!/usr/bin/env bash

TESTFAIRY_UPLOAD_API_KEY=1234356

if [[ "$APPCENTER_XCODE_PROJECT" ]]; then
 curl https://upload.testfairy.com/api/upload \
 -F "api_key=$TESTFAIRY_UPLOAD_API_KEY" \
 -F "file=@$APPCENTER_OUTPUT_DIRECTORY/example.ipa"
fi

if [[ -z "$APPCENTER_XCODE_PROJECT" ]]; then
 curl https://upload.testfairy.com/api/upload \
 -F "api_key=$TESTFAIRY_UPLOAD_API_KEY" \
 -F "file=@$APPCENTER_OUTPUT_DIRECTORY/example.apk"
fi
```

### 2. Verify a Post Build Step Exists

App-center uses this file as a `post build script` for your project, so your app gets uploaded automatically.

<img src={useBaseUrl('/img/test-fairy/ci-tools/appcntr-1.png')} alt="post build script"/>
