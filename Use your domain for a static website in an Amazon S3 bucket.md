# Use your domain for a static website in an Amazon S3 bucket

> This getting started tutorial shows you how to perform the following tasks:

<ul>
    <li>
      Register a domain name, such as example.com
  </li>
  <li>
    Create an Amazon S3 bucket and configure it to host a website
  </li>
    <li>
    Create a sample website and save the file in your S3 bucket
  </li>
    <li>
    Configure Amazon Route 53 to route traffic to your new website
  </li>
</ul>

> When you're finished, you'll be able to open a browser, enter the name of your domain, and view your website

Topics 

- [Prerequisites](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started-s3.html#getting-started-prerequisites)
- [Step 1: Register a domain](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started-s3.html#getting-started-find-domain-name)
- [Step 2: Create an S3 bucket for your root domain](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started-s3.html#getting-started-create-s3-website-bucket)
- [Step 3 (optional): Create another S3 Bucket, for your subdomain](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started-s3.html#getting-started-create-s3-www-bucket)
- [Step 4: Set up your root domain bucket for website hosting](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started-s3.html#getting-started-configure-root-for-website)
- [Step 5 : (optional): Set up your subdomain bucket for website redirect](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started-s3.html#getting-started-subdomain-bucket-redirect)
- [Step 6: Upload index to create website content](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started-s3.html#getting-started-upload-content)
- [Step 7: Edit S3 Block Public Access settings](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started-s3.html#getting-started-block-access)
- [Step 8: Attach a bucket policy](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started-s3.html#getting-started-attach-policy)
- [Step 9: Test your domain endpoint](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started-s3.html#getting-started-test-domain-endpoint)
- [Step 10: Route DNS traffic for your domain to your website bucket](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started-s3.html#getting-started-create-alias)
---
I know this is too late for the original question but there may be more people with the same issues (me last week).

I was having the same issue while trying to create a route in route53 with CloudFormation. I was trying to redirect my domain www.example.com to example-bucket.s3-website-eu-west-1.amazonaws.com.

It turns out you cannot redirect to an arbitrary bucket. The bucket name must be the same as the domain you're trying to alias. So if you want to redirect www.example.com, your bucket name must be www.example.com and the URL must be www.example.com.s3-website-eu-west-1.amazonaws.com.

Moreover cloudformation has a weird syntax. Cloudformation doesn't need the name of the bucket (it already knows it). It only needs the endpoint.

So instead of using something like
```
"AliasTarget": {
               "DNSName" : "example-bucket.s3-website-eu-west-1.amazonaws.com",
               "HostedZoneId" : "<zoneID>"
             },
```
you need
```
"AliasTarget": {
               "DNSName" : "s3-website-eu-west-1.amazonaws.com",
               "HostedZoneId" : "<zoneID>"
             },
```
And route53 where to redirect because the name of the route must be the same as the name of the bucket.

---
- [Step 11: Test your website](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started-s3.html#getting-started-test)
- [Step 12 (optional): Use Amazon CloudFront to speed up distribution of your content](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started-s3.html#getting-started-cloudfront)
