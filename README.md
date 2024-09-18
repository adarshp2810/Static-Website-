# Static-Website-

This guide outlines the steps to deploy a static website using Amazon S3 for storage, CloudFront for content delivery, and a CI/CD pipeline for automated updates.
Step 1:
Begin by creating an S3 bucket. You can accept the default bucket configuration during this step

Step 2: Enable Static Website Hosting
Navigate to the properties of your newly created S3 bucket.
Locate the "Static Website Hosting" section and enable it.
Specify your main HTML file as the "Index document" (e.g., "index.html").
Save your changes.


 Step 3: Upload Website Files
Upload all your website's static files (HTML, CSS, JavaScript, images, etc.) to the S3 bucket.
Now if we check the link which we got after enabling static website it shows the error that the site can’t be reached.


 Step 4: Configure CloudFront Distribution
Search for CloudFront and create a new distribution.

 2.Select your S3 bucket as the origin domain.

 3. Set the "Origin Access" to "Legacy access identity."
 4. Create a new Origin Access Identity (OAI) and update your S3 bucket policy accordingly.

 5. Choose "Redirect HTTP to HTTPS" under "Viewer protocol policy."
 6. Select the appropriate HTTP method(s).


7. Set the "Default Root Object" to the name of your main HTML file (e.g., "index.html").
8. Create the distribution and wait for deployment to complete.
9. Once deployed, copy the "Distribution domain name" and access your website in a web browser.
 
Step 5: Automate Updates with CodePipeline
Search for CodePipeline and create a new pipeline (version 2).
Choose a descriptive name for your pipeline.


 Select "GitHub (version 2)" as the source provider and connect it to your GitHub repository containing your website code. 

 Make sure to upload your code on GitHub before connecting to GitHub

Choose the repository where you have the project and leave the remaining to default. Click on Next.
Skip the "Build Provider" step if you don't require any build process.
In the "Deploy Provider" step, choose Amazon S3 to ensure updates from your GitHub repository are automatically reflected in your S3 bucket.

Review the pipeline configuration and create the pipeline.


The index.html part shows the Creation of pipeline lets change the code in GitHub repository.


 The above image shows the changes made.

index.html is updated
Cache Invalidation and Viewing Updates
Changes might not be immediately visible due to CloudFront's caching. To view updates:
Open CloudFront and navigate to your distribution.
Select "Invalidations" and click "Create invalidation."
Enter a wildcard path (/*) and create the invalidation.
Refresh your website to see the updated content.

 
