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
