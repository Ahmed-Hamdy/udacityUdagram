# Hosting a Full-Stack Application

This project is Full-Stack Application that is hosted on AWS and you can follow the below steps inorder to run it locally and after making sure the project working well follow cloud deployment 
# Installation

## local building
    - install node package manager for both the frontend and the server using command 
        * npm install //for the server
        * yarn //for the frontend
    - create local postgres database and pass its enviroment variabels to the server 
    - start the server in production via command 
        * npm run rod
    - start the frontend web via 
        * yarn start
    - then you can access opne the frontend web page therough link : 
        * http://localhost:${port}/api/v0
    - you can regeister to the web site using Register button 

## Cloud deployment
    - download and istalol  AWS CLI and EB CLI
    - create AWS IAM account and acces
    - add AWS IAM (Access key ID) and (Secret access key) via command 
        * aws configure
#### Create Postgres DB
    - on AWS RDS service create Postgres dtabase with the following porperties 
        * port 5432
#### Create an Elastic Beanstalk environment
    - create elastic beanstalk repository with command
        * eb init udagram-api --platform node.js --region us-east-1
    - create an environment running a sample application with name udagarm-api-dev using command
        * eb create --sample udagarm-api-dev
    - make sure we are using it by running in rootDir of our server
        * eb use udagram-api-dev
    - add dtabase enviroment variabels to EB enviroment
#### S3 Bucket
    - on AWS S3 service ceate new buckt with following characteristics
        * public access
        * add the follwing policy to the bucket 
            {
                "Version": "2012-10-17",
                "Statement": [
                    {
                        "Sid": "PublicReadGetObject",
                        "Effect": "Allow",
                        "Principal": "*",
                        "Action": [
                            "s3:GetObject"
                        ],
                        "Resource": [
                            "arn:aws:s3:::${Bucket ARN}/*"
                        ]
                    }
                ]
            }
        * configure static website hosting

#### Pipeline 
    - create CircleCI configuration file in the root of the project and fill it with the pipeline process 
    - Create GitHub repository
    - upload the project files to the repository
    - login on circle ci sebsite using your github account
    - in projects dashboard setup a project
    - add aws enviroment variabels to circleci project
    - circleci will excute asll pipeline process that set in the CircleCI configuration file     

## Dependencies

```
- Node v14.15.1 (LTS) or more recent. While older versions can work it is advisable to keep node to latest LTS version

- npm 6.14.8 (LTS) or more recent, Yarn can work but was not tested for this project

- AWS CLI v2, v1 can work but was not tested for this project

- A RDS database running Postgres.

- A S3 bucket for hosting uploaded pictures.

```

## Testing

This project contains two different test suite: unit tests and End-To-End tests(e2e). Follow these steps to run the tests.

1. `cd udagram/udagram-frontend`
1. `npm run test`
1. `npm run e2e`

# To acees the front-end web page use the following link:

    http://udagram-frontend-udacity.s3-website-us-east-1.amazonaws.com/home

## Built With

- [Angular](https://angular.io/) - Single Page Application Framework
- [Node](https://nodejs.org) - Javascript Runtime
- [Express](https://expressjs.com/) - Javascript API Framework

## License

[License](LICENSE.txt)
