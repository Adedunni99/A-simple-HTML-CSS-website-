# A-simple-HTML-CSS-website-
Created  a simple HTML/CSS website and deploy it to Google Cloud

Part 1 – Build a Simple Website

Create a folder on your computer,  GCP.


Inside it create two files: index.html, style.css

    index.html

    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>My First GCP Site</title>
    <link rel="stylesheet" href="style.css">
    </head>
    <body>
    <h1>Hello from Google Cloud!</h1>
    <p>This is my simple HTML/CSS website.</p>
    </body>
    </html>



    style.css
    
    body {
    font-family: Arial, sans-serif;
    background-color: #f0f8ff;
    text-align: center;
    padding-top: 50px;
    }
    h1 {
      color: #2c3e50;
    }

You can preview it locally by double-clicking index.html.

 Part 2 – Set Up Google Cloud
 
Create a Google Cloud account (https://console.cloud.google.com/)

Install the gcloud CLI (https://cloud.google.com/sdk/docs/install)

Log in and select a project: 

    gcloud auth login

    gcloud config set project cool-coral-473110-d0


 Part 3 – Create a Storage Bucket
 
Buckets must have a unique name. My-gcp-html-site-dunni.

Create it and allow public read:

    gsutil mb -l us-central1 gs://my-gcp-html-site-123/

    gsutil iam ch allUsers:objectViewer gs://my-gcp-html-site-123

 Part 4 – Upload Your Website Files
 
From the folder where index.html and style.css live:

    gsutil cp * gs://my-gcp-html-site-123


 Part 5 – Set the Bucket as a Website
 
Tell GCS to use index.html as the main page:

    gsutil web set -m index.html gs://my-gcp-html-site-123


 Part 6 – View the Live Site
 
The site is now publicly reachable at:

    http://storage.googleapis.com/my-gcp-html-site-123/index.html

 <img width="1854" height="802" alt="Screenshot from 2025-09-25 18-22-38" src="https://github.com/user-attachments/assets/f93ea169-c94a-4116-b028-b7462254040f" />


Quick Recap

Build: Create index.html + style.css.

Deploy:

    gcloud auth login

    gsutil mb -l us-central1 gs://my-gcp-html-site-123/

    gsutil iam ch allUsers:objectViewer gs://my-gcp-html-site-123

    gsutil cp * gs://my-gcp-html-site-123/
    gsutil web set -m index.html gs://my-gcp-html-site-123



