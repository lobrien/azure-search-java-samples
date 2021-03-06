---
services: search
platforms: java
author: liamca
topic: sample
languages:
  - java
products:
  - azure
  - azure-search
---

# Getting Started with Azure Search using Java
This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

![Flask sample MIT license badge](https://img.shields.io/badge/license-MIT-green.svg)

This is a sample of how to interact with Azure Search using Java.  Not only does it execute most of the common API requests against Azure Search, but it also implements some of the best practices such as handling retries, etc.  

# Contents

| File/folder | Description |
|-------------|-------------|
| `src/main`       | Sample source code. |
| `src/test` | Test code exercising URL and query construction. |
| `pom.xml` | Maven 3 project file. |
| `CONTRIBUTING.md` | Guidelines for contributing to this project. |
| `LICENSE` | MIT License. | 
| `README.md`   | This file. |
| 

## Prerequisites

- Install a Java 11 SDK. An option that does not incur support costs is [Zulu](https://docs.microsoft.com/java/azure/jdk/?view=azure-java-stable).
- Choose a strategy for building and running the project using Maven 3:
    - If you wish to build and run from the command-line, install [Maven 3](https://maven.apache.org/download.cgi).
    - If you wish to use VSCode, install [VSCode](https://code.visualstudio.com/) and the [Maven for Java](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-maven) extension.
    - If you wish to use IDEA, install [IntelliJ IDEA](https://www.jetbrains.com/idea/) with default Java options.

## Setup

1. Clone or download this sample repository
1. Follow the steps in the article [Create an Azure Search service in the portal](https://docs.microsoft.com/azure/search/search-create-service-portal) to create and configure an Azure Search service that uses the "hotels" sample data.
1. Open project in IDE:
    * In VSCode: 
        1. Open folder containing `pom.xml` 
    * In IDEA: 
        1. Use the "Import project" dialog to open `pom.xml`
        1. Select the Java 11 JDK to use with the project
1. Configure access to the search service by editing the `ServiceName` and `ApiKey` values in the file [azure_search_config](src/main/resources/azure_search_config). Note that the `ServiceName` should only be the specific name of the service. For instance, if the URL to your service was `https://myservice.search.windows.net`, the `ServiceName` would be `myservice`.

## Running the sample

1. Execute Maven goal `verify exec:java`:
    * Command line: run `mvn verify exec:java`.
    * In VSCode: 
        1. Open Command Palette and run "Maven: Execute commands".
        2. Execute the custom goal `verify exec:java`.
    * In IDEA:
        1. Open Maven Panel and Execute Maven Goal `verify exec:java`.

The console should show the Maven build and testing process and the output of the program as it:
 
* Creates an index, possibly deleting the existing index.
* Runs the indexing task.
* Executes simple and advanced queries.
* Looks up a specific document.
* Performs a suggest query, which is used in type-ahead use-cases.

Finally, the Maven process should exit with a success message. 

## Key concepts

The app specifies a number of domain classes whose structure mirrors the index of the Hotels dataset. This index shows the use of complex types in Azure Search, such as the `Address` and `Room` types. 

The `SearchServiceHelper` class defines methods that help querying Azure Search. The `SearchIndexClient` uses these methods to accomplish the various tasks.

The files `SearchOptions` and `SuggestOptions` use the Builder pattern to compose the various query parameters. These classes and their associated testing classes may be of use in your own code. 

    
## Next steps

You can learn more about Azure Search on the [official documentation site](https://docs.microsoft.com/azure/search).
