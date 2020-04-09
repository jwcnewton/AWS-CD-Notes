```bash
#Create Bucket
aws s3 mb s3://qa-aws-jn --profile qacli
make_bucket: qa-aws-jn

#Upload index html
aws s3 cp index.html s3://qa-aws-jn --profile qacli                                                     

Copy all files
aws s3 cp . s3://qa-aws-jn --profile qacli --recursive

#Create as website
aws s3 website s3://qa-aws-jn --profile qacli --index-document index.html --error-document error/index.html

#Make website files and assets public
aws s3 cp . s3://qa-aws-jn --profile qacli --recursive --acl public-read                                   
```