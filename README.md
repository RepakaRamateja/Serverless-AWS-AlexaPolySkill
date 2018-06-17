# Alexapolyskill

 Amazon Alexa Skill and Serverless web application built using PYTHON | HTML 5 |  CSS 3| JAVASCRIPT and Amazon AWS services  S3 | API GateWay | Lambda | DynamoDB | SNS | Poly 

</br>

## Goal:

The goal is to build application using serverless architecture which converts text to audio mp3 files using Amazon Poly service and finally to publish Alexa skill which uses the generated audio files by Poly. 

</br>

## Architecture:

</br>

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

</br>

### Alexa skill

</br>

![alt text](https://github.com/RepakaRamateja/Alexapolyskill/blob/master/images/skillarch.png)


</br>

### Technology stack

</br>

![alt text](https://github.com/RepakaRamateja/Alexapolyskill/blob/master/images/stack.png)

</br>

<table>
<thead>
<tr>
<th>Area</th>
<th>Technology</th>
</tr>
</thead>
<tbody>
	<tr>
		<td>Front-End</td>
		<td>HTML5, CSS3, JAVASCRIPT</td>
	</tr>
	<tr>
		<td>Back-End</td>
		<td>Python</td>
	</tr>
	<tr>
		<td>Database</td>
		<td>Dynamo DB(Aws Cloud Service)</td>
	</tr>
  <tr>
		<td>Images Storage</td>
		<td>Amazon AWS-S3</td>
	</tr>
    <tr>
		<td>Other Aws Services</td>
		<td>API GateWay | Lambda | DynamoDB | SNS | Poly | Amazon Alexa Skill Set</td>
	</tr>
</tbody>
</table>

</br>



## Features:

### Serverless website

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


Last but not least build  amazon alexa skill which uses the audio files present in s3 bucket. 


### Steps to create Alexa Skill 

• login to alexa website

     while logging into the alexa website ( amazon.alexa.com ) use the same email address as for alexa developer services

• click on alexa skill kit

     then create skill

• fill the necessary details like skill name and details

•  Now chooose a model to add your skill

•  Select custom skill and then create skill

    Now it will create skill interface now we need to fill four details which are  stated below

    Invocation Name : simply name to invoke your skill

    Intents Samples and Slots

    Build Model

    Endpoint

•  Now Add intent GetNewFactIntent  

•  then configure sample utterances like 

    tell me a fact

	give me a fact

    help me study

    tell me something


• save model

• build model  

  (* takes some time)

• Now in case of endpoint supply alexa portal with aws resource name

• go back to aws console and create new lambda function

    blue print and type alexa

    then select alexa-skill-kit-sdk-factskill

    enter name and role choose an existing role

    and create a function

• go to designer and then add triggers

    alexa skills kit

    after saving create new file index.js

    alexa lab src contains that file index.js

• Now go s3 bucket where your audio files are stored and then 

• Select the links and paste them in the code 

• Save the file 

• Save the lambda function

• Copy the arn and go to alexa developer window and paste the arn 

• Save the end points and click save 

• Now go to test the skill and test it 

you can also test it in real life i.e by using amazon alexa echo or echo dot 

So through echo dot or alexa echo based on your invocation name and utterances it will start replying with audio mp3 files that's it.
  






  

  