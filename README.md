# ontogen

**This repository is currently empty.** It contains a `LICENSE` file and nothing
else — no source, no data, no history beyond the single commit that added the
licence.

It is reserved as the intended home of **`autot-onto`**, the 16-stage RAG
pipeline (`autot_30.py`) that authors CycL-style ontologies from source
documents. That code is not here yet.

This README documents that state deliberately, rather than describing a project
the repository does not contain.

## Where the `autot-onto` material actually lives

| Repository | What it holds |
|---|---|
| [`mstupk/ontogen_data`](https://github.com/mstupk/ontogen_data) | The SLURM job script that runs the pipeline, documented in detail — the three-phase priority scheme, model choice, state files, and the self-update helper. The closest thing to a description of the pipeline's behaviour. |
| [`mstupk/cycl-test-ontologies`](https://github.com/mstupk/cycl-test-ontologies) | Stage-by-stage JSON outputs from real pipeline runs, across three model configurations. Shows the 16-stage structure concretely. |
| [`mstupk/oag-pipeline`](https://github.com/mstupk/oag-pipeline) | `_autot_30.py`, a faithful port of the pipeline to the DeepSeek API instead of Ollama. Currently the most complete *source* for the pipeline's logic. |
| [`mstupk/gtdlxrx`](https://github.com/mstupk/gtdlxrx) | The sibling extraction pipeline, modelled on `autot_30.py`. Self-contained, but its `CLAUDE.md` explains the relationship. |

If you are looking for the pipeline implementation, start with
`_autot_30.py` in `oag-pipeline`.

## If you are filling this repository in

The companion repository `ontogen_data` already expects a project layout with
these directories beside the pipeline module:

```
cyc-ref/                   # Cyc reference material — phase 0 input
input-context/             # curated local sources — phase 1 input
input-context-wikipedia/   # bulk Wikipedia downloads — phase 2 input, kept separate on purpose
target-context/            # target-side context DB
pipeline_stages/           # per-stage cache
out-ke/                    # generated .ke ontology rules
```

plus the state files `processed.txt`, `atoms.txt`, `ontology_index.json`,
`cyc_index.json`, `wikitopics.txt`, `wiki_downloaded.txt` and `failed.txt`.

The pipeline is invoked as a module — `python -m autot_30` — so the entry point
belongs in an importable package, not a loose script.

## Licence

CC BY 4.0. See `LICENSE`.
