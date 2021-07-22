 # Report 

Repo: https://github.com/24hdev-khanhnoi/serverless
<br>

#### Finish:
- Setting up a Serverless app ( setup, deoloy helloworld,..)
- Create your AWS resources (DynamoDB Table,  S3 Bucket for File Uploads)
- Building a Serverless API (setup base, CRUD simple, deplpy,..)
<br>

#### Problem:
- You have attempted to create more buckets than allowed
For information about how to increase your bucket limit (Fix Done)
- Eslint ( Fix Done)
<br>

##### images


 
 # Serverless Node.js Leaning 

 # Report

- 21/7
 #### Tìm hiểu serverless, AWS Lambda, IAM, ..
 #### IAM
 ![alt text](images/1.png)
  ![alt text](images/2.png)
  
 #### Configure the AWS CLI , Install the AWS CLI
 ```
 brew install awscli
 aws configure
 ```
 ![alt text](images/3.png)
  ![alt text](images/4.png)


 #### Setting up a Serverless app

 ```
 npm install -g serverless
 serverless install --url https://github.com/AnomalyInnovations/serverless-nodejs-starter --name notes-api
 ```

![alt text](images/5.png)
![alt text](images/6.png)

##### handler.js: Là nơi mà chúng ta sẽ định nghĩa các hàm lambda (Lambda Function).

#####  serverless.yml: Là nơi chúng ta sẽ khai báo cấu hình cho ứng dụng, file này thông thường có 3 phần chính sau:
Provider: Sử dụng để công khai các cấu hình cụ thể cho nhà cung cấp dịch vụ Cloud, ví dụ như cấu hình tên nhà cung cấp, môi trường runtime, khu vực sử dụng…vv

Functions: Chúng ta sẽ chỉ định các Function logic chức năng tại đây.

Resources: Phần này sẽ khai báo các tài nguyên để cho các Functions của bạn sử dụng được. Tài nguyên sẽ được khai báo bởi một dịch vụ của AWS có tên là CloudFormation.

```
npm install aws-sdk --save-dev
npm install uuid@7.0.3 --save
```
   ![alt text](images/7.png)
      ![alt text](images/8.png)

##### aws-sdk allows us to talk to the various AWS services.
##### auuid generates unique ids. We need this for storing things to DynamoDB..
#### Add support for ES6 and TypeScript
```
npm install --save-dev serverless-bundle
```


![alt text](images/9.png)
![alt text](images/10.png)

#### Deploy your Hello World API

```
serverless deploy
```

![alt text](images/11-.png)
![alt text](images/12.png)
![alt text](images/13.png)
![alt text](images/serverless-hello-world-api-architecture.png)


#### Initialize the Backend Repo 

Repo: https://github.com/24hdev-khanhnoi/serverless 


#### Create a DynamoDB Table
![alt text](images/14.png)
![alt text](images/15.png)
![alt text](images/16.png)

#### Create a DynamoDB Table
![alt text](images/17.png)
![alt text](images/18.png)
###### Nếu có Lỗi
![alt text](images/19.png)

- 22/7
 Fix bằng cách xoá 1 vài bucket không quan trọng
 ![alt text](images/20.png)

Sau khi thêm: 
 ![alt text](images/21.png)
  ![alt text](images/22.png)

#### Building a Serverless API
![alt text](images/serverless-public-api-architecture.png)

##### Add a Create Note API
``` create.js ``` ( test )

   ![alt text](images/23.png)
``` serverless.yml ```

   ![alt text](images/24.png)
``` mocks/create-event.json ```

   ![alt text](images/25.png)

``` 
$ serverless invoke local --function create --path mocks/create-event.json
```
   ![alt text](images/26.png)

##### Refactor Our Code

```
/create.js
/libs/dynamodb-lib.js
libs/handler-lib.js
```

![alt text](images/26_1.png)
![alt text](images/26_2.png)
![alt text](images/26_3.png)

##### Problem
Nếu có lỗi:
 
   ![alt text](images/27.png)

Fix bằng cách formatcode ở các file đó

#### CRUD config serverless.yml
![alt text](images/29_00.png)
#### Add a Get Note API
![alt text](images/29_0.png)
![alt text](images/29.png)
![alt text](images/30.png)

#### Add a list all the notes API
![alt text](images/31.png)
![alt text](images/32.png)
![alt text](images/33.png)

#### Add an update note API
![alt text](images/34.png)
![alt text](images/35.png)
![alt text](images/36.png)
![alt text](images/37.png)
![alt text](images/38.png)
![alt text](images/39.png)

#### Deploy the APIs

![alt text](images/40.png)
![alt text](images/41.png)
![alt text](images/42.png)
# Problem
- 21/7 
You have attempted to create more buckets than allowed
For information about how to increase your bucket limit
![alt text](images/19.png)
Fix bằng cách xoá 1 vài bucket không quan trọng
 ![alt text](images/20.png)

- 22/7
   ![alt text](images/27.png)

Fix bằng cách formatcode ở các file đó



<hr>








