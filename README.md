# TSF_Transformer
Time series forecasting using transformer architecture

Introduction

This project is recommended to be executed using Google Colab.
Google Colab provides a preconfigured environment with GPU support, simplifies dependency management, and integrates seamlessly with interactive notebooks. This setup allows the training pipeline to run without requiring any local installation or hardware configuration.

It is recommended (but not strictly mandatory) to have a Comet ML account in order to enable experiment tracking, metric logging, and result visualization. When provided, Comet ML significantly improves reproducibility and monitoring of the training process.

I. Execution on Google Colab
1) Opening the Notebook

The notebook can be opened directly in Google Colab either by uploading it manually or by opening it from the GitHub repository using the “Open in Colab” option.

2) Comet ML API Key Configuration (Recommended)

To enable experiment tracking, a Comet ML API key should be provided using Google Colab secrets.

The API key must be added in Settings → Secrets with the following name:

COMET_API_KEY

and the corresponding value set to your personal Comet ML API key.
If no API key is provided, experiment logging will be disabled, but the notebook will still execute.

3) Dataset Preparation

The input data must consist of one or more CSV files containing Bernstein polynomial coefficients. These files should be grouped locally in a directory named bern/ prior to execution.

4) Dataset Upload

During execution, Google Colab will automatically prompt the user to upload the dataset files. At that moment, at least one CSV file from the bern/ directory must be selected and uploaded. The notebook handles data loading and preprocessing internally, without requiring any manual path configuration.

5) Running the Notebook

Once the dataset is uploaded and the optional Comet ML configuration is completed, the notebook can be executed sequentially. Training, validation, evaluation, and logging are triggered automatically by the execution flow.