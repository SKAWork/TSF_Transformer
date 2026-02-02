# TSF_Transformer
Time series forecasting using transformer architecture

__Introduction__

This project is recommended to be executed using Google Colab.
Google Colab provides a preconfigured environment with GPU support, simplifies dependency management, and integrates seamlessly with interactive notebooks. This setup allows the training pipeline to run without requiring any local installation or hardware configuration.

It is recommended (but not strictly mandatory) to have a Comet ML account in order to enable experiment tracking, metric logging, and result visualization. When provided, Comet ML significantly improves reproducibility and monitoring of the training process.

__I. Execution on Google Colab__
**1) Opening the Notebook**

The notebook can be opened directly in Google Colab either by uploading it manually or by opening it from the GitHub repository using the “Open in Colab” option.

**2) Comet ML API Key Configuration (Recommended)**

To enable experiment tracking, a Comet ML API key should be provided using Google Colab secrets.

The API key must be added in Settings → Secrets with the following name:

COMET_API_KEY

and the corresponding value set to your personal Comet ML API key.
If no API key is provided, experiment logging will be disabled, but the notebook will still execute.

**3) Dataset Preparation**

The input data must consist of one or more CSV files containing Bernstein polynomial coefficients. These files should be grouped locally in a directory named bern/ prior to execution.

**4) Dataset Upload**

During execution, Google Colab will automatically prompt the user to upload the dataset files. At that moment, at least one CSV file from the bern/ directory must be selected and uploaded. The notebook handles data loading and preprocessing internally, without requiring any manual path configuration.

**5) Running the Notebook**

Once the dataset is uploaded and the optional Comet ML configuration is completed, the notebook can be executed sequentially. Training, validation, evaluation, and logging are triggered automatically by the execution flow.

__II. Local Execution (Optional)__
**1) Prerequisites**

To run the notebook locally, the following prerequisites must be installed:

Python 3.9+ (or compatible version)

PyTorch (with or without CUDA, depending on GPU availability)

Additional Python packages:

numpy

pandas

matplotlib

tqdm

comet_ml (optional, for experiment logging)

python-dotenv (to load the Comet ML API key from a .env file)

It is strongly recommended to use a virtual environment (e.g., venv or conda) to isolate dependencies.

**2) Cloning the Repository**

Clone the GitHub repository to your local machine:

git clone <repository_url>
cd <repository_directory>

**3) Installing Dependencies**

Install the required packages using pip:

pip install -r requirements.txt

**4) Comet ML API Key Configuration (Optional)**

To enable experiment logging with Comet ML:

Create a .env file in the root of the project.

Add your Comet ML API key:

COMET_API_KEY=your_personal_comet_api_key


The notebook automatically reads this key using python-dotenv.
If no key is provided, the notebook will run normally, but metrics will not be logged.

**5) Dataset Placement**

Create a local directory named bern/ and place all CSV files containing Bernstein polynomial coefficients inside this folder. The notebook will automatically scan this directory and load all CSV files with the .csv extension.

**6) Running the Notebook**

Open the notebook in Jupyter or your preferred local environment.

Execute cells sequentially to perform data loading, preprocessing, model initialization, training, evaluation, and optional Comet ML logging.

Ensure that the Python environment has double precision (float64) support for accurate polynomial evaluation.