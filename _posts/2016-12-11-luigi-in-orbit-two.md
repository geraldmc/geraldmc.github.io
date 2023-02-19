---
layout: post
title: Luigi In Orbit, part II
#published: false
#categories: ['luigi', 'data engineering']
#tags: ['luigi', 'data engineering']

---

You can run a prepared Docker image as previously shown, or roll your own, upload it to [Docker Hub](https://hub.docker.com/) and run as follows. 

{% highlight python %}

docker run geraldmc/docker-landsat 
    download LC80220392016073LGN00 
    -p
    --upload
    --key <AWS-ACCESS-KEY>
    --secret <AWS-SECRET-KEY>
    --bucket <BUCKET>
    --region s3.amazonaws.com
{% endhighlight %}

The above extends the previous command in part I in the several ways:

+ It runs a custom Docker image that .
+ It downloads a specific scene_ID, containing all 11 spectral bands. 
+ It processes bands 3-4-5 and creates a color-corrected image.
+ It uploads the resulting image to a bucket on Amazon S3. 

Up to now, it's assumed that Docker is run locally and that image data retrieved and processed is likewise. However, there are significant storage and performance costs when running things this way. Unless you plan to use Landsat only once or twice, running locally is not a good route. Rather one should use a cloud provider like Amazon. AWS EC2 and S3 services can provide a significantly faster network while offering tighter security. AWS is not free, but over time you’ll avoid wasted efforts. Plus, you'll have CPU enough on your local box to binge the latest series on Netflix all while processing your images in the cloud. 



