<p align="center">
  <a href="" rel="noopener">
 <img width=auto height=200px src="https://avatars.githubusercontent.com/u/28861843?s=200&v=4" alt="Katalon Google Cloud Build"></a>
</p>

<h1 align="center">Katalon Google Cloud Build</h1>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()
[![GitHub Issues](https://img.shields.io/github/issues/kylelobo/The-Documentation-Compendium.svg)](https://github.com/kylelobo/The-Documentation-Compendium/issues)
[![GitHub Pull Requests](https://img.shields.io/github/issues-pr/kylelobo/The-Documentation-Compendium.svg)](https://github.com/kylelobo/The-Documentation-Compendium/pulls)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](/LICENSE)

</div>

---

<p align="center"> A sample project of using Katalon Docker image with Google Cloud Build
    <br> 
</p>

## 📝 Table of Contents

- [Getting Started](#getting_started)
- [Usage](#usage)
- [Built Using](#built_using)
- [TODO](../TODO.md)
- [Contributing](../CONTRIBUTING.md)
- [Authors](#authors)
- [Acknowledgments](#acknowledgement)
- [References](#references)

## 🏁 Getting Started <a name = "getting_started"></a>

### Prerequisites

* A valid Katalon API Key<br/>
  Refer to [Generate API keys][Generate_API_Key] for more information about API key generation.

* Enable Google [Cloud Build API][Enable_Cloud_Build_API]

* Enable [Secret Manager API][Using_Secret_Manager]

* [Prepare a secret][Using_Secret_Manager] to store the Katalon API key


### Setup cloudbuid project

Create a `cloudbuild.yaml` file at the root of your katalon project

```yaml
steps:
- name: 'docker'
  args: ['pull', 'katalonstudio/katalon']
- name: 'docker'
  entrypoint: 'sh'
  args: ['-c', 'docker run -t --rm -v /workspace:/tmp/project katalonstudio/katalon katalonc.sh -projectPath=/tmp/project -browserType="Chrome" -retry=0 -retryStrategy=immediately -testSuiteCollectionPath="Test Suites/Simple Test Suite Collection" --config -webui.autoUpdateDrivers=true -apiKey=$$KATALON_API_KEY']
  secretEnv: ['KATALON_API_KEY']
availableSecrets:
  secretManager:
  - versionName: projects/$PROJECT_ID/secrets/KATALON_API_KEY/versions/1
    env: 'KATALON_API_KEY'
```

## 🔧 Running the tests <a name = "tests"></a>

Explain how to run the automated tests for this system.

4. 

5. 

### Connect to repo & Create a trigger


### Push a commit & Trigger run mannually


## 🎈 Reporting <a name="usage"></a>

Add notes about how to use the system.

## 🚀 Deployment <a name = "deployment"></a>

Add additional notes about how to deploy this on a live system.

## ⛏️ Built Using <a name = "built_using"></a>

- [MongoDB](https://www.mongodb.com/) - Database
- [Express](https://expressjs.com/) - Server Framework
- [VueJs](https://vuejs.org/) - Web Framework
- [NodeJs](https://nodejs.org/en/) - Server Environment

## 🎉 Acknowledgements <a name = "acknowledgement"></a>

- Hat tip to anyone whose code was used
- Inspiration
- References


## 🧐 References <a name = "references"></a>

* [Code build dashboard](https://console.cloud.google.com/cloud-build/dashboard)
* [Build configuration file schema](https://cloud.google.com/build/docs/build-config-file-schema)
* [Using secrets from Secret Manager](https://cloud.google.com/build/docs/securing-builds/use-secrets)
* [Secret Manager][Secret_Manager]
* [Cloud builders](https://cloud.google.com/build/docs/cloud-builders)
* [Substituting variable values](https://cloud.google.com/build/docs/configuring-builds/substitute-variable-values)


[Generate_API_Key]: https://docs.katalon.com/katalon-analytics/docs/ka-api-key.html#generate-a-katalon-api-key
[Secret_Manager]: https://console.cloud.google.com/security/secret-manager
[Using_Secret_Manager]: https://cloud.google.com/build/docs/securing-builds/use-secrets
[Enable_Cloud_Build_API]: https://cloud.google.com/build?hl=en