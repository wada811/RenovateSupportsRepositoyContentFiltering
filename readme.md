# RenovateSupportsRepositoyContentFiltering

This repository is repoduction that Renovate supports Repository content filtering of predefined registry in Gradle. 

See Also:
[renovatebot/renovate#14589](https://github.com/renovatebot/renovate/issues/14589) Support repository content filtering of predefined registry in Gradle

## Reproduction

1. Fork this repository.
2. Self hosting with docker below this configuration.
    ```
    module.exports = {
      token: 'your token',
      repositories: ['you/RenovateSupportsRepositoyContentFiltering'],
    };
    ```
3. Run [wada811/renovate/feat/14589-support-repository-content-filtering](https://github.com/wada811/renovate/tree/feat/14589-support-repository-content-filtering)

    If you want to debug, run Run [wada811/renovate/debug/14589-support-repository-content-filtering](https://github.com/wada811/renovate/tree/debug/14589-support-repository-content-filtering)
4. PRs is created.

## Debug log

### tokens 

```
DEBUG: tryMatch: packageFile: settings.gradle (repository=wada811/RenovateSupportsRepositoyContentFiltering)
       "tokens": [
         {"type": "word", "offset": 448, "value": "google"},
         {"type": "leftBrace", "offset": 455, "value": "{"},
         {"type": "word", "offset": 469, "value": "content"},
         {"type": "leftBrace", "offset": 477, "value": "{"},
         {"type": "word", "offset": 495, "value": "includeGroupByRegex"},
         {"type": "string", "value": "androidx\\..*", "offset": 516},
         {"type": "word", "offset": 547, "value": "includeGroupByRegex"},
         {"type": "string", "value": "com\\.android.*", "offset": 568},
         {"type": "word", "offset": 601, "value": "includeGroupByRegex"},
         {"type": "string", "value": "com\\.google\\..*", "offset": 622},
         {"type": "rightBrace", "offset": 653, "value": "}"},
         {"type": "rightBrace", "offset": 663, "value": "}"},
         {"type": "word", "offset": 673, "value": "maven"},
         {"type": "leftBrace", "offset": 679, "value": "{"},
         {"type": "word", "offset": 693, "value": "url"},
         {"type": "string", "value": "https://jitpack.io", "offset": 698},
         {"type": "word", "offset": 730, "value": "content"},
         {"type": "leftBrace", "offset": 738, "value": "{"},
         {"type": "word", "offset": 756, "value": "includeGroupByRegex"},
         {"type": "string", "value": "com\\.github\\..*", "offset": 777},
         {"type": "rightBrace", "offset": 808, "value": "}"},
         {"type": "rightBrace", "offset": 818, "value": "}"},
         {"type": "word", "offset": 828, "value": "mavenCentral"},
         {"type": "leftParen", "offset": 840, "value": "("},
         {"type": "rightParen", "offset": 841, "value": ")"},
         {"type": "rightBrace", "offset": 847, "value": "}"},
         {"type": "rightBrace", "offset": 849, "value": "}"},
         {"type": "word", "offset": 851, "value": "rootProject"},
         {"type": "dot", "offset": 862, "value": "."},
         {"type": "word", "offset": 863, "value": "name"},
         {"type": "assignment", "offset": 868, "value": "="},
         {
           "type": "string",
           "value": "RenovateRepositoryContentFiltering",
           "offset": 871
         },
         {"type": "word", "offset": 907, "value": "include"},
         {"type": "string", "offset": 916, "value": ":app"}
       ]
```

### matcher, tokenMap

```
DEBUG: tryMatch: packageFile: settings.gradle (repository=wada811/RenovateSupportsRepositoyContentFiltering)
       "matchers": [
         {
           "matchType": "word",
           "matchValue": ["mavenCentral", "jcenter", "google", "gradlePluginPortal"],
           "tokenMapKey": "registryName"
         },
         {"matchType": "leftBrace"},
         {"matchType": "word", "matchValue": ["content"]},
         {"matchType": "leftBrace", "lookahead": true}
       ],
       "tokenMap": {"registryName": {"type": "word", "offset": 448, "value": "google"}}
```


### registryUrl

```
DEBUG: extractAllPackageFiles: registryUrl: https://dl.google.com/android/maven2/ (repository=wada811/RenovateSupportsRepositoyContentFiltering)
DEBUG: extractAllPackageFiles: registryUrl: https://plugins.gradle.org/m2/ (repository=wada811/RenovateSupportsRepositoyContentFiltering)
DEBUG: extractAllPackageFiles: registryUrl: https://repo.maven.apache.org/maven2 (repository=wada811/RenovateSupportsRepositoyContentFiltering)
DEBUG: extractAllPackageFiles: registryUrl: https://dl.google.com/android/maven2/ (repository=wada811/RenovateSupportsRepositoyContentFiltering)
DEBUG: extractAllPackageFiles: registryUrl: https://jitpack.io (repository=wada811/RenovateSupportsRepositoyContentFiltering)
DEBUG: extractAllPackageFiles: registryUrl: https://repo.maven.apache.org/maven2 (repository=wada811/RenovateSupportsRepositoyContentFiltering)
```

### Full

[debug.log](https://raw.githubusercontent.com/wada811/RenovateSupportsRepositoyContentFiltering/main/debug.log)
