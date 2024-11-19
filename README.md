# Milo goes to college
Use this project template to create a Milo site.

## Steps

1. Copy existing [`college`](https://adobe.sharepoint.com/:f:/r/sites/adobecom/Shared%20Documents/demos/college) content folder to your sharepoint and give helix@adobe.com View access
2. Click "[Use this template](https://github.com/adobecom/milo-college/generate)" Github button on this project.
3. Install the [AEM Code Sync Bot](https://github.com/apps/aem-code-sync)

From your newly created project

1. Install the [Helix Bot](https://github.com/apps/helix-bot/installations/new).
2. Change the fstab.yaml file to point to your content.
3. Add the project to the [Helix Sidekick](https://github.com/adobe/helix-sidekick).
4. Start creating your content.

## Developing
1. Install the [Helix CLI](https://github.com/adobe/helix-cli): `sudo npm install -g @adobe/aem-cli`
1. Run `aem up` this repo's folder. (opens your browser at `http://localhost:3000`)
1. Open this repo's folder in your favorite editor and start coding.

## Testing
```sh
npm run test
```
or:
```sh
npm run test:watch
```
This will give you several options to debug tests. Note: coverage may not be accurate.

## Security
1. Create a Service Now ID for your project via [Service Registry Portal](https://adobe.service-now.com/service_registry_portal.do#/search)
2. Update the `.kodiak/config.yaml` file to make sure valid team members are assigned security vulnerability Jira tickets.


## Milo Setup

Milo requires the following Sidekick configuration. If using the standard setup, this will be found in `tools/sidekick/config.json`. However, if using the config service, this file becomes irrelevant and is deleted. Therefore the settings are also being provided in this readme so that it can be passed to the configuration service if required. 

```json
{
  "plugins": [
    {
      "id": "library",
      "title": "Library",
      "environments": [
        "edit"
      ],
      "isPalette": true,
      "passConfig": true,
      "paletteRect": "top: auto; bottom: 20px; left: 20px; height: 398px; width: 360px;",
      "url": "https://milo.adobe.com/tools/library",
      "includePaths": [
        "**.docx**"
      ]
    },
    {
      "id": "tools",
      "title": "Tools",
      "isContainer": true
    },
    {
      "containerId": "tools",
      "id": "localize",
      "title": "Localize",
      "environments": [
        "edit"
      ],
      "url": "https://milo.adobe.com/tools/loc/index.html",
      "passReferrer": true,
      "passConfig": true,
      "excludePaths": [ "/**" ],
      "includePaths": [ "**/:x**" ]
    },
    {
      "containerId": "tools",
      "title": "Check Schema",
      "id": "checkschema",
      "environments": ["prod"],
      "event": "check-schema",
      "excludePaths": [
        "/tools**",
        "*.json"
      ]
    },
    {
      "containerId": "tools",
      "title": "Preflight",
      "id": "preflight",
      "environments": [
        "dev",
        "preview",
        "live"
      ],
      "event": "preflight"
    },
    {
      "containerId": "tools",
      "id": "locales",
      "title": "Locales",
      "environments": [
        "edit",
        "dev",
        "preview",
        "live"
      ],
      "isPalette": true,
      "passConfig": true,
      "passReferrer": true,
      "paletteRect": "top: auto; bottom: 25px; left: 75px; height: 388px; width: 360px;",
      "url": "https://milo.adobe.com/tools/locale-nav",
      "includePaths": [
        "**.docx**"
      ]
    }
  ]
}
```