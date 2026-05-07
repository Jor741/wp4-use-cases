# D4.1: UC Specifications and Scenarios

## Editing conventions

Deliverable D4.1 is split into different files, named as follows:

* `N--...md`: Title and introduction of chapter N. The title should be
  written as `# Title`. No other headers should be inserted.

* `M.N--...md`: Title and introduction of section M.N. The title
  should be written as `## Title`. No other headers should be
  inserted.

* `M.N.O--...md`: Title and introduction of section M.N.O. The title
  should be written as `### Title`. Subsections can be added using
  syntax with more hashes, such as `#### Subsection` or `##### Subsection`.

The rules above guarantee that the file naming is consistent with the
final document structure.

Regarding the allowed Markdown syntax, do not use `---` syntax
(horizontal lines).

## Documentation builder

### Docker-based process

Build and start the builder container:

```
docker compose up
```

While the container runs, build the documentation with the following command:

```
docker exec -it doc_builder /D4.1/build.py html   # pdf, docx or leave empty for all
```

### Local installation

#### Setup

1. Install [Quarto](https://quarto.org).

2. Set up the local Python environment:

```
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

#### Use

```
source .venv/bin/activate
python build.py
```
