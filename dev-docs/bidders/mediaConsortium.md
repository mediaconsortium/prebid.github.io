---
layout: bidder
title: Media Consortium
description: Prebid Media Consortium Bidder Adapter
biddercode: mediaConsortium
media_types: banner, video
pbjs: true
sidebarType: 1
---

### Prebid JS

To get acces to the full feature set of the adapter you'll need to allow localstorage access in the `bidderSettings`.

```javascript
    pbjs.bidderSettings = {
        mediaConsortium: {
            storageAllowed: true
        }
    }
```

#### Controlling 1plusX profile API usage and FPID retrieval

You can use the `setBidderConfig` function to enable or disable 1plusX profile API usage and fpid retrieval.

If the keys found below are not defined, their values will default to `false`.

```javascript
    pbjs.setBidderConfig({
        bidders: ['mediaConsortium'],
        config: {
            // Controls the 1plusX profile API usage
            useProfileApi: true,
            // Controls the 1plusX fpid retrieval
            readOnePlusXId: true
        }
    });
```

#### Required video parameters

| Name       | Scope    | Description                               | Example        | Type                 |
|------------|----------|-------------------------------------------|----------------|----------------------|
| playerSize | required | Array of sizes accepted by the player     | `[[300, 250]]` | `[number, number][]` |
| context    | required | Video context, must always be `outstream` | `outstream`    | `string`             |

##### example ad unit

```javascript
    const adUnits = [
        {
            code: 'div-prebid-video',
            mediaTypes:{
                video: {
                    playerSize: [[300, 250]],
                    context: 'outstream'
                }
            },
            bids:[
                {
                    bidder: 'mediaConsortium',
                    params: {}
                }
            ]
        }
    ];
```