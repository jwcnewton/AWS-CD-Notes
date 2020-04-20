# Amazon CloudFront
Amazon CloudFront is a content delivery web service which integrates with other Amazon Web Services products to give you an easy way to distribute content to end users with low latency, high data transfer speeds, and no minimum usage commitments.

## How CloudFront works

When CloudFront get a request it will first compare the request with it's own configuration to decided how to serve this request, then it will forward the request to the applicable target service based on the file type. the target services will then send the requested files back to the CloudFront edge location. As soon as the edge location receives the first byte from the origin, it will start to forward those files to the user. These files will also be added to the cache in the edge location for future requests.

### Reporting

Out of the box CloudFront comes with reporting 

There are five key reports: 

* CloudFront Cache Statistics which displays information related to the edge locations for the last 60 days, with data points ranging from every hour to every day. 

* CloudFront Popular Objects, which lists the 50 most popular objects and statistics about these objects ranging from the number of requests, hits, and misses, and repeat downloads and requests by HTTPS status codes. 

* CloudFront Top Referrers Report, which lists the top 25 referrers including the number of requests from each referrer. 

* CloudFront Usage Reports provides information about the number of requests, data transferred by protocol, and by destination. 

* CloudFront Viewers Report provides information about the type of device users use to access your content, browser, operating system, and location.


## CloudFront and multiple buckets

How do I serve multiple buckets? You will need a separate CloudFront distribution for each bucket. However, you won't need to manage buckets in different locations. You would only need more than one bucket if you wish to set up separate domains, like images.example.com and download.example.com. A single distribution can have multiple CNAMEs, but they would be serving the same content.

Also see: [This post]("https://vimalpaliwal.com/blog/2018/10/10f435c29f/serving-multiple-s3-buckets-via-single-aws-cloudfront-distribution.html")