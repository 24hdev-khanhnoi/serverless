 # Report 

Repo: https://github.com/24hdev-khanhnoi/serverless
<br>

#### Finish:
- Setting up a Serverless app ( setup, deoloy helloworld,..)
- Create your AWS resources (DynamoDB Table,  S3 Bucket for File Uploads)
- Building a Serverless API (setup base, CRUD simple, deplpy,..)
- Users and authentication (Cognito user pool, Cognito identity pool,...)
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

```
POST - https://jcentwq22d.execute-api.us-east-1.amazonaws.com/prod/notes
  GET - https://jcentwq22d.execute-api.us-east-1.amazonaws.com/prod/notes/{id}
  GET - https://jcentwq22d.execute-api.us-east-1.amazonaws.com/prod/notes
  PUT - https://jcentwq22d.execute-api.us-east-1.amazonaws.com/prod/notes/{id}
  DELETE - https://jcentwq22d.execute-api.us-east-1.amazonaws.com/prod/notes/{id}
  GET - https://jcentwq22d.execute-api.us-east-1.amazonaws.com/prod/hello
```

#### Handling Auth in Serverless APIs

![alt text](images/serverless-auth-api-architecture.png)

#### Create a Cognito User Pool

##### Create User Pool
![alt text](images/43.png)
![alt text](images/44.png)
![alt text](images/45.png)
![alt text](images/46.png)
![alt text](images/47.png)
![alt text](images/48.png)
![alt text](images/49.png)

##### Create App Client

![alt text](images/50.png)
![alt text](images/51.png)
![alt text](images/52.png)


##### Create Domain Name
![alt text](images/53.png)

#### Create a Cognito Test User



##### Create User

![alt text](images/56.png)

![alt text](images/54.png)
![alt text](images/55.png)
![alt text](images/57.png)


Sử dụng AWS CLI để đăng ký người dùng bằng email và mật khẩu của họ.

```
aws cognito-idp sign-up \
  --region YOUR_COGNITO_REGION \
  --client-id YOUR_COGNITO_APP_CLIENT_ID \
  --username admin@example.com \
  --password Passw0rd!
```

```
aws cognito-idp sign-up \
  --region us-east-2 \
  --client-id 59j0tt0qci8dm9us7an226srsb \
  --username nqkhanh1998@gmail.com \
  --password Passw0rd!
```

Người dùng được tạo trong Cognito User Pool. Tuy nhiên, trước khi người dùng có thể xác thực với User Pool, tài khoản cần được xác minh. Hãy nhanh chóng xác minh người dùng bằng lệnh quản trị viên.


```
aws cognito-idp admin-confirm-sign-up \
  --region YOUR_COGNITO_REGION \
  --user-pool-id YOUR_COGNITO_USER_POOL_ID \
  --username admin@example.com
```

```
aws cognito-idp admin-confirm-sign-up \
  --region us-east-2 \
  --user-pool-id us-east-2_c7ZXkYHe7 \
  --username nqkhanh1998@gmail.com
```

#### Create a Cognito Identity Pool

##### Create Pool
![alt text](images/58.png)
![alt text](images/59.png)


- 23/7

![alt text](images/60.png)
![alt text](images/61.png)
![alt text](images/62.png)
![alt text](images/63.png)
![alt text](images/63.png)
![alt text](images/64.png)

```
YOUR_S3_UPLOADS_BUCKET_NAME  notes-app-uploads-kn
YOUR_API_GATEWAY_ID jcentwq22d
YOUR_API_GATEWAY_REGION us-east-2

````

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "mobileanalytics:PutEvents",
        "cognito-sync:*",
        "cognito-identity:*"
      ],
      "Resource": [
        "*"
      ]
    },
    {
      "Effect": "Allow",
      "Action": [
        "s3:*"
      ],
      "Resource": [
        "arn:aws:s3:::notes-app-upload-kn/private/${cognito-identity.amazonaws.com:sub}/*"
      ]
    },
    {
      "Effect": "Allow",
      "Action": [
        "execute-api:Invoke"
      ],
      "Resource": [
        "arn:aws:execute-api:us-east-1:*:jcentwq22d/*/*/*"
      ]
    }
  ]
}

```



#### Secure the APIs

##### Serverless IAM Auth


#### Test the APIs


![alt text](images/65.png)

##### Problem

Lỗi 403 
![alt text](images/66.png)


Có vẻ như mình đã config khi create identity pool
Fix bằng cách xoá identity pool cũ và lập cái mới
Thì sẽ có lỗi là role cũ đã tồn tại. 3 cách
1. đặt tên role mới ( VD thêm số 2 sau)
2. Vô config role lại
3. xoá role cũ đi

Mình đã xoá role cũ đi 

![alt text](images/69.png)
![alt text](images/67.png)
![alt text](images/68.png)
![alt text](images/70.png)


```
npx aws-api-gateway-cli-test \
--username='admin@example.com' \
--password='Passw0rd!' \
--user-pool-id='YOUR_COGNITO_USER_POOL_ID' \
--app-client-id='YOUR_COGNITO_APP_CLIENT_ID' \
--cognito-region='YOUR_COGNITO_REGION' \
--identity-pool-id='YOUR_IDENTITY_POOL_ID' \
--invoke-url='YOUR_API_GATEWAY_URL' \
--api-gateway-region='YOUR_API_GATEWAY_REGION' \
--path-template='/notes' \
--method='POST' \
--body='{"content":"hello world","attachment":"hello.jpg"}'


```
npx aws-api-gateway-cli-test \
--username='nqkhanh1998@gmail.com' \
--password='Passw0rd!' \
--user-pool-id='us-east-2_c7ZXkYHe7' \
--app-client-id='59j0tt0qci8dm9us7an226srsb' \
--cognito-region='us-east-2' \
--identity-pool-id='us-east-2:a2415eac-5c7c-45b4-bbc0-6e79ffcf897f' \
--invoke-url='https://jcentwq22d.execute-api.us-east-1.amazonaws.com/prod' \
--api-gateway-region='us-east-1' \
--path-template='/notes' \
--method='POST' \
--body='{"content":"hello world cli test","attachment":"helloCLITest.jpg"}'

```


```
npx aws-api-gateway-cli-test --username nqkhanh1998@gmail.com --password Passw0rd! --user-pool-id us-east-2_c7ZXkYHe7 --app-client-id 59j0tt0qci8dm9us7an226srsb --cognito-region us-east-2 --identity-pool-id us-east-2:a2415eac-5c7c-45b4-bbc0-6e79ffcf897f --invoke-url https://jcentwq22d.execute-api.us-east-1.amazonaws.com/prod --api-gateway-region us-east-1 --path-template /notes --method POST --body "{\"content\":\"hello world2\",\"attachment\":\"hello2.jpg\"}"

```







<hr>


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

23/7 

 Lỗi 403 
![alt text](images/66.png)


Có vẻ như mình đã config khi create identity pool
Fix bằng cách xoá identity pool cũ và lập cái mới
Thì sẽ có lỗi là role cũ đã tồn tại. 3 cách
1. đặt tên role mới ( VD thêm số 2 sau)
2. Vô config role lại
3. xoá role cũ đi

Mình đã xoá role cũ đi 

![alt text](images/69.png)
![alt text](images/67.png)
![alt text](images/68.png)
![alt text](images/70.png)

<hr>