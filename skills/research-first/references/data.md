# Data, Analysis & ML Reference

Domain-specific guidance for data tasks (datasets, notebooks, dashboards, ML models, analysis pipelines, BI reports).

## Step 1: Context detection

Check these before searching:

- Existing datasets in the project (`data/`, `datasets/`, connected warehouses)
- Notebooks already written (`notebooks/`, `.ipynb` files)
- BI tools in use (Tableau, Looker, Metabase, Power BI, Mode, Hex)
- Data sources connected (Postgres, BigQuery, Snowflake, S3, Redshift)
- ML framework in use (PyTorch, TensorFlow, scikit-learn, Hugging Face Transformers)
- Existing models or embeddings (`models/`, HF cache, MLflow registry)

**Domain-fit guidance** - use existing infra as the starting point:

- Data already lives in BigQuery -> start with SQL. Suggest a notebook only if the analysis genuinely requires it.
- Team has Tableau / Looker / Metabase -> add a view or report there. Suggest a new tool only if the existing one can't support the need.
- Project uses Hugging Face -> search for existing models first. Fine-tuning only if nothing off-the-shelf is close enough.
- Team uses Jupyter -> add a notebook; don't introduce a new notebook tool (Quarto, Observable) unless there's a clear gap.

## Step 2b: Web search patterns

- `"open dataset {domain} {year}"` - public datasets
- `"kaggle {problem} dataset"` - Kaggle datasets and notebooks
- `"huggingface {model/dataset} {task}"` - ML models and datasets
- `"{analysis type} notebook template github"` - reusable notebooks
- `"papers with code {problem}"` - state-of-the-art benchmarks with code
- `"site:arxiv.org {topic}"` - academic papers

## Step 2c: Reusable patterns and templates

- **Analysis templates**: EDA notebooks on Kaggle (most popular competitions have reference EDAs with thousands of upvotes).
- **Visualization notebooks**: Observable, Kaggle, NBViewer examples.
- **Methodologies**: CRISP-DM (data mining), OSEMN (obtain/scrub/explore/model/interpret), DMAIC (Six Sigma for process data).
- **Model cards & dataset cards**: Hugging Face convention for documenting models and datasets (use this format even outside HF).

## Step 5: Execution guidance for data/analysis

- Import the found dataset or notebook first.
- Adapt existing code to the specific data shape before writing new analysis logic.
- Cite the dataset and model source (with exact version/revision if available).
- For ML: check the model's license - many HF models are non-commercial or research-only.
- Reproduce the reference notebook's baseline metric before trying to improve it.

## Key resource lists (data/ML)

**Datasets:**
- [Kaggle](https://kaggle.com) - datasets, notebooks, competitions
- [Hugging Face Datasets](https://huggingface.co/datasets) - ML-ready datasets
- [Google Dataset Search](https://datasetsearch.research.google.com) - public datasets across all domains
- [Awesome Public Datasets](https://github.com/awesomedata/awesome-public-datasets)
- [Data.gov](https://data.gov) - US government datasets
- [data.europa.eu](https://data.europa.eu) - EU open data

**Models:**
- [Hugging Face Models](https://huggingface.co/models) - pretrained models by task
- [Papers With Code](https://paperswithcode.com) - state-of-the-art with implementations
- [Ollama library](https://ollama.com/library) - local LLMs

**Notebooks and analysis:**
- Kaggle Notebooks (sort by votes for canonical EDAs)
- [NBViewer](https://nbviewer.org) - shared Jupyter notebooks
- [Google Colab](https://colab.research.google.com) - shared notebooks
- GitHub `.ipynb` search

**Forums:**
- Reddit: r/datascience, r/MachineLearning, r/learnmachinelearning, r/statistics, r/dataengineering, r/LocalLLaMA
- Kaggle Discussions (very high signal for specific competitions)
- Hugging Face forums
- Papers With Code community
