# Alexapolyskill

Serverless web application built using python and Amazon AWS services S3 | API GateWay | Lambda | DynamoDB | SNS | Poly  and  Amazon Alexa Skill

</br>

## Goal:

The goal is to build application using serverless architecture which converts text to audio mp3 files using Amazon Poly service and finally to publish Alexa skill which uses the generated audio files by Poly. 

</br>

## Architecture:


### Serverless Website

![alt text](https://github.com/RepakaRamateja/Alexapolyskill/blob/master/images/Architecure.png)


Amazon s3 contains all the html files and converted audio files

Api gateway invokes lambda functions basing on user request type 

for instance 

    get  request invokes get post lambda function
    post request invokes New Post lambda function etc.


Each lambda function has a unique responsibility.

get post lambda function retrives all the posts from dynamo db and audio files from s3

New post lambda function inserts posts into dynamo db and inserts a message into SNS topic which inturn triggers another lambda function
(Convert to Audio) which uses text from dynamo db and converts it into mp3 and store it in s3 service.

Amazon poly is aws service which converts text to Audio.

Amazon SNS(simple notification service) is asynchronous service which invokes convert to audio lambda function when message is arrived.

Amazon Dynamodb is amazon nosql db service which is used for storing  and retriving of the posts.


### Alexa skill

![alt text](https://github.com/RepakaRamateja/Alexapolyskill/blob/master/images/skillarch.png)


</br>

### Technology stack

![alt text](https://github.com/RepakaRamateja/Alexapolyskill/blob/master/images/stack.png)


## Features:

![alt text](https://github.com/RepakaRamateja/Alexapolyskill/blob/master/images/overview.png)

  First user need to enter input text and then select voice from the list.

  Then click on button Say it

  Now in the background processing happens and then mp3 files are generated.

  To retrive the files type * in the text box and then click on search button.

  It retrives all the mp3 files that are converted and stored in S3 bucket. (Refer below screen shot)

</br>

![alt text](https://github.com/RepakaRamateja/Alexapolyskill/blob/master/images/files.png)

</br>

  Now user can download all the files.


###  Alexa Skill   

  amazon.alexa.com 

  while loggind into the alexa website use the same email address for alexa developer services

  developer.amazon.com

  click on alexa skill kit

  then create skill

  fill the details like skill name and details

  now chooose a model to add your skill

  select custom skill and then create skill

  now it will create skill interface now we need to fill four details

  Invocation Name : simply name to invoke your skill

  Intents Samples and Slots

  Build Model

  Endpoint


add intent GetNewFactIntent

then configure sample utterances

tell me a fact

give me a fact

help me study

tell me something

save model

build model

takes some time

Now in case of endpoint supply alexa portal with aws resource name

now go back to aws console and create new lambda function

blue print and type alexa

then select alexa-skill-kit-sdk-factskill

enter name and role choose an existing role

and create a function

go to designer and then add triggers

alexa skills kit

after saving create new file index.js

alexa lab src contains that file index.js

now go s3 bucket where your audio files are stored and then 

select the links and paste them in the code 

save the file 

save the lambda function

copy the arn and go to alexa developer window and paste the arn 

save the end points and save 

now go to test the skill and test it 

you can also test it in real life i.e by using amazon alexa



  Last but not least build  amazon alexa skill which uses the audio files present in s3 bucket. 

  

  




