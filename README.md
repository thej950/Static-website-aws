# aws-static-website

#S3-Static website Hosting 
 1. creating S3 bucket (thej-website) make sure Enable public access

 2. upload required source code or files 
	Amazon S3>Buckets>thej-website>Upload
		image.jfif
		index.html
		README.md
		404.html

 3. Enabe static website hosting 
	Amazon S3>Buckets>thej-website>Edit static website hosting
		Edit static website hosting
			Static website hosting (select Enable)
			Hosting type (select Host a static website)
			Index document (index.html)
			Error document - optional (404.html)

			- click on save changes 

 4. Write Policy to Enable to access website from browser 
	Amazon S3>Buckets>thej-website
		thej-website 
			Permissions
				- Bucket policy
				- Note : Make sure give /* after ARN 
    ```
	{
	  "Id": "Policy1726213161993",
	  "Version": "2012-10-17",
	  "Statement": [
	    {
	      "Sid": "Stmt1726213155392",
	      "Action": [
	        "s3:GetObject"
	      ],
	      "Effect": "Allow",
	      "Resource": "arn:aws:s3:::mybucket-950/*",
	      "Principal": "*"
	    }
	  ]
	}
   ```
 5. Now take url from static website hosting under properties 
	Bucket website endpoint
		url : http://thej-website.s3-website-us-east-1.amazonaws.com