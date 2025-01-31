---
title: "Moving from an S3 Bucket to Amplify Hosting"
datePublished: Fri Jan 31 2025 12:20:26 GMT+0000 (Coordinated Universal Time)
cuid: cm6kqfmje000s09jt4caw5h8o
slug: moving-from-an-s3-bucket-to-amplify-hosting
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1738325908581/742596b1-0d76-4f9d-9ec1-5eab3026d748.png
tags: aws, s3, amplify-hosting

---

Leading up to AWS re:Invent 2024, AWS [announced](https://aws.amazon.com/blogs/aws/simplify-and-enhance-amazon-s3-static-website-hosting-with-aws-amplify/) the integration between Amplify and S3. With this feature, it’s never been easier to migrate your site from an S3 bucket to a content delivery network (CDN). The benefits of this migration include:

* Automatic deployment to the globally available AWS content delivery network (CDN) powered by CloudFront
    
* HTTPS support
    
* Easily connect your website to a custom domain using the Amplify console
    
* Bring your own Custom SSL certificates
    
* Monitor your website with built in access logs and CloudWatch metrics
    
* Set up password protection for your website
    
* Create redirect and rewrites rules in the Amplify console
    

If you already have you site hosted in an S3 bucket, the process only take a couple of clicks. First, inside of your S3 bucket, go to the Properties tab and scroll down to the Static website hosting. Click on the button Create Amplify App.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1737605253392/2f4bbebd-dc9f-4d52-aa79-3c2f4475b4a6.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1737605318067/5043169e-a986-4b82-9507-2503e0aa844f.png align="center")

From there, you will be redirected to Amplify to confirm your s3 bucket configuration. Click Save and deploy.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1737605393653/3ac20ee6-03cb-4016-bd7f-087a46a662d5.png align="center")

After a couple of minutes, you’ll be able to visit your hosted site through Amplify.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1737605482949/72dd7bed-2e96-4101-a4ba-8d2f8bff760f.png align="center")

And that’s it! If you have a custom domain, you can configure it in the custom domains pane in the navigation. Make sure to check the AWS Blog to stay updated on new features with Amplify.