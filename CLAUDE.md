# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Important Git Workflow Policy

**CRITICAL:** Do NOT commit any changes to git until the user explicitly asks you to commit. The user will review all changes first and then request commits when ready. This includes:
- Do NOT run `git add` commands
- Do NOT run `git commit` commands
- Do NOT run `git push` commands
- Only create commits when user explicitly says "commit" or "create a commit"

## Repository Overview

This is "Ciencia de Datos Hidrometeorológicos con Python" (Hydrometeorological Data Science with Python), an interactive educational book built using the Project Pythia Cookbook framework. The project teaches atmospheric and climate data analysis using Python, with applications specific to Latin America and Colombia.

**Important Context:**
- Content is primarily in Spanish, targeting Latin American students and researchers
- Part of the Project Pythia ecosystem (https://projectpythia.org/)
- Licensed under Apache 2.0 (code) and CC BY 4.0 (content)
- Published to GitHub Pages via automated workflows

## Architecture

**MyST-based Book System:**
- Built with MyST (Markedly Structured Text) - a Jupyter Book variant
- Jupyter notebooks are the primary content format
- Configuration in `myst.yml` controls book structure, metadata, and build settings
- GitHub Actions handle automated building and deployment

**Content Organization:**
- `notebooks/1.fundamentos/` - Python fundamentals (adapted from Pythia Foundations)
- `notebooks/2.acceso-datos/` - Accessing IDEAM stations, radars, GFS models
- `notebooks/3.Aplicaciones/` - Scientific applications: ENSO, ERA5, radar QVPs/QPE
- `notebooks/data/` - Sample datasets (radar RAWDSX2, SST NetCDF, station CSVs)
- `notebooks/images/` - Logos and educational images
- `notebooks/notebook-template.ipynb` - Standard template for new notebooks

**Key Dependencies:**
- Scientific stack: NumPy, Pandas, Xarray (>= 3.12), Zarr >= 3.0
- Atmospheric tools: xradar (PyART successor), cmweather, cartopy, siphon
- Cloud data: gcsfs, s3fs, boto3, intake-esm, obstore
- Custom: raw2zarr (installed from git for radar data processing)

## Development Commands

**Environment Setup:**
```bash
conda env create -f environment.yml
conda activate cdh-python
```

**Local Development:**
```bash
cd notebooks/
jupyter lab  # Interactive notebook editing
```

**Building the Book:**
```bash
myst build --html                    # Build HTML version
myst build --html --execute          # Build with notebook execution (slow)
myst clean                           # Clean build artifacts
```

**Testing in Cloud:**
- Binder URL: https://binder.projectpythia.org/v2/gh/ProjectPythia/AtmosCol-2023/main?labpath=notebooks
- Use this to verify notebooks work in clean environment

## GitHub Actions Workflows

**publish-book.yaml (on push to main):**
- Triggers on commits to main branch
- Uses `ProjectPythia/cookbook-actions/.github/workflows/build-book.yaml@main`
- Builds with `myst build --html` (notebooks NOT executed during build)
- Deploys to GitHub Pages automatically

**nightly-build.yaml (daily at 00:00 UTC):**
- Runs complete build and link checker
- Only runs for ProjectPythia org (not forks)
- Useful for catching broken external links

**Important:** This repository uses `execute_notebooks: "off"` in myst.yml, meaning notebooks are NOT executed during GitHub Actions builds. This differs from standard Pythia Cookbook practice where notebooks are auto-executed. When contributing, verify notebooks run cleanly but strip outputs before committing.

## Working with Notebooks

**Adding/Modifying Notebooks:**

1. Use `notebooks/notebook-template.ipynb` as starting point
2. Follow Project Pythia structure:
   - Title with top-level `#` header
   - Overview section listing learning objectives
   - Prerequisites table (concepts, importance, notes)
   - Time estimate and system requirements
   - Imports section up front
   - Clear subsections with `##` and `###` headers
   - Summary and "What's next?" sections
   - Resources/references with proper citations

3. **IMPORTANT - Notebook Execution Policy:**
   - Test notebooks locally by executing fully: `Kernel > Restart Kernel and Run All Cells...`
   - Verify no errors occur
   - **Strip outputs before committing:** `Kernel > Restart Kernel and Clear All Outputs...`
   - Rationale: GitHub Actions automatically execute notebooks during build
   - For local testing with execution: `myst start --execute`

4. Add to book structure in `myst.yml`:
   - Edit `project.toc` section
   - Notebooks organized under `title` sections with `children` lists
   - Path relative to repo root (e.g., `file: notebooks/3.Aplicaciones/3.5.QPE.ipynb`)

**Data Files:**

Follow Project Pythia data management hierarchy:
1. **Preferred:** Remote access via Xarray/Siphon/Intake (e.g., OPENDAP, AWS Open Data)
2. **Acceptable:** Direct commit if <50MB and properly licensed
3. **Alternative:** Generate sample data programmatically
4. **Last resort:** Contact Project Pythia for Jetstream2 Object Store access

Current data in `notebooks/data/`:
- `CAR220809191504.RAWDSX2` - Proprietary radar format (4.2MB)
- `sst.mnmean.nc` - Sea surface temperature NetCDF (62MB)
- `radar_locations.csv` - Colombian radar network stations
- `ds.zarr/` - Zarr chunked array store (untracked)

**Notebook Development Notes:**
- Spanish is primary language; maintain consistency
- Include educational context for Latin American climate/data sources
- Use admonitions (Info/Success/Warning/Danger) for key points
- Avoid code comments as narrative; use Markdown cells instead
- Link to external Pythia Foundations content where appropriate

## MyST Configuration (myst.yml)

**Critical settings:**
- `execute_notebooks: "off"` - Notebooks must be pre-executed
- `template: book-theme` - Uses Pythia book theme
- `jupyter.binder` config points to projectpythia.org Binder instance
- Table of contents (`project.toc`) controls book structure and navigation

**Modifying Table of Contents:**
The TOC uses nested structure:
```yaml
toc:
  - file: README.md
  - title: Section Name
    children:
      - file: notebooks/path/to/notebook.ipynb
```

## Key Technologies

**Data Formats:**
- NetCDF4/HDF5 - Climate datasets (ERA5, GFS, SST)
- Zarr - Cloud-optimized chunked arrays
- RAWDSX2 - Colombian radar proprietary format
- CSV - Station metadata

**Cloud Data Access:**
- OPENDAP protocol for remote dataset access
- AWS S3 and Google Cloud Storage via boto3/gcsfs
- Intake-ESM catalogs for CMIP6 climate model data

**Visualization:**
- Matplotlib/Cartopy - Static maps and plots
- HVPlot - Interactive web-based visualizations
- Datashader - Large dataset rendering
- cmweather - Meteorological colormaps

## Project Pythia Integration

This cookbook follows Project Pythia Cookbook standards:
- Uses shared `cookbook-actions` workflows for CI/CD
- Follows Pythia notebook template structure
- Part of ProjectPythia GitHub organization
- Listed in Pythia Cookbook Gallery
- DOI via Zenodo: https://doi.org/10.5281/zenodo.8316796

**Key Repository Files (per Pythia guidelines):**
- `myst.yml` - Book configuration, TOC, metadata
- `CITATION.cff` - Authorship and citation information
- `_gallery_info.yml` - Thumbnail and tags for gallery discoverability
- `environment.yml` - Conda environment specification
- `README.md` - Repository homepage/description

**Contributing Guidelines:**
- Cookbooks are "living documents" - ongoing updates encouraged
- Use GitHub Issues for improvements and bug reports
- Content must be geoscience-focused and educational
- Link to Pythia Foundations for prerequisite concepts
- Maintain consistency with established style

**Cookbook Guide Reference:**
Full guidelines: https://projectpythia.org/cookbook-guide/

When making significant changes, ensure compatibility with Project Pythia build infrastructure and community standards.

## Custom Agents for Cookbook Development

This project includes specialized agent definitions in `.claude/commands/` for notebook development and quality assurance. These agents help maintain Pythia Cookbook standards and ensure high-quality Spanish educational content.

**Agent Definitions Location:**
- **Source files**: `.claude/commands/*.md` (committed to repository)
- **Active agents**: Installed in `~/.claude/agents/` (global, not tracked in git)

**Why both locations?**
- `.claude/commands/` - Version-controlled definitions for contributors to reference
- `~/.claude/agents/` - Global installation for Claude Code to execute

**Available Agents:**

1. **pythia-compliance-checker** - Validates notebook structure against Pythia standards
   - Checks required sections (overview, prerequisites, summary, etc.)
   - Validates heading hierarchy (one # title, proper ##/### nesting)
   - Verifies prerequisites table format
   - Ensures myst.yml TOC integration

2. **spanish-grammar-reviewer** - Reviews Spanish language quality
   - Grammar, spelling, and accent marks
   - Technical terminology consistency
   - Educational language clarity
   - Bilingual context awareness (Spanish narrative + English code)

3. **notebook-flow-reviewer** - Evaluates pedagogical effectiveness
   - Learning progression and narrative flow
   - Appropriate complexity for audience level
   - Cognitive load assessment
   - Example quality and relevance

4. **data-validator** - Checks data management practices
   - File sizes (<50MB guideline)
   - Remote access preference (OPENDAP, cloud)
   - Data licensing and attribution
   - Jetstream2 Object Store compliance

5. **science-reviewer** - Validates scientific accuracy
   - Atmospheric/climate science correctness
   - Data interpretation and analysis quality
   - Appropriate methods and best practices
   - Domain-specific terminology accuracy

6. **code-quality-checker** - Reviews code execution and style
   - "Restart & Run All" reproducibility
   - Code clarity and organization
   - Binder compatibility
   - Error handling and robustness

7. **accessibility-reviewer** - Ensures inclusive design
   - Alt text for all images
   - Colorblind-friendly visualizations
   - Clear language and definitions
   - Inclusive examples and terminology

8. **metadata-validator** - Validates repository metadata
   - CITATION.cff completeness
   - myst.yml configuration
   - _gallery_info.yml tags and thumbnail
   - Author attribution consistency

9. **bilingual-coordinator** - Manages Spanish/English consistency
   - Terminology translation choices
   - Code vs narrative language separation
   - Link language appropriateness
   - Cultural context preservation

10. **content-creator** - Assists with new notebook creation
    - Generates notebooks from Pythia template
    - Populates standard sections
    - Suggests structure for topic
    - Ensures Pythia compliance from start

**Using Agents:**

Agents are invoked using the Task tool with the `subagent_type` parameter:

```python
# Example: Check notebook compliance
Task(
    subagent_type="pythia-compliance-checker",
    description="Review notebook for Pythia compliance",
    prompt="""
    Review notebooks/3.Aplicaciones/3.1.ENSO.ipynb for compliance with
    Project Pythia Cookbook standards.

    Provide a detailed report with:
    - Compliance score and status
    - Section-by-section checklist
    - Specific issues with cell references
    - Actionable fixes needed
    """
)
```

**Workflow Recommendations:**

1. **Before committing new notebook:**
   - Run `pythia-compliance-checker` for structure
   - Run `spanish-grammar-reviewer` for language quality
   - Run `code-quality-checker` for execution test
   - Run `metadata-validator` to verify myst.yml entry

2. **For content revisions:**
   - Run `notebook-flow-reviewer` for pedagogy
   - Run `science-reviewer` for accuracy
   - Run `accessibility-reviewer` for inclusivity

3. **Before PR to ProjectPythia:**
   - Run `metadata-validator` for repository metadata
   - Run `data-validator` for data compliance
   - Run `bilingual-coordinator` for terminology consistency

**Agent Source Files:**

Original agent specifications can be found in the project at `.claude/commands/` for reference, but the active agents are installed in `~/.claude/agents/` for use across multiple projects.