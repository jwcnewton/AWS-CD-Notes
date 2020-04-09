Creating an aws cli profile:

`vi ~/.aws/config`

```conf
[default]
region = EU


[profile qacli]
region=us-west-2
output=json
aws_access_key_id=XXXXX
aws_secret_access_key=XXXXX
```

See [create static website](./stdout/create-static-website.md)