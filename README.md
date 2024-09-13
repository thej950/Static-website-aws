## S3 Static Website Hosting

### 1. Creating an S3 Bucket (`thej-website`)

- Go to the **Amazon S3** console.
- Click **Create bucket**.
- Name your bucket `thej-website`.
- **Enable public access** settings to ensure your bucket is publicly accessible.

### 2. Upload Required Source Files

- Navigate to **Amazon S3 > Buckets > thej-website > Upload**.
- Upload the following files:
  - `image.jfif`
  - `index.html`
  - `README.md`
  - `404.html`

### 3. Enable Static Website Hosting

- Go to **Amazon S3 > Buckets > thej-website > Edit static website hosting**.
  - Select **Enable** for Static website hosting.
  - Choose **Host a static website** for Hosting type.
  - Set **Index document** to `index.html`.
  - Set **Error document** (optional) to `404.html`.
- Click **Save changes**.

### 4. Write Policy to Enable Website Access from the Browser

- Go to **Amazon S3 > Buckets > thej-website > Permissions > Bucket policy**.
- Make sure to include `/*` after the ARN.
  
```json
{
  "Id": "Policy1726213161993",
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt1726213155392",
      "Effect": "Allow",
      "Principal": "*",
      "Action": [
        "s3:GetObject"
      ],
      "Resource": "arn:aws:s3:::thej-website/*"
    }
  ]
}
```

### 5. Retrieve the Website URL

- Go to **Static website hosting** under the **Properties** tab of your S3 bucket.
- Note the **Bucket website endpoint** URL:

  ```
  URL: http://thej-website.s3-website-us-east-1.amazonaws.com
  ```