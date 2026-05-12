# Methodology

This chapter describes how the content of D4.1 was produced during the T4.2 stock-taking phase of WP4. Its purpose is to make the working method behind the deliverable visible, so that readers can assess the rigour and completeness of the specifications that follow, and so that other Large Scale Pilots can, if they wish, replicate or adapt the approach.

The methodology behind D4.1 is the combined result of three activities that ran in parallel during the stock-taking phase. First, a **consolidation activity** through which the initial ideas contributed by the UC leads were turned into a coherent set of 11 accepted use cases. Second, a **stakeholder engagement activity** through which UC leads identified and involved the partners that each use case needs (credential issuers, relying parties, wallet providers, and others). Third, a **specification activity** through which the use case descriptions were progressively enriched, first via a lightweight metadata spreadsheet and then via a standardised specification template designed by GRNET and filled by each UC lead.

The diagram below summarises the process that led from the initial UC ideas to the detailed specifications presented in this deliverable. Blue steps are activities owned by the individual UC leads; orange steps are coordination activities owned by GRNET acting as the WP4 coordinator; green steps represent the three state transitions of the UC set (initial pool, final accepted set, and detailed specifications).

```mermaid
%%| fig-width: 300px
flowchart TD
    A["UC Leads propose initial use case ideas"] --> B["UC Leads identify and engage the required partners<br/>(credential issuers, relying parties, wallet providers, ...)"]
    B --> C["Initial pool: 28 candidate use cases"]
    C --> D{"WP4 consolidation<br/>led by GRNET"}
    D -->|"merge overlapping UCs"| E["Merged / deduplicated UCs"]
    D -->|"group related travel episodes"| F["UCs united under SEDIT-X"]
    E --> G["Final set:<br/>11 accepted use cases"]
    F --> G
    G --> H["Lightweight spreadsheet per UC:<br/>basic metadata, high-level description, actors"]
    H --> I["GRNET designs the standardised UC template:<br/>metadata list, field descriptions, exemplary values"]
    I --> J["UC Leads fill the template for their own UC"]
    J --> K["Detailed UC specifications<br/>(Chapter 8 and Annex A of D4.1)"]

    classDef leadStep fill:#E8F0FE,stroke:#3B78E7,color:#000
    classDef wp4Step fill:#FFF4E5,stroke:#F5A623,color:#000
    classDef outputStep fill:#E6F4EA,stroke:#34A853,color:#000

    class A,B,J leadStep
    class D,E,F,H,I wp4Step
    class C,G,K outputStep
```

The chapter is organised as follows. Section @sec-3_1 describes the stock-taking and analysis approach, explaining how the 11 use cases were arrived at and how the analysis was structured. Section @sec-3_2 reports on stakeholder involvement, with a dedicated subsection for each of the 11 use cases so that the reader can trace, for every UC, who was consulted and by which means. Section @sec-3_3 lists the sources and tools that supported the work, again broken down per use case to make the evidence base explicit.
