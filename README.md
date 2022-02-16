# Deploy Data Pipeline in AWS using Serverless Framework
1. Preparation (on MacOS as example)
2. Serverless Framework Code
3. Deploy change into AWS

# Preparation (on MacOS as example)
## S3
```powershell
Build a S3 bucket for deploy if needed 
```

## Python

```powershell
# 1. Install or update python to version 3.8
# 2. cd to the directory where requirements.txt is located
# 3. Optional: activate your virtualenv
# 4. Run the following command to install required python packages
% pip3 install -r requirements.txt
```

## Serverless Initialization 

```powershell
# 1. Install or update Serverless to latest
% curl -o- -L https://slss.io/install | bash
% serverless upgrade

# 2. Install Node
% brew update
% brew install node

# 3. Test Node
% node -v

# 4. Test npm
% npm -v

# 6 Check serverless framework version
% serverless -v
```
 ## Serverless Project Initialization
```powershell
# Create a new Serverless Service/Project
% serverless create --template aws-python3 --path {project_folder}
```

# Serverless Framework Code
### Open your project in VScode
```powershell
% open -a “Visual Studio Code” {project_folder}
```
### Modify .python file
```powershell
# Rename python file
% mv handler.py data_pipeline.py

# Copy the code into your python file from data_pipeline.py and save it

# Install boto3 if you do not have it
sudo apt install python3-pip -y
sudo pip3 install boto3

# Create requirements.txt for external packages
touch requirements.txt
echo “<library>” >> requirements.txt

# Install needed librarires
sudo pip3 install -r requirements.txt
```
### Serverless Plugin Installation
```powershell
# Instal Serverless Prune Plugin 
% sudo sls plugin install -n serverless-prune-plugin

# Install serverless python requirements (https://github.com/UnitedIncome/serverless-python-requirements)s
% sudo sls plugin install -n serverless-python-requirements

# Install serverless dotenv plugin
% sudo npm i -D serverless-dotenv-plugin
```

### Create .env file and put environment variables if need
```env
APPLICATION=my-data-pipeline
STAGE=dev
REGION=ap-southeast-2
# This will be automatically added into lambda runtime, if you enter it in serverless.yml:custom.dotenv.include 
TZ_LOCAL=Australia/Sydney
```

### Modify serverless.yml file
```bash
# Copy the code into your yml file and save it
```

# Deploy change into AWS
```powershell
% sls deploy
```