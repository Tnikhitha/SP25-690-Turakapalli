19/04/2026 11:28 EDT Add general and mathematical comparison to main.ipynb
- Expanded the notebook beyond visual comparison to include a general neural network comparison section
- Added model-level comparison details such as parameter count, skip-connection usage, and denoising strategy
- Added mathematical image comparison metrics including MSE, MAE, PSNR, and SSIM
- Compared baseline output, residual output, and their relationship to the shared noisy input

19/04/2026 11:24 EDT Revise main.ipynb to compare both neural networks
- Replaced the single-model notebook flow with a side-by-side comparison workflow for BaselineCNN and ResidualCNN
- Added repository root detection and direct imports from the local models package
- Configured the notebook to load the same noisy input image and both trained checkpoints
- Saved baseline and residual outputs to results/ and displayed noisy, baseline, and residual images together
- Added a simple output-difference metric to make the model comparison explicit

18/04/2026 00:25 EDT Squash commits into single push
- Used git reset --soft to combine all recent commits into one
- Removed accidentally staged data files to respect .gitignore
- Successfully pushed single commit "Complete repository setup" to GitHub

18/04/2026 00:24 EDT Fix Git push error from large CIFAR-10 file
- Removed cifar-10-python.tar.gz from Git history using git filter-branch
- Removed .gitattributes from LFS tracking and added to .gitignore
- Force pushed to overwrite remote history and resolve 100MB file size limit error

18/04/2026 00:22 EDT Remove data files from Git and update .gitignore
- Removed data files and placeholders from Git tracking: noisy_test.png, noisy_cifar_test.png, denoised_test.png, *_placeholder.txt
- Added data/, results/, training/*.pth, *.png, *_placeholder.txt, .venv/, uv.lock to .gitignore
- Prevents accidental commit of large data files and environment-specific files

18/04/2026 00:20 EDT Fix Colab import error in main.ipynb
- Added BaselineCNN and ResidualCNN class definitions directly in the notebook
- Removed dependency on local models package for Colab compatibility
- Notebook now self-contained and runnable in Google Colab

18/04/2026 00:18 EDT Create main.ipynb for Google Colab
- Converted main.py to Jupyter notebook format (main.ipynb)
- Modified root_dir to use Path.cwd() for Colab compatibility
- Added example usage cell with hardcoded input/output paths
- Removed argparse main block, replaced with direct execution in notebook

18/04/2026 00:12 EDT Add input/output display to main.py
- Added print statements in main() to show input image path, output path, model, image size, checkpoint status, device, and tensor shapes
- Helps with debugging and verifying script execution

18/04/2026 00:15 EDT Add training functionality with CIFAR-10
- Renamed placeholder file `training` to `training_placeholder.txt`
- Created `training/` directory
- Added `training/train.py` script that auto-downloads CIFAR-10, adds Gaussian noise, and trains the CNN models
- Trained residual CNN for 5 epochs on noisy CIFAR-10 data
- Saved trained model checkpoint for use in `main.py`

18/04/2026 00:05 EDT Fix module import under uv run
- Added repo root insertion into `sys.path` at the top of `main.py`
- Ensures `from models.residual_cnn import ResidualCNN` resolves correctly when executed with `uv run`
- Keeps `main.py` argument validation intact for `--input` and `--output`

18/04/2026 00:10 EDT Create data and results directories and test image
- Renamed placeholder files `data` and `results` to `data_placeholder.txt` and `results_placeholder.txt`
- Created `data/` and `results/` directories
- Generated a synthetic noisy test image `data/noisy_test.png` for script testing
- Verified `uv run .\main.py --input .\data\noisy_test.png --output .\results\denoised_test.png` works

18/04/2026 00:00 EDT Fix imports and create models package
- Renamed conflicting root file `models` to `models_placeholder.txt`
- Created `models/` package directory
- Added `models/__init__.py` with exported model classes
- Added `models/baseline_cnn.py` and `models/residual_cnn.py`
- Verified `from models.residual_cnn import ResidualCNN` and `from models.baseline_cnn import BaselineCNN` import successfully
