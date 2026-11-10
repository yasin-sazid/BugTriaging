# Bug Triaging through Developer Expertise Retrieval

A Java research prototype for recommending developer expertise for bug reports. The project combines bug history, repository evidence, source-code imports, and text processing to connect an incoming issue with candidate developers.

## Research motivation

Bug assignment depends on more than a developer's name: past fixes, technical vocabulary, and repository experience all provide signals about relevant expertise. This implementation represents those signals as searchable profiles and examines recommendations across experienced developers, newcomers with repository evidence, and fresh graduates.

## Retrieval pipeline

```text
Bug XML + developer history + repository evidence
                         |
             Parsing and text normalization
                         |
             Developer expertise profiles
                         |
             Separate Lucene indexes
                         |
             Bug-keyword queries and ranking
                         |
                Recommendation results
```

`TextProcessor` splits camel-case terms, tokenizes text, removes stop words, and applies Porter stemming. The parser package handles XML, repository listings, Java source imports, and GitHub-derived information. `profiles/` models bugs and developer categories, while `testing/Test` organizes a date-based experiment and Lucene searches.

## Project structure

| Path | Responsibility |
| --- | --- |
| `src/mainPackage/Main.java` | Experiment entry point |
| `src/parser/` | Data acquisition and parsing |
| `src/naturalLanguageProcessor/` | Keyword normalization |
| `src/profiles/` | Domain and expertise models |
| `src/testing/` | Indexing, recommendation, and result aggregation |
| `src/files/` | Supplied data and text resources |

## Explore the experiment

Use a Java IDE with JDK 11 or newer, mark `src/` as the source root, and configure the imported libraries: Apache Lucene, JavaParser, JGit, jsoup, JSON.simple, JDOM, and Snowball stemming. Provision the XML data, repository collections, stop-word list, and Windows working paths referenced by the parser and test classes. Launch `mainPackage.Main` to follow the configured experiment.

The technical contribution is an integrated expertise-retrieval workflow that combines natural-language processing with software-repository evidence and distinguishes candidate groups during recommendation.
