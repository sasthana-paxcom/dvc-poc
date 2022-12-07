## Installing DVC

pip install dvc
pip install dvc[s3]

## Start DVC inside your git repo
dvc init  
### .dvc/.gitignore and .dvc/config is created

## start tracking a file or directory
dvc add < DATA>

### A . dvc file (example: data.dvc) will be created.[Size in KBs]. 
### This is a tracker file for the *hashed* data, to be send to remote storage.

### Now that your data is dvc, add the < DATA > to .gitignore. (DO NOT ADD .dvc OR *.dvc in .gitignore)

## We are ready to send the large file to remote. Lets set a remote now.

## For AWS S3 as the remote.

dvc remote add -d myremote  s3://<BUCKET & KEY/LOCATION>

### **-d** stands for default. The information about the storage will be saved under .dvc/config

## Assuming this is a private bucket, an AWS access key pair needs to be created with R-W access to this S3
## Export those keys

### For Git-bash / cygwin
AWS_ACCESS_KEY_ID=<aws_s3_access_key>
AWS_SECRET_ACCESS_KEY=<aws_s3_secret_access_key>

### For powershell
$env:AWS_ACCESS_KEY_ID=<aws_s3_access_key>
$env:AWS_SECRET_ACCESS_KEY=<aws_s3_secret_access_key>


## git Commiting everyting with set-up
git add .
git commit -m "Configure DVC and remote storage"

## Now lets push our DVC object
dvc push

##You can check the AWS S3, it's now populated with the Hashes of our data

## Other DVC Commands
dvc diff
dvc checkout
dvc pull [some .dvc file]
dvc get


## Transfer directly to remote without local caching
[https://dvc.org/doc/command-reference/import-url#example-transfer-to-remote-storage]  
dvc import-url https://data.dvc.org/get-started/data.xml data.xml --to-remote

### above will create only a data.xml.dvc file locally, if we want data locally as well, just remove --to-remote flag



