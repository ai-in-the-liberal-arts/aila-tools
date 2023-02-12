+++
title = "Using Google Cloud Auto ML"
description = "Auto ML is a web-browser based machine learning modeling system for developers (or budding developers) with limited machine learning expertise to train high-quality models specific to their business needs."
date = 2022-04-14
[extra]
author = "Lemara Williams"
+++

Auto ML is a web-browser based machine learning modeling system for developers (or budding developers) with limited machine learning expertise to train high-quality models specific to their business needs.
![image|690x201](upload://hz29vczrRAnOX5ScdM3NM0nxT93.png)

A short introductory video can be found at this [link](https://www.youtube.com/watch?v=GbLQE2C181U) using AutoML Vision as an example.

This service provided by Google is not completely free, however there is a free tier available that will be useful to most people's needs.

## What's in AutoML

Auto ML consists of 4 categories to help with deciphering what you would like to analyze in your project: Vertex AI, Sight, Language, and Structured Data.

Vertex AI: A unified platform for all of Auto ML and also custom code training and all your models are stored in one central model repository.

Sight: AutoML Image (object detection and image classification) and AutoML Video (content discovery and engaging video experiences)

Language: AutoML Text (classify text data, extract information, or understand the sentiment of authors) and AutoML Translation (dynamically detect and translate between languages)

Structured Data: AutoML Tabular (use regression to find a numeric value, or use classification to predict a categorical outcome from your tabular data)

## How Much Does AutoML cost?

When you first sign up for AutoML, you automatically get enrolled in the 90 day, $300 free trial. The Free Trial credits apply to all Google Cloud resources, with some exceptions: you can't add GPUs to your virtual machine (VM) instances, you can't request a quota increase, and you can't create VM instances that are based on Windows Server images.

After your free trial ends you have to upgrade to a paid Cloud Billing account, however you can still stay within the free tier. The free tier consists of:

* [ **AutoML Natural Language** ](https://cloud.google.com/natural-language/automl/docs)
  * 5000 units of prediction per month
* [ **AutoML Tables** ](https://cloud.google.com/automl-tables/docs)
  * 6 node hours for training and prediction
* [ **AutoML Translation** ](https://cloud.google.com/translate/automl/docs)
  * 500,000 translated characters per month
* [ **AutoML Video Intelligence** ](https://cloud.google.com/video-intelligence/automl/docs)
  * 40 node hours for training
  * 5 node hours for prediction
* [ **AutoML Vision** ](https://cloud.google.com/vision/automl/docs)
  * 40 node hours for training and online prediction
  * 1 node hour for batch classification prediction
  * 15 node hours for Edge training

After that, the cost is calculated per node hour. If you want more information on cost, or would like to discuss whether your data set will exceed the free tier feel free to contact any of the student assistants.

# Signing Up + Tutorial

To sign up for AutoML, you can start at this [link](https://console.cloud.google.com/freetrial/signup/tos?_ga=2.144746292.1687972180.1632594753-2044124437.1631467286&_gac=1.227715823.1631654677.CjwKCAiAv4n9BRA9EiwA30WND3eT5AUBRTtmGzkBIIrXQkgWXRIJQaYm7jPZhJbLXY7g-XnG2vZAPhoCJfYQAvD_BwE).

When you get to the link follow the steps to sign up, follow the steps on each screen to input all your information. On the last screen you do need to input your card information, but you will not be charged in accordance with the free trial. A note: you cannot use an Amherst email to sign up.

![](upload://yBnK6pQqBz9FK9XiVbz9rumpeTd.png)

After signing up you should land on your home page. Welcome to the Google Cloud Platform!

![](upload://tnfk8ea5AF8X5rhSyUrxkcdmLDV.png)

Press "Select a project" on the upper left of the tap toolbar and select your first project or create a new one!

![](upload://kzzRbtv150UcNaxqq5u2x9XFoKx.png)

It brings you back to the same home page as before. Use the menu at the left to bring down all products and scroll until you see Vertex AI. Clicking "Vertex AI" will bring you to the Vertex AI dashboard. Click "Enable Vertex AI API" to get your account ready to run it.

After that, you can start preparing your training data. Click "Create Dataset" under "Prepare your training data."

We will show some of the capabilities of Vertex AI by running a classification on tabular data.

![](upload://me8rC4hcMBCXkr37trvJJyi7uoa.png)

To upload your data you could either upload a CSV file from your computer or Google Cloud, or upload a table or view from BigQuery (another Google Cloud service).

![](upload://oTrBS2MQWMBX3UsYz2qLBkvy4gX.png)

After being uploaded your data will be trained when you click "Train New Model" and you will receive an email to the address you used to sign up when the model has been trained successfully or if it failed and why.

![](upload://dbtVsnsKa3Sg8ZhZWzhIGiqNThj.png)

When you go back to Vertex AI to see your results and here you can dig into all the details that resulted from the test!

![](upload://xg6LIfsjhP1ADIxI4yyIsLV845Z.png)
If you have any questions on specific concepts or terminology please leave a comment!
