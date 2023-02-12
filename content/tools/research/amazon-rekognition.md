+++
title = "What is Amazon Rekognition?"
description = "Amazon Rekognition is a cloud-based software as a service computer vision platform that was launched in 2016."
date = 2022-05-12
[extra]
author = "Reihaneh Iranmanesh"
+++

[Amazon Rekognition](https://aws.amazon.com/rekognition/) is a cloud-based software as a service computer vision platform that was launched in 2016. It is the biggest competitor to Google Cloud Vision API. Rekognition provides a number of computer vision capabilities, which can be divided into two categories: Algorithms that are pre-trained on data collected by Amazon or its partners, and algorithms that a user can train on a custom dataset. Amazon Rekognition includes a simple, easy-to-use API that can quickly analyze any image or video file that is stored in Amazon S3, so most of its services require no machine learning expertise to use! In this tutorial, we will mainly focus on three services that Rekognition offers, which all use pre-trained machine learning and deep learning algorithms to automate image and video analysis.
![](upload://jES02jEb6lT8rc8Z1QyXI9MYGxt.png)
# How to use the service

First of all, you should create an Amazon Web Services (AWS) account that will let you have free access to all AWS services within the limits of the [Free Tier](https://aws.amazon.com/free/?sc_channel=em&sc_campaign=wlcm&sc_publisher=aws&sc_medium=em_wlcm_1d&sc_detail=wlcm_1d&sc_content=other&sc_country=global&sc_geo=global&sc_category=mult&ref_=pe_1679150_261538020&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all) for 12 months. You can create an account by using this [portal](https://portal.aws.amazon.com/billing/signup#/start/email). Be sure to make a root user account to get unrestricted access to all free demos and services. After filling in the sign-up form, you have to verify both your AWS account and also the Gmail you used for signing up. Feel free to use your Amherst College Gmail if you are working on a personal project or an assignment relevant to the courses you are taking. You can [sign in](https://signin.aws.amazon.com/signin?redirect_uri=https%3A%2F%2Fus-east-1.console.aws.amazon.com%2Fconsole%2Fhome%3FhashArgs%3D%2523%26isauthcode%3Dtrue%26nc2%3Dh_ct%26region%3Dus-east-1%26skipRegion%3Dtrue%26src%3Dheader-signin%26state%3DhashArgsFromTB_us-east-1_356a00db78c790ec&client_id=arn%3Aaws%3Asignin%3A%3A%3Aconsole%2Fcanvas&forceMobileApp=0&code_challenge=ghjJeppn9XNYT2CFdEWlkcM4DMgifdAXtJi8GzG46n0&code_challenge_method=SHA-256) after Amazon verifies and activates your AWS account. 
![1|669x500](upload://9ptvWgixAXCnryFLpgk52exWeMP.jpeg)

After signing in as a root user, you can search for different services and features in your AWS Management Console (as shown by the red arrow in the picture).

![2|690x328](upload://jsvYzrzslLmB9upf7oDg5aOSSeQ.jpeg)

Search for Amazon Rekognition, and the service will pop up as an option (highlighted in purple). 

![3|690x334](upload://ysYSqZ5grj2fCbTA5tIbtUMQ9hT.jpeg)

You can also click on the default Services menu (highlighted in green in the previous picture) to see a list of different options for other types of AWS services that may be applicable depending on the project of your choice. Once you use Amazon Rekognition, it will automatically show up in your dashboard under the “Recently visited services” section, so that you do not have to look it up again (highlighted in yellow in the previous picture). As you can see in the yellow drop-down on the left side of the screenshot, Rekognition offers a variety of tools that you can use for both image and video analysis. For our purposes, we will only use three different tools: Label Detection, Image Moderation, and Facial Analysis. Let’s start then!!

![4|690x332](upload://sdGv7vePOyQCiKhuUZMXspprMRM.jpeg)

**Note**: For all of the following tools, Amazon Rekognition Image does the detection through the DetectLabels API. This API automatically identifies thousands of objects, scenes, and concepts and returns a confidence score for each label. DetectLabels uses a default confidence threshold of **50**.

 ## **[Label Detection](https://docs.aws.amazon.com/rekognition/latest/dg/labels.html?pg=ln&sec=ft)**

**Description**: With Amazon Rekognition Label Detection, you can detect labels in images and videos. A label or a tag is an object, scene, action, or concept found in an image or video based on its contents. You can even detect activities such as "delivering a package" or "playing soccer." For example, a photo of people on a tropical beach may contain labels such as Palm Tree (object), Beach (scene), Running (action), and Outdoors (concept).

**Usage**: Using this tool, I uploaded an image of The Powerhouse. You can see the labels in the Results (pink highlight) section, including Leaf, Plant, Tree, etc. You can click on “show more” to look into tags that have a lower confidence score, meaning that the algorithm is not quite sure whether the object, scene, or concept actually appears and exists in the picture. You can either upload an image from the system you are using or simply drag and drop it. You can also copy the image address and put it into the “Use image URL” section to start the process.

![5|690x339](upload://pfxAHk3lBGZLduVvZczlgTspvmi.jpeg)

![6|690x353](upload://A6KHlrUFlzMpvHEhPvf7BPFGNTy.jpeg)


 In the following picture, I ran the tool on a picture of two mammoth fossils in the Beneski Museum of Natural History. Apparently, Amazon Rekognition does not even have a mammoth tag and labeled the skeleton as a zebra, which is clearly wrong. However, you can make a request to Rekognition to add and detect a new tag. In other words, you can train the model with your own images and tags!! In this way, you would also help the service to develop and become more competent in recognizing less-known and more complicated tags.

![7|690x343](upload://xkDHQ5R5iPlTJj8e2Nilpnsaq04.jpeg)

## **[Unsafe Visual Content Detection and Moderation](https://docs.aws.amazon.com/rekognition/latest/dg/moderation.html?pg=ln&sec=ft)**

**Description**: Amazon Rekognition can detect adult, explicit and violent content in images and in stored videos. Developers can use the returned metadata to filter inappropriate content based on their business needs. Beyond flagging an image based on the presence of unsafe content, the API also returns a hierarchical list of labels with confidence scores. These labels indicate specific categories of unsafe content, which enables granular filtering and management of large volumes of user-generated content (UGC). Examples include social and dating sites, photo-sharing platforms, blogs and forums, apps for children, e-commerce sites, entertainment, and online advertising services.

**Usage**: For this section, you have the three aforementioned options to upload the image of your interest. At first, the image you upload appears blurry and almost unrecognizable. You can see in the Results section (pink highlight) the reasoning behind why the content is considered to be violent or explicit. 

![8|690x332](upload://9VKCB2JWL0ASlcw4yprXaRw9Xa5.jpeg)

For example, in the second photo, where I uploaded a photo of World War II, it can be seen that due to the excessive amount of violence and destruction in the picture, the photo is blurry. However, if you do not feel disturbed seeing these types of images, you can click to view the actual content. This is the same filtering that Instagram Sensitive Content Control uses.

![9|690x332](upload://6RW1g5QswWEWqnQxbKpPWPZw6SV.jpeg)

## **[Face Detection and Analysis](https://docs.aws.amazon.com/rekognition/latest/dg/faces.html)**

**Description**: Facial attribute detection in images, including gender, age range, emotions (e.g. happy, calm, disgusted), whether the face has a beard or mustache, whether the face has eyeglasses or sunglasses, whether the eyes are open, whether the mouth is open, whether the person is smiling, and the location of several markers such as the pupils and jawline.

**Usage**: Using this tool, I uploaded a photo of Leonardo DiCaprio starring in the famous movie, “The Wolf of Wall Street”. It appears that he is clearly frustrated, and not smiling (a confidence score of 92.2%). The tool wrongly detects that Jordan has a beard with a high confidence score of 84.7%, although he clearly does not. 

![10|690x333](upload://waHeswcXfLhbbzDLCeKRQiwbcvt.jpeg)

In the second picture, I uploaded the famous meme starring DiCaprio again. (Yes, you guessed it, I am a fan.) Although his mouth is weirdly shaped in the meme, the tool somewhat detects that it is actually open (53.4% confidence score). As you can see the filter also detects age, gender, facial hair, and many other facial features.

![11|690x336](upload://sNLAR16eW10fZ0XnBXZCYwZTnOb.jpeg)



**Note**: For gender detection, be sure to carefully read the [guidelines on face attributes](https://docs.aws.amazon.com/rekognition/latest/dg/guidance-face-attributes.html). Amazon notes that a gender binary (male/female) prediction is based on the physical appearance of a face in a particular image. It does not indicate a person’s gender identity, and you should not use Amazon Rekognition to make such a determination. They do not recommend using gender binary predictions to make decisions that impact  an individual's rights, privacy, or access to services. So, before doing any project and analyzing any form of data, be sure to check the guidelines of all the tools described and carefully consider the ethical aspects of your project.

## Other Services:

[**Video Segment Detection**](https://docs.aws.amazon.com/rekognition/latest/dg/segments.html?pg=ln&sec=ft): Detect key segments in videos, such as black frames, start or end credits, slates, color bars, and shots. You can find where the opening and end credits are in a piece of content or break up videos into smaller clips for better indexing.

[**Custom Labels**](https://docs.aws.amazon.com/rekognition/latest/customlabels-dg/what-is.html?pg=ln&sec=ft): Detect custom objects such as brand logos using automated machine learning (AutoML) to train your models with as few as 10 images. With Amazon Rekognition Custom Labels, you can identify the objects and scenes in images that are specific to your business needs. For example, you can find your logo in social media posts, identify your products on store shelves, classify machine parts in an assembly line, distinguish healthy and infected plants, or detect animated characters in videos.

There are many, many other cool services that you can check and explore!
Depending on the number of your API requests, you may have to pay to use more advanced tools that provide more reliable, accurate insight regarding your data and training model. In this tutorial, only free demos were shown. All of these services usually have a low cost. With Amazon Rekognition, you pay for the images and videos that you analyze, and the face metadata that you store. There are no minimum fees or upfront commitments. You can get started for free, and save more as you grow with the Amazon Rekognition tiered pricing model. You can read more about pricing here: https://aws.amazon.com/rekognition/pricing/.

**Final Note**: Like many other Image Recognition technologies, Amazon Rekognition also has its own biases and deficiencies, but something is for sure: these models change dynamically every day and are trained on more diverse and representative data as time passes. Depending on your project, you might want to use another product. You can choose to use [Clarifai](https://www.clarifai.com/clarifai-free-account?utm_campaign=Branded%20Search%20Ads&utm_source=ppc&utm_term=clarifai&utm_campaign=Campaign+-+Visual+Search+-+SKAG&utm_source=adwords&utm_medium=ppc&hsa_acc=4305946045&hsa_cam=12661178807&hsa_grp=120788459192&hsa_ad=522162671711&hsa_src=g&hsa_tgt=kwd-310517979502&hsa_kw=clarifai&hsa_mt=e&hsa_net=adwords&hsa_ver=3&gclid=CjwKCAjwve2TBhByEiwAaktM1MeHuqQ_tmuVpwEIxtBnryevoR--YDX7KqBZUCGytEj0KbCb-3ryIxoCiisQAvD_BwE), [Google Cloud Vision API](https://cloud.google.com/vision?utm_source=google&utm_medium=cpc&utm_campaign=na-US-all-en-dr-bkws-all-all-trial-e-dr-1011347&utm_content=text-ad-none-any-DEV_c-CRE_507175471151-ADGP_Desk%20%7C%20BKWS%20-%20EXA%20%7C%20Txt%20~%20AI%20%26%20ML%20~%20Vision%20AI_General-KWID_43700066018829712-kwd-554619409396&utm_term=KW_google%20cloud%20platform%20vision%20api-ST_google%20cloud%20platform%20vision%20api&gclid=CjwKCAjwve2TBhByEiwAaktM1AwmiwN9txqILfRJbDZcF2t8h8nAT2gS3J5iarBi9yqGcg6h9tisgBoCRNwQAvD_BwE&gclsrc=aw.ds), [Microsoft Computer Vision API](https://azure.microsoft.com/en-us/services/cognitive-services/computer-vision/#features), or another new tool that has been recently launched. For a comprehensive review and comparison of all of these services, you might want to take a look at the following links to choose a service that is most suitable and applicable to your needs and aligns with your educational or career goals.

[Google Cloud Vision vs Amazon Rekoginition: Which is Better?](https://webuters.medium.com/google-cloud-vision-vs-amazon-rekoginition-which-is-better-c7cb4780d82a#:~:text=Google%20Cloud%20Vision%20vs%20Amazon%20Rekognition%3A%20Detection%20of%20Face%20%26%20Objects,accuracy%20than%20the%20other%20option)

[Google Vision vs. Amazon Rekognition: A Vendor-neutral Comparison](https://cloudacademy.com/blog/google-vision-vs-amazon-rekognition/)

[Comparing Image Tagging Services: Google Vision, Microsoft Cognitive Services, Amazon Rekognition and Clarifai](https://blog.filestack.com/thoughts-and-knowledge/comparing-google-vision-microsoft-cognitive-amazon-rekognition-clarifai/)

If you have any questions about the service or faced any issues implementing these tools, feel free to leave us a comment! You can also check out the [Amazon Rekognition FAQs page](https://aws.amazon.com/rekognition/faqs/).

References:

https://en.wikipedia.org/wiki/Amazon_Rekognition

https://docs.aws.amazon.com/rekognition/latest/dg/what-is.html

https://aws.amazon.com/rekognition/image-features/
