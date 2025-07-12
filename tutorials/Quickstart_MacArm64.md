## Pre-requisites

- [x] `miniconda` for Macbook M1/M2/M3 (`arm64`)
- [x] `homebrew`, `git`, `XCode`
- [x] Github account and authentication tokens
- [x] VS Code

## Steps

1. Open a Terminal application and `git clone` this repository inside a folder, e.g., `~/summer2025/:

```sh
mkdir -p ~/summer2025;
git clone https://github.com/Summer2025-SPAC/SPAC_Shiny;
cd ~/summer2025/Spacy_Shiny
```
 
2. `git checkout` as branch, e.g.,  `branch_name` on your local repo and create a new branch `gh_iss2_rk`:

```sh
git checkout branch_name;
```

3. Open the folder in VS Code: 

```sh
cd ~/summer2025/Spacy_Shiny;
code ./
``` 

4. Inside the VS Code `terminal`, create a `conda` environment, e.g., `spacy_viz_py39_arm64`: 

```sh
cd ~/summer2025/Spacy_Shiny;
conda deactivate;
conda create -n spacy_viz_py39_arm64 python=3.9 -y;
conda activate spacy_viz_py39_arm64
```

> Install any additional system libraries using `conda` or `homebrew`. Then install the Spacy Visualization package in       editable mode. 
>
> In particular, install tables and c-blsoc2 using `conda` 

```sh
conda install -c conda-forge tables c-blosc2
``` 

> This ensures all dependencies are compatible and already compiled, so no Cython compilation is needed. This avoids the C API mismatch and build errors which you might see with pip.
>
> At the time of writing, the above command installs `tables` version `3.9.2`. Since this command installs tables with `conda`, `requirements.txt` has to be changed to not constrain `tables` to a specific version, so set it to`tables>=3.8.0`, to avoid further installation issues. 
>
> Finally, let pip install the rest of the packages. 

```sh
python3 -m pip install -r requirements.txt
```

5. Assuming all installation works, run the shiny app in the terminal.

```sh
shiny run app.py
```