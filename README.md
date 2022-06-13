# Hosting a Full-Stack Application

### **You can use you own project completed in previous courses or use the provided Udagram app for completing this final project.**

---

In this project you will learn how to take a newly developed Full-Stack application built for a retailer and deploy it to a cloud service provider so that it is available to customers. You will use the aws console to start and configure the services the application needs such as a database to store product information and a web server allowing the site to be discovered by potential customers. You will modify your package.json scripts and replace hard coded secrets with environment variables in your code.

After the initial setup, you will learn to interact with the services you started on aws and will deploy manually the application a first time to it. As you get more familiar with the services and interact with them through a CLI, you will gradually understand all the moving parts.

You will then register for a free account on CircleCi and connect your Github account to it. Based on the manual steps used to deploy the app, you will write a config.yml file that will make the process reproducible in CircleCi. You will set up the process to be executed automatically based when code is pushed on the main Github branch.

The project will also include writing documentation and runbooks covering the operations of the deployment process. Those runbooks will serve as a way to communicate with future developers and anybody involved in diagnosing outages of the Full-Stack application.

# local building
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

# Cloud deployment
    - download and istalol  AWS CLI and EB CLI
    - create AWS IAM account and acces
    - add AWS IAM (Access key ID) and (Secret access key) via command 
        * aws configure
### Create Postgres DB
    - on AWS RDS service create Postgres dtabase with the following porperties 
        * port 5432
### Create an Elastic Beanstalk environment
    - create elastic beanstalk repository with command
        * eb init udagram-api --platform node.js --region us-east-1
    - create an environment running a sample application with name udagarm-api-dev using command
        * eb create --sample udagarm-api-dev
    - make sure we are using it by running in rootDir of our server
        * eb use udagram-api-dev
    - add dtabase enviroment variabels to EB enviroment
### S3 Bucket
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
        
### Pipeline 
    - create CircleCI configuration file in the root of the project and fill it with the pipeline process 
    - Create GitHub repository
    - upload the project files to the repository
    - login on circle ci sebsite using your github account
    - in projects dashboard setup a project
    - add aws enviroment variabels to circleci project
    - circleci will excute asll pipeline process that set in the CircleCI configuration file     

# Udagram

This application is provided to you as an alternative starter project if you do not wish to host your own code done in the previous courses of this nanodegree. The udagram application is a fairly simple application that includes all the major components of a Full-Stack web application.
###### To acees the front-end web page use the following link:

    http://udagram-frontend-udacity.s3-website-us-east-1.amazonaws.com/home

### Dependencies

```
- Node v14.15.1 (LTS) or more recent. While older versions can work it is advisable to keep node to latest LTS version

- npm 6.14.8 (LTS) or more recent, Yarn can work but was not tested for this project

- AWS CLI v2, v1 can work but was not tested for this project

- A RDS database running Postgres.

- A S3 bucket for hosting uploaded pictures.

```

### Installation

Provision the necessary AWS services needed for running the application:

1. In AWS, provision a publicly available RDS database running Postgres. 
1. In AWS, provision a s3 bucket for hosting the uploaded files. 
1. Export the ENV variables needed or use a package like [dotnev](https://www.npmjs.com/package/dotenv)/.
1. From the root of the repo, navigate udagram-api folder `cd starter/udagram-api` to install the node_modules `npm install`. After installation is done start the api in dev mode with `npm run dev`.
1. Without closing the terminal in step 1, navigate to the udagram-frontend `cd starter/udagram-frontend` to intall the node_modules `npm install`. After installation is done start the api in dev mode with `npm run start`.

## Testing

This project contains two different test suite: unit tests and End-To-End tests(e2e). Follow these steps to run the tests.

1. `cd udagram/udagram-frontend`
1. `npm run test`
1. `npm run e2e`

There are no Unit test on the back-end

### Unit Tests:

Unit tests are using the Jasmine Framework.

### End to End Tests:

The e2e tests are using Protractor and Jasmine.

## Built With

- [Angular](https://angular.io/) - Single Page Application Framework
- [Node](https://nodejs.org) - Javascript Runtime
- [Express](https://expressjs.com/) - Javascript API Framework

## License

[License](LICENSE.txt)
