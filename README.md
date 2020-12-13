# CAB-FAIR-PRICE-PREDICTION

## Table of Content

  * [Overview](#overview)
  * [Motivation](#motivation)
  * [Technical Aspect](#technical-aspect)
  * [Installation](#installation)
  * [Run](#run)
  * [Directory Tree](#directory-tree)
  * [To Do](#to-do)
  * [Bug / Feature Request](#bug---feature-request)
  * [Technologies Used](#technologies-used)
  * [Team](#team)
  * [Credits](#credits)
  
  ## Overview
  This is a simple image classification Flask app trained on the top of Keras API. The trained model (`app/model/model.h5`) takes an image (Indian Paper Currency) as an input and predict the class of image from __10, 20, 50, 100, 200, 500, 2000__ denomination.

## Motivation
What could be a perfect way to utilize unfortunate lockdown period? Like most of you, I spend my time in cooking, Netflix, coding and reading some latest research papers on weekends. The idea of classifying indian currency struck to me when I was browsing through some research papers. I couldn't find any relevant research paper (and of course dataset!) associated with it. And that led me to collect the images of Indian currency to train a deep learning model using [this](https://github.com/hardikvasa/google-images-download) amazing tool.

## Technical Aspect
This project is divided into two part:
1. Training a deep learning model using Keras. (_Not covered in this repo. I'll update the link here once I make it public._)
    - A user can choose image from a device or capture it using a pre-built camera.
    - Used __Amazon S3 Bucket__ to store the uploaded image and predictions.
    - Used __CSRF Token__ to protect against CSRF attacks.
    - Used __Sentry__ to catch the exception on the back-end.
    - After uploading the image, the predictions are displayed on a __Bar Chart__.
## Installation
    The Code is written in Python 3.7. If you don't have Python installed you can find it [here](https://www.python.org/downloads/). If you are using a lower version of Python you can upgrade using the pip package, ensuring you have the latest version of pip. To install the required packages and libraries, run this command in the project directory after [cloning](https://www.howtogeek.com/451360/how-to-clone-a-github-repository/) the repository:
```bash
pip install -r requirements.txt
```
## Run
> STEP 1
#### Linux and macOS User
Open `.bashrc` or `.zshrc` file and add the following credentials:
```bash
export AWS_ACCESS_KEY="your_aws_access_key"
export AWS_SECRET_KEY="your_aws_secret_key"
export ICP_BUCKET='your_aws_bucket_name'
export ICP_BUCKET_REGION='bucket_region'
export ICP_UPLOAD_DIR='bucket_path_to_save_images'
export ICP_PRED_DIR='bucket_path_to_save_predictions'
export ICP_FLASK_SECRET_KEY='anything_random_but_unique'
export SENTRY_INIT='URL_given_by_sentry'
```
Note: __SENTRY_INIT__ is optional, only if you want to catch exceptions in the app, else comment/remove the dependencies and code associated with sentry in `app/main.py`

#### Windows User
Since, I don't have a system with Windows OS, here I collected some helpful resource on adding User Environment Variables in Windows.

__Attention__: Please perform the steps given in these tutorials at your own risk. Please don't mess up with the System Variables. It can potentially damage your PC. __You should know what you're doing__. 
- https://www.tenforums.com/tutorials/121855-edit-user-system-environment-variables-windows.html
- https://www.onmsft.com/how-to/how-to-set-an-environment-variable-in-windows-10

> STEP 2

To run the app in a local machine, shoot this command in the project directory:
```bash
gunicorn wsgi:app
```


## Directory Tree 
```
├── app 
│   ├── __init__.py
│   ├── main.py
│   ├── model
│   ├── static
│   └── templates
├── config
│   ├── __init__.py
├── processing
│   ├── __init__.py
├── requirements.txt
├── runtime.txt
├── LICENSE
├── Procfile
├── README.md
└── wsgi.py
```

## To Do
1. Convert the app to run without any internet connection, i.e. __PWA__.
2. Add a better vizualization chart to display the predictions.

## Bug / Feature Request
If you find a bug (the website couldn't handle the query and / or gave undesired results), kindly open an issue [here](https://github.com/rowhitswami/Indian-Currency-Prediction/issues/new) by including your search query and the expected result.

If you'd like to request a new function, feel free to do so by opening an issue [here](https://github.com/rowhitswami/Indian-Currency-Prediction/issues/new). Please include sample queries and their corresponding results.

## Technologies Used

![](https://forthebadge.com/images/badges/made-with-python.svg)

[<img target="_blank" src="https://keras.io/img/logo.png" width=200>](https://keras.io/) [<img target="_blank" src="https://flask.palletsprojects.com/en/1.1.x/_images/flask-logo.png" width=170>](https://flask.palletsprojects.com/en/1.1.x/) [<img target="_blank" src="https://number1.co.za/wp-content/uploads/2017/10/gunicorn_logo-300x85.png" width=280>](https://gunicorn.org) [<img target="_blank" src="https://www.kindpng.com/picc/b/301/3012484.png" width=200>](https://aws.amazon.com/s3/) 

[<img target="_blank" src="https://sentry-brand.storage.googleapis.com/sentry-logo-black.png" width=270>](https://www.sentry.io/) [<img target="_blank" src="https://openjsf.org/wp-content/uploads/sites/84/2019/10/jquery-logo-vertical_large_square.png" width=100>](https://jquery.com/)

## Team
[![Sanyam Gujral](/https://github.com/settings/profile)](https://gujralsanyam22.com/) |
-|
[![Sanyam Gujral](https://gujralsanyam22.com/) |)


## Credits
- [Google Images Download](https://github.com/hardikvasa/google-images-download) - This project wouldn't have been possible without this tool. It saved my enormous amount of time while collecting the data. A huge shout-out to its creator [Hardik Vasa](https://github.com/hardikvasa).

