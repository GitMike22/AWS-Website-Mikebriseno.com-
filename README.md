# AWS-Website-Mikebriseno.com-
My website hosted on AWS - steps on how I did it and copy of files for it.

Cloud resume challenge, have you heard of it?

It is a challenge created by Forrest Brazeal back in 2020, it is a fun project where you create an online resume for yourself using HTML, CSS, and Javascript then host it on AWS using various AWS services. 

I used a template from html5 website. I used VS Code to change the HTML and CSS a bit to meet my requirements of how I wanted it to look. 

I followed a couple videos for the main static website.
1. Created S3 bucket
2. Cloudfront Ditribution
3. Route 53
4. Bought Domain with Namecheap.com
5. Created SSL certificate for domain

The hardest part out of this whole project was probably coming up with a name for my website. I did end up using namecheap.com for my domain name, as the name suggests their domains be cheap. I landed on a simple mikebriseno.com. 

This was the first part, once this was done I was able to have an up and running website!

But everytime I wanted to update my website or edit something I would need to upload the new file with the edits directly to AWS S3 bucket and delete the old one...surely there is a faster way?

* * * TECHNOLOGY INCOMING ! * * *

So there is! It is called creating a CI/CD pipeline, or Continuous intergration / continuous Deployment pipeline. I used Github Actions, however there are other flavors of this out there. ( Jenkins, Gitlab CI/CD, AWS Codecommit etc.)

Using various videos out there I figured out Github actions to create a CI/CD pipeline, allowing me to update my website files on VS CODE > GITHUB > S3 Bucket > Internet(WWW).
I used Jake Jarvis S3 Sync action repo for this! Very easy to use if you dont screw up easy things like I did.
Troubles I had that I figured out
*of note the repo states push to "Master" branch, the default on github is now called Main, so if you are using main, dont forget to change that or else it wont work!
*I also didnt have my .github/workflows folder and main.yaml file in the same folder as the rest of my website files so it wasn't working properly
https://github.com/jakejarvis/s3-sync-action

“Creating invalidations” in cloudfront for the distribution as it had the previous version cached, had to create invalidation to remove cache using a wildcard (/* all files)
Had to create a github action for this

In the end, I'm not done with this project! There's so much more you can add to it and I'm excited to continue working on it as it's fun to build upon it! I'll write a part 2 on what I end up adding to it!
