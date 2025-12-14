# Universal Grammar Generative Model

This project simulates syntax acquisition using a neuro-symbolic generative model. It combines a probabilistic model of Universal Grammar (UG) with a neural network “innate solver” to learn grammar parameters from sentences.

## Prerequisites

1. **Julia**: You need to have Julia installed (v1.9 or higher recommended).  
   [Download Julia here](https://julialang.org/downloads/).

2. **Jupyter Notebook**: Required to run the `.ipynb` file.

## Setup & Installation

To set up the project environment and install all necessary packages (including `Gen.jl`), follow these steps:

1. Open your terminal/command prompt in this project folder.  
2. Start Julia by typing:

   ```bash
   julia
   ```

3. Run the following commands in the Julia REPL to create the environment and install dependencies:

   ```julia
   using Pkg
   Pkg.activate("psyc261")
   Pkg.add([
       "Gen",
       "Distributions",
       "Plots",
       "StatsPlots",
       "JLD2",
       "ProgressMeter",
       "Parameters",
       "PyCall",
       "Conda",
       "JSON3",
       "StatsBase",
       "Random"
   ])
   ```

This will generate the `Project.toml` and `Manifest.toml` files automatically.

## How to Run

Open the main notebook **`ug_genmodel_v0.ipynb`** in Jupyter. The project is controlled by two main toggles near the top of the notebook:

### 1. Training the Model

If you want to train the neural network solver:

- Set `const TRAIN_MODEL = true` in the notebook.
- Run the cells. This saves the trained parameters to `innate_solver_params.jld2`.

*If you want to use the pre-trained file, leave this as `false` to skip training. The file already contains the correct implementation of the neural network.*

### 2. Running the Simulation

If you want to run the main learning experiment (comparing Naive vs. Guided learning):

- Set `RUN_SMC = true` in the simulation section.
- Run the cells to execute Sequential Monte Carlo (SMC) inference.
- Results will be saved to `smc_results_rejuv.jld2`.

*In the same way as the neural network, a pre-trained file is provided. If you want to use it, leave this as `false` to skip training and the saved file will be used*

### 3. Visualizing Results

- Run the final cells in the notebook to generate the analysis dashboard (learning curves, accuracy plots, etc.).

## File Structure

- **`ug_genmodel.ipynb`** — The main code (Model, Training, Inference, Visualization).  
- **`src/ug_model.jl`** — Helper file containing lexicon and grammar definitions.  
- **`*.jld2`** — Saved data files (neural net weights and simulation results).