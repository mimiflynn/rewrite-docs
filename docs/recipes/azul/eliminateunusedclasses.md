---
sidebar_label: "Eliminate unused classes"
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Eliminate unused classes

**io.moderne.azul.EliminateUnusedClasses**

_Deprecate and later delete classes that are unused, as detected by Azul Intelligence Cloud._

## Recipe source

This recipe is only available to users of [Moderne](https://docs.moderne.io/).


This recipe is available under the [Moderne Proprietary License](https://docs.moderne.io/licensing/overview).

## Options

| Type | Name | Description | Example |
| -- | -- | -- | -- |
| `URL` | azulUrl | 'Azul Intelligence Cloud endpoint. | `https://YOUR_ENDPOINT.azul.com` |
| `String` | azulApiKey | API key used to make REST requests to Azul Intelligence Cloud. | `YOUR-API-KEY` |
| `String` | markDeprecatedAfter | *Optional*. Classes that haven't been used in this duration will be marked deprecated but not yet for removal. Defaults to P4W | `P4W` |
| `String` | markForRemovalAfter | *Optional*. Classes that haven't been used in this duration will be marked deprecated and for removal. Defaults to P1Y | `P3M` |
| `String` | removeAfter | *Optional*. Classes that haven't been used in this duration will be removed. Defaults to P2Y | `P1Y` |


## Usage

This recipe has required configuration parameters and can only be run by users of Moderne.
To run this recipe, you will need to provide the Moderne CLI run command with the required options. 
Or, if you'd like to create a declarative recipe, please see the below example of a `rewrite.yml` file:

```yaml title="rewrite.yml"
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.EliminateUnusedClassesExample
displayName: Eliminate unused classes example
recipeList:
  - io.moderne.azul.EliminateUnusedClasses: 
      azulUrl: https://YOUR_ENDPOINT.azul.com
      azulApiKey: YOUR-API-KEY
      markDeprecatedAfter: P4W
      markForRemovalAfter: P3M
      removeAfter: P1Y
```

<Tabs groupId="projectType">
<TabItem value="moderne-cli" label="Moderne CLI">

You will need to have configured the [Moderne CLI](https://docs.moderne.io/user-documentation/moderne-cli/getting-started/cli-intro) on your machine before you can run the following command.

```shell title="shell"
mod run . --recipe EliminateUnusedClasses --recipe-option "azulUrl=https://YOUR_ENDPOINT.azul.com" --recipe-option "azulApiKey=YOUR-API-KEY" --recipe-option "markDeprecatedAfter=P4W" --recipe-option "markForRemovalAfter=P3M" --recipe-option "removeAfter=P1Y"
```

If the recipe is not available locally, then you can install it using:
```shell
mod config recipes jar install org.openrewrite.recipe:rewrite-azul:{{VERSION_ORG_OPENREWRITE_RECIPE_REWRITE_AZUL}}
```
</TabItem>
</Tabs>

## See how this recipe works across multiple open-source repositories

import RecipeCallout from '@site/src/components/ModerneLink';

<RecipeCallout link="https://app.moderne.io/recipes/io.moderne.azul.EliminateUnusedClasses" />

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
## Data Tables

<Tabs groupId="data-tables">
<TabItem value="io.moderne.azul.table.ReachableClasses" label="ReachableClasses">

### Reachable classes
**io.moderne.azul.table.ReachableClasses**

_Classes in a repository's source code that are reachable. This data table does not contain information about reachability in libraries._

| Column Name | Description |
| ----------- | ----------- |
| Class name | The fully qualified name of the class that is reachable. |
| Last used | The date and time when the method was last used. |
| AppEnv | The 'AppEnv' as defined by Azul Intelligence Cloud. |

</TabItem>

<TabItem value="org.openrewrite.table.SourcesFileResults" label="SourcesFileResults">

### Source files that had results
**org.openrewrite.table.SourcesFileResults**

_Source files that were modified by the recipe run._

| Column Name | Description |
| ----------- | ----------- |
| Source path before the run | The source path of the file before the run. `null` when a source file was created during the run. |
| Source path after the run | A recipe may modify the source path. This is the path after the run. `null` when a source file was deleted during the run. |
| Parent of the recipe that made changes | In a hierarchical recipe, the parent of the recipe that made a change. Empty if this is the root of a hierarchy or if the recipe is not hierarchical at all. |
| Recipe that made changes | The specific recipe that made a change. |
| Estimated time saving | An estimated effort that a developer to fix manually instead of using this recipe, in unit of seconds. |
| Cycle | The recipe cycle in which the change was made. |

</TabItem>

<TabItem value="org.openrewrite.table.SourcesFileErrors" label="SourcesFileErrors">

### Source files that errored on a recipe
**org.openrewrite.table.SourcesFileErrors**

_The details of all errors produced by a recipe run._

| Column Name | Description |
| ----------- | ----------- |
| Source path | The file that failed to parse. |
| Recipe that made changes | The specific recipe that made a change. |
| Stack trace | The stack trace of the failure. |

</TabItem>

<TabItem value="org.openrewrite.table.RecipeRunStats" label="RecipeRunStats">

### Recipe performance
**org.openrewrite.table.RecipeRunStats**

_Statistics used in analyzing the performance of recipes._

| Column Name | Description |
| ----------- | ----------- |
| The recipe | The recipe whose stats are being measured both individually and cumulatively. |
| Source file count | The number of source files the recipe ran over. |
| Source file changed count | The number of source files which were changed in the recipe run. Includes files created, deleted, and edited. |
| Cumulative scanning time (ns) | The total time spent across the scanning phase of this recipe. |
| 99th percentile scanning time (ns) | 99 out of 100 scans completed in this amount of time. |
| Max scanning time (ns) | The max time scanning any one source file. |
| Cumulative edit time (ns) | The total time spent across the editing phase of this recipe. |
| 99th percentile edit time (ns) | 99 out of 100 edits completed in this amount of time. |
| Max edit time (ns) | The max time editing any one source file. |

</TabItem>

</Tabs>
